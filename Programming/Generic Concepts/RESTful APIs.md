# What is REST?

In API architecture REST stands for **RE**presentational **S**tate **T**ransfer, it is a not a specific product or technology but rather a specification or model to follow when designing your APIs.

While different technologies exist when making requests to servers such as HTTP, HTTPS and FTP, REST is not a type of request but rather an architectural style that exposes data from a server in a way that has been laid out in the REST design.

This way when working with RESTful APIs you can expect a cohesive experience in relation to other RESTful APIs that you have worked with in the past speeding up development because it isn't necessary to learn the rules of a new API every time.
# What Makes an API a REST API?
## 1. Use HTTP Request Verbs

What are some of these HTTP Request Verbs?

![](Pictures/RESTful%20APIs%20-%20Request%20Verbs.png)

We've already worked with some of these in the past when making simple Flask servers but let's take a look at some brief descriptions:

1. **Get** - Fetch the information.
2. **Post** - Create *new* information.
3. **Put** - Update/Replace the *all* of the information with new data.
4. **Patch** - Update/Replace *part* of a the information with new data.
5. **Delete** - Remove the information from the source.

You may notice that there are a lot of similarities with the structure of a *CRUD* application which if we remember specifies being able to *C*reate, *R*ead, *U*pdate and *D*elete.
## 2. User Specific Patterns of Routes/Endpoint URLs

In order for our endpoint to be *Restful* we have to have a specific pattern of routes in our applicaton.

| HTTP Verbs | /articles                    | /articles/jack-bauer                            |
| ---------- | ---------------------------- | ----------------------------------------------- |
| GET        | Fetches **all** the articles | Fetches **the** article on jack-bauer           |
| POST       | Creates **one** new article  | -                                               |
| PUT        | -                            | Updates **the** article on jack-bauer           |
| PATCH      |                              | Updates *part* of **the** article on jack-bauer |
| DELETE     | Deletes **all** the articles | Deletes **the** article on jack-bauer           |
# Python Example

## GET Random Cafe

```python
# HTTP GET - Read Record
@app.route("/random", methods=["GET"])
def random():
    try:
        result = db.session.execute(db.select(Cafe).order_by(Cafe.name))
        all_cafes = result.scalars().all()
        if not all_cafes:
            return jsonify({"error": "No cafes found"}), 404

        random_cafe = choice(all_cafes)

        return jsonify(
            cafe={
                "id": random_cafe.id,
                "name": random_cafe.name,
                "map_url": random_cafe.map_url,
                "img_url": random_cafe.img_url,
                "location": random_cafe.location,
                "seats": random_cafe.seats,
                "has_toilet": random_cafe.has_toilet,
                "has_wifi": random_cafe.has_wifi,
                "has_sockets": random_cafe.has_sockets,
                "can_take_calls": random_cafe.can_take_calls,
                "coffee_price": random_cafe.coffee_price,
            }
        )
    except SQLAlchemyError as e:
        print(f"Database query failed: {e}")
        return jsonify({"error": "Database error occurred"}), 500
```

In this example we're creating a route that is mapped to the `/random` route expecting a 'Get' request. We use the jsonify library to provide our responses as json and use `try` and `if` to provide appropriate responses for cases where the expected result is not returned. Notice that status codes are provided for those cases.
## POST New Cafe

```python
@app.route("/add_cafe", methods=["POST"])
def add_cafe():
    new_cafe_info = request.args
    new_cafe = Cafe(
        name=new_cafe_info.get("name", ""),
        map_url=new_cafe_info.get("map_url", ""),
        img_url=new_cafe_info.get("img_url", ""),
        location=new_cafe_info.get("location", ""),
        seats=new_cafe_info.get("seats", ""),
        has_toilet=new_cafe_info.get("has_toilet", "False").lower() in ["true", "1"],
        has_wifi=new_cafe_info.get("has_wifi", "False").lower() in ["true", "1"],
        has_sockets=new_cafe_info.get("has_sockets", "False").lower() in ["true", "1"],
        can_take_calls=new_cafe_info.get("can_take_calls", "False").lower()
        in ["true", "1"],
        coffee_price=new_cafe_info.get("coffee_price", ""),
    )

    try:
        result = db.session.execute(db.select(Cafe).order_by(Cafe.name))
        all_cafes = result.scalars().all()
        if db_has_name(new_cafe, all_cafes):
            return jsonify({"error": f"Database already has {new_cafe.name}"}), 400
        else:
            db.session.add(new_cafe)
            db.session.commit()

    except SQLAlchemyError as e:
        return jsonify({"error": f"Database error {e} occured"}), 500

    return jsonify({"success": f"Added {new_cafe.name} to the Database"}), 200
```

## PUT/PATCH Existing Cafe

```python
@app.route("/update-price/<int:cafe_id>", methods=["PUT", "PATCH"])
def update_price(cafe_id):
    cafe_to_update = Cafe.query.get_or_404(
        cafe_id, description=f"Cafe at ID:{cafe_id} not Found"
    )
    new_price = request.args.get("coffee_price", None)
    if new_price is not None:

        if len(new_price) > 250:
            return (
                jsonify(
                    {"error": "Coffee price exceeds maximum length of 250 characters"}
                ),
                400,
            )

        try:
            cafe_to_update.coffee_price = new_price
            db.session.commit()
            return jsonify({"message": "Coffee price updated successfully"}), 200
        except DataError:
            return jsonify({"error": "Invalid data for coffee price"}), 400
    else:
        return jsonify({"error": "No coffee price provided"}), 400

```

## DELETE Cafe

```python
@app.route("/delete-cafe/<int:cafe_id>", methods=["DELETE"])
def delete_cafe(cafe_id):
    cafe_to_delete = Cafe.query.get_or_404(
        cafe_id, description=f"Cafe at ID:{cafe_id} not Found"
    )

    try:
        db.session.delete(cafe_to_delete)
        db.session.commit()
    except SQLAlchemyError as e:
        return jsonify({"error": f"Database Error {e} Occured"}), 500
    return jsonify({"success": f"Cafe ID:{cafe_id} Deleted"}), 200
```