# What is SQL Alchemy?

SQL Alchemy is an ORM (Object-Relational Mapping) which allows us to work with the structure of the database is designed in a Class and we can work with rows in the database by reading them in as Objects or creating our own Objects and writing them to the database as new rows.

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

```python nums
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