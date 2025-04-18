
# app.py

# To run the Flask app, use the command:
# python app.py
# Make sure to install Flask first:
# pip3 install Flask
# This code sets up a simple Flask web application that returns "Hello, Flask! 🎉" when accessed at the root URL.
# This is a basic Flask application that serves a simple "Hello, Flask!" message.

from flask import Flask

app = Flask(__name__)

@app.route('/')
def home():
    return 'Hello, Flask! 🎉'

if __name__ == '__main__':
    app.run(debug=True)


## ▶️ 2. Run the Flask app

In your terminal (with virtual environment activated):

python app.py

You should see output like:

 * Running on http://127.0.0.1:5000/ (Press CTRL+C to quit)


## 🛠 Tip: Want to auto-reload when you change the code?

Set the FLASK_ENV to development. This enables debug mode.
Linux/macOS:

export FLASK_APP=app.py
export FLASK_ENV=development
flask run


## FLASK-SQLALCHEMY PROPERTIES
A Flask App has its own properties and configurations. Here are some common ones:
[]: 
[]: - `SQLALCHEMY_DATABASE_URI`: The database URI.
[]: - `SQLALCHEMY_TRACK_MODIFICATIONS`: Set to False to disable track modifications.
[]: - `SQLALCHEMY_ECHO`: Set to True to log SQL queries.
[]: 
[]: ## 🔹 Flask-SQLAlchemy vs SQLAlchemy
[]: 
[]: - Flask-SQLAlchemy is a wrapper around SQLAlchemy that provides additional features and simplifies the integration with Flask.
[]: - It provides a more Flask-like API and integrates better with Flask's application context.
[]: 
[]: ## 🔹 Flask-SQLAlchemy vs Flask-Migrate
[]: 
[]: - Flask-SQLAlchemy is for database ORM and management.
[]: - Flask-Migrate is for handling database migrations.
[]: 
[]: ## 🔹 Flask-SQLAlchemy vs SQLAlchemy ORM
[]: 
[]: - SQLAlchemy ORM is the core library for object-relational mapping.
[]: - Flask-SQLAlchemy is a Flask extension that builds on top of SQLAlchemy ORM.
[]: 
[]: ## 🔹 Flask-SQLAlchemy vs SQLAlchemy Core
[]: 
[]: - SQLAlchemy Core is the low-level API for SQLAlchemy.
[]: - Flask-SQLAlchemy is a higher-level abstraction that simplifies the usage of SQLAlchemy in Flask applications.
[]: 
[]: ## 🔹 Flask-SQLAlchemy vs Flask-SQLite
[]: 
[]: - Flask-SQLAlchemy is a general-purpose ORM for various databases.
[]: - Flask-SQLite is specifically for SQLite databases.

## SQL Alchemy  VS flask-alchemy
# SQL Alchemy
-SQL Alchemy is a powerful SQL toolkit and Object Relational Mapper (ORM) for Python.
-It is a powerful python library that provides a set of high level API tools for working with relational databases.
# flask-alchemy
-flask-alchemy is a Flask extension that adds SQL Alchemy support to Flask applications.
-It adds SQLAlchey support to a Flask Application.
-It is a wrapper around SQL Alchemy that makes it easier to use with Flask.

## Feature |             SQLAlchemy                            |               Flask-SQLAlchemy
What it is | A powerful database toolkit and ORM for Python    | A Flask extension that integrates SQLAlchemy with Flask
Use Case   | Standalone Python apps or advanced setups         |         Flask web apps
Setup      | Manual engine/session management                  | Simplified setup via Flask config
Syntax     | Verbose, full control                             | Cleaner, Flask-friendly syntax
Ideal For  | Large/custom apps, non-Flask projects             | Flask apps, rapid development


## 🔹 What is SQLAlchemy?

    Core Python library for working with databases.

    Provides two layers:

        SQL Expression Language (low-level, like writing raw SQL in Python).

        ORM (Object Relational Mapping — maps classes to DB tables).

    Can be used in any Python project (Flask, Django, FastAPI, or even without a framework).

   ## 🔹 What is Flask-SQLAlchemy?

    A thin wrapper around SQLAlchemy made for Flask.

    Simplifies configuration and common patterns.

    Adds Flask-friendly helpers like db.Model, Model.query, and auto-managed sessions.

## CONFIGURATION OF FLASK-ALCHEMY
from flask import Flask
from flask_sqlalchemy import SQLAlchemy

app = Flask(__name__)
app.config['SQLALCHEMY_DATABASE_URI'] = 'sqlite:///mydatabase.db'
db = SQLAlchemy(app)

## CREATING A MODEL
class User(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    name = db.Column(db.String(80), nullable=False)
    email = db.Column(db.String(120), unique=True, nullable=False)

## CRUD OPERATIONS
# Create
-Add a new record 
new_user = User(name='John Doe',)
db.session.add(new_user)
db.session.commit()

# Read
-Retrieve data from the database
all_users = User.query.all()
single_
# ****Read***
user = User.query.filter_by(name='John Doe').first()

# Update
-Change an existing record
user.name = 'Jane Doe'
db.session.commit()

# Delete
-Remove a record
# Delete a user
user = User.query.get(1)
if user:
db.session.delete(user)
db.session.commit()
# This code sets up a simple Flask web application with SQLAlchemy support, allowing you to perform CRUD operations on a User model.


## Other flask extensions
- Flask-WTF: For handling forms and CSRF protection.
- Flask-Migrate: For database migrations.
- Flask-Login: For user authentication.
- Flask-Mail: For sending emails.
- Flask-RESTful: For building REST APIs.


## Extra Features in Flask-SQLAlchemy

    Model.query – shorthand for session.query().

    paginate() – built-in support for pagination.

    get_or_404(), first_or_404() – helpful for Flask-based APIs.

## 🔹 Common Config Options

app.config['SQLALCHEMY_TRACK_MODIFICATIONS'] = False  # avoid overhead
app.config['SQLALCHEMY_ECHO'] = True  # log SQL queries


## When Should You Use Which?
Scenario	Use
You're building a Flask web app	✅ Flask-SQLAlchemy
You need maximum control or are not using Flask	✅ SQLAlchemy
You want to scale up with custom DB logic	✅ SQLAlchemy
You’re doing quick prototyping or REST APIs in Flask	✅ Flask-SQLAlchemy