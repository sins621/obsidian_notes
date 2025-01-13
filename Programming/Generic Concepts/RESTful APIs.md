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