vv# What is SQL Alchemy?
vvvvV
SQL Alchemy is an ORM (Object-Relational Mapping) which allows us to work with the structure of the database is designed in a Class and we can work with rows in the database by reading them in as objects or creating our own objects and writing them to the database as new rows.

We are using SQL Alchemy along with Flask so that it is aware of the context of our web application and is able to manage connections to the database when endpoints in our server are accessed by the user.
# Creating a Model

Once we have created and initialized our Flask Application:
## Initializing the Database

```python
from flask import Flask, jsonify, render_template, request
from flask_sqlalchemy import SQLAlchemy
from sqlalchemy.orm import DeclarativeBase, Mapped, mapped_column
from sqlalchemy import Integer, String, Boolean


app = Flask(__name__)


# CREATE DB
class Base(DeclarativeBase):
    pass


# Connect to Database
app.config["SQLALCHEMY_DATABASE_URI"] = "sqlite:///cafes.db"
db = SQLAlchemy(model_class=Base)
db.init_app(app)
```

-we can create a Class representing our table configuration:
## Creating the Class

```python
# Cafe TABLE Configuration
class Cafe(db.Model):
    id: Mapped[int] = mapped_column(Integer, primary_key=True)
    name: Mapped[str] = mapped_column(String(250), unique=True, nullable=False)
    map_url: Mapped[str] = mapped_column(String(500), nullable=False)
    img_url: Mapped[str] = mapped_column(String(500), nullable=False)
    location: Mapped[str] = mapped_column(String(250), nullable=False)
    seats: Mapped[str] = mapped_column(String(250), nullable=False)
    has_toilet: Mapped[bool] = mapped_column(Boolean, nullable=False)
    has_wifi: Mapped[bool] = mapped_column(Boolean, nullable=False)
    has_sockets: Mapped[bool] = mapped_column(Boolean, nullable=False)
    can_take_calls: Mapped[bool] = mapped_column(Boolean, nullable=False)
    coffee_price: Mapped[str] = mapped_column(String(250), nullable=True)
```

If the database doesn't already exist we can create it with the following:
## Creating the Database

```python
with app.app_context():
    db.create_all()
```

This will generate a `cafes.db` file in the `./instance/` directory. 

Now we are ready to create, read, update and delete fields from our database.
# CRUD Tasks with SQL Alchemy

## Reading Items from the Database

```python
result = db.session.execute(db.select(Cafe).order_by(Cafe.name))
all_cafes = result.scalars()
```

We use the `db.session.execute()` command to execute an SQL query, in this instance we  want to return all the rows from the Cafe table with each row represented as an instance of the Cafe ORM model. Finally we sort them by the 'name' column.

We use `scalars()` to ensure that only information related to the Cafe ORM model is returned excluding any other meta data or unrelated information in the table.

We can also return a list rather than an SQL Alchemy object by using `scalars().all()`. This is useful when you may want to pass the the information to HTML templates.
## Searching for Items in the Database

```python
# cafe_location variable = Location we're searching
cafe_location_query = db.session.execute(
	db.select(Cafe).where(Cafe.location == cafe_location)
).scalar()
```

In this example we're querying the database for an entry where the location of the cafe is equal to the variable we're passing in. The important method here is `where()`. Using this method we pass in our query as where the value we're querying is equivalent to the value at a specified attribute of the model.

**Note**: `scalar()` is used here in place of `scalars()` as we only intend to return a single row from the database. # Error Handling

We can use `try` statements to throw exceptions when we have errors relating to accessing the database, let's continue with our Cafe database as an example:

```python 
from sqlalchemy.exc import SQLAlchemyError

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

Should we fail to execute a command via SQL Alchemy we'll return code 500 along with a description for why the get request failed and the same is true for the instance where the SQL Query was successful but no information was returned.
## Adding Items to the Database

In order to add an item to our database we first need to create an object using the model we created earlier.

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
```

In this example we're creating a post request endpoint for a user to submit a new item to the database via submitting the information via the request parameters. We then create a new `Cafe` object using the following constructor defined in the `Cafe` class:

**Note**: It's important to provide appropriate alternative results for the `.get()` method in the event that it is unable to fetch data under that key.

```python
def __init__(
	self,
	name,
	map_url,
	img_url,
	location,
	seats,
	has_toilet,
	has_wifi,
	has_sockets,
	can_take_calls,
	coffee_price,
):
	self.name = name
	self.map_url = map_url
	self.img_url = img_url
	self.location = location
	self.seats = seats
	self.has_toilet = has_toilet
	self.has_wifi = has_wifi
	self.has_sockets = has_sockets
	self.can_take_calls = can_take_calls
	self.coffee_price = coffee_price
```

Now with the new object we can attempt to commit it to our database:

```python
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

Again we're making sure to report any possible errors with our database query but because the **title of the database is unique** we first check if there isn't an existing database entree with the same name using our own `db_has_name(cafe_o, cafe_list)` function which simply iterates through the list of cafes and checks for a matching name.

Once we're sure that we can safely commit the object to the database we use the `db.session.add()` method and finally commit using `db.session.commit()`.
## Updating Existing Records in the Database

```python
@app.route('/update-price/<int:cafe_id>', methods=['PUT', 'PATCH'])
def update_price(cafe_id):
    cafe_to_update = Cafe.query.get_or_404(cafe_id, description=f"Cafe at ID:{cafe_id} not Found")
    new_price = request.args.get("coffee_price", None)
    if new_price is not None:

        if len(new_price) > 250:
            return jsonify({"error": "Coffee price exceeds maximum length of 250 characters"}), 400

        try:
            cafe_to_update.coffee_price = new_price
            db.session.commit()
            return jsonify({"message": "Coffee price updated successfully"}), 200
        except DataError:
            return jsonify({"error": "Invalid data for coffee price"}), 400
    else:
        return jsonify({"error": "No coffee price provided"}), 400
```

In order to update an existing row in the database we first need to fetch that specific item. In this case we're using the ID to query the database with `.query.get_or_404(id, description)`. This method will automatically return 404 if no row is found at that ID and we can provide a description for the 404 message to help the user understand where his query failed. Normally a generic 404 message is supplied which may confuse the user into thinking that they have incorrectly accessed the endpoint.

Once we have an object for the row that we intend to update we can update the attribute for that object as we would any other object of a class and make a commit to the database again.
## Deleting a Record from the Database:

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

Deleting a row is quite simple, all we need to do is retrieve the object from the database and pass it into the `.session.delete()` method and make a commit to the database.