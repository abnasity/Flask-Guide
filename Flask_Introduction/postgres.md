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
-To create a new table in PostgreSQL, you can use the following command: -->
# ```sql
 CREATE TABLE users (
    id SERIAL PRIMARY KEY,
 name VARCHAR(80) NOT NULL,
 email VARCHAR(120) UNIQUE NOT NULL
# );
# ```
-This command creates a new table called `users` with three columns: `id`, `name`, and `email`.
 -The `id` column is of type `SERIAL`, which automatically generates a unique identifier for each row.
 -The `name` column is of type `VARCHAR(80)`, which can store strings up to 80 characters long.
 -The `email` column is of type `VARCHAR(120)` and must be unique for each user.
#
# ## Inserting Data
# -To insert data into the `users` table, you can use the following command:
# ```sql
# INSERT INTO users (name, email) VALUES ('John Doe', 'johndoe@gmail.com');
# ```   

# CREATING FORMS IN FLASK
- Creating forms in Flask is commonly done using Flask-WTF, a Flask extension that integrates WTForms with Flask.
# Step by step guide to creating and using forms in Flask
1) install flask-WTF by using pip install flask-wtf
2) add a secret key for basic protection
           from flask import Flask

    app = Flask(__name__)
    app.secret_key = 'your_secret_key'
3) create a formclass by using the subclass FlaskForm
from flask_wtf import FlaskForm
from wtforms import StringField, SubmitField
from wtforms.validators import DataRequired

class NameForm(FlaskForm):
    name = StringField('Your Name', validators=[DataRequired()])
    submit = SubmitField('Submit')

4) create a view and render the form
         from flask import render_template, redirect, url_for
        from forms import NameForm

        @app.route('/', methods=['GET', 'POST'])
        def index():
            form = NameForm()
            if form.validate_on_submit():
                name = form.name.data
                return redirect(url_for('success', name=name))
            return render_template('index.html', form=form)

        @app.route('/success/<name>')
        def success(name):
            return f'Hello, {name}!'


5) Create an html template to render

            <!doctype html>
        <html>
        <head><title>Flask Form</title></head>
        <body>
        <form method="POST">
            {{ form.hidden_tag() }}
            {{ form.name.label }} {{ form.name(size=20) }}
            {{ form.submit() }}
        </form>
        </body>
        </html>

## NB - Always include {{ form.hidden_tag() }} for CSRF protection.