## USING POSTGRESQL WITH FLASK
#
-PostgreSQL is a powerful, open-source object-relational database system. It is widely used in production environments and can be easily integrated with Flask applications.
#
# ## INSTALLING POSTGRESQL
# -To use PostgreSQL with Flask, you need to install the `psycopg2` package, which is a PostgreSQL adapter for Python.
# -You can install it using pip:
# ```bash
# pip install psycopg2
# ```
#
 ## CONFIGURING POSTGRESQL IN FLASK
 -To configure PostgreSQL in your Flask application, you need to set the `SQLALCHEMY_DATABASE_URI` to the PostgreSQL connection string.
-The connection string format is:
# ```bash
 postgresql://username:password@localhost:5432/database_name
# ```
 -Here's an example of how to set it up in your Flask app:
# ```python
# from flask import Flask
# from flask_sqlalchemy import SQLAlchemy
#
# app = Flask(__name__)
# app.config['SQLALCHEMY_DATABASE_URI'] = 'postgresql://username:password@localhost:5432/database_name'
# app.config['SQLALCHEMY_TRACK_MODIFICATIONS'] = False
# db = SQLAlchemy(app)
#
# class User(db.Model):
#     id = db.Column(db.Integer, primary_key=True)
#     name = db.Column(db.String(80), nullable=False)
#     email = db.Column(db.String(120), unique=True, nullable=False)    


#     def __repr__(self):
#         return f'<User {self.name}>'

## Entering the PostgreSQL Shell
# -To enter the PostgreSQL shell, you can use the following command:
# ```bash
# psql -U username -d database_name
# ```
# -Replace `username` with your PostgreSQL username and `database_name` with the name of your database.
# -Once you are in the shell, you can run SQL commands to interact with your database.

-- # ## Creating a Database
# -To create a new database in PostgreSQL, you can use the following command in the PostgreSQL shell:
# ```sql
# CREATE DATABASE database_name;
# ```
# -Replace `database_name` with the name you want to give to your new database.
# -After creating the database, you can connect to it using the following command:
# ```sql
# \c database_name;
# ```
# -This will switch you to the new database, and you can start creating tables and inserting data.
# -->
# ## Creating a Table
# -To create a new table in PostgreSQL, you can use the following command: -->