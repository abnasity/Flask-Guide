## ORGANIZING A FLASK PROJECT:
- A flask app can be organized inorder to make it more maintainable and scalable.
- The organization of a flask app can be done in the following way:

__
## File/Folder	Purpose
# templates 
- HTML files for rendering views
Used with Jinja2 templating engine.

Example:

templates/
  └── index.html
    └── about.html

# __init__.py	
- Initializes app and extensions
This is where you:

    Initialize the Flask app

    Set configurations

    Connect to the database

    Register blueprints

    Register error handlers

# *****example****
 from flask import Flask
from flask_sqlalchemy import SQLAlchemy

db = SQLAlchemy()

def create_app():
    app = Flask(__name__)
    app.config['SQLALCHEMY_DATABASE_URI'] = 'sqlite:///site.db'
    db.init_app(app)

    from .routes import main
    app.register_blueprint(main)

    return app

# models.py
	- Database models using SQLAlchemy

    Used with Flask-SQLAlchemy.

# ****Example:

from . import db

class User(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    username = db.Column(db.String(150), nullable=False)
    email = db.Column(db.String(150), unique=True, nullable=False)
# routes.py	
- URL routes and logic

Purpose: Defines routes/URLs and what happens when a user visits them.

Example:

from flask import Blueprint, render_template

main = Blueprint('main', __name__)

@main.route('/')
def home():
    return render_template('index.html')
    
# run.py	
- Starts the Flask server

# *******Example:

from myapp import create_app

app = create_app()

if __name__ == '__main__':
    app.run(debug=True)