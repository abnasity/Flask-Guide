 Flask blueprints are a way to organize your Flask application into smaller, reusable components. They allow you to group related routes, templates, and static files together, making your application more modular and easier to maintain.

## WHY USE BLUEPRINTS?
-Better organization of code
-Easy to reuse across different projects
-Makes your app modular and scalable
-Encourages separation of concerns
-Allows for easier testing and debugging
-Helps in managing large applications
-Encourages a clean 

directory structure-Improves collaboration among developers


## STEPS TO CREATE A BLUEPRINT

1. Create a new directory for your blueprint (e.g., `my_blueprint`).

2. Inside the directory, create an `__init__.py` file to define the blueprint.

3. Define your blueprint in the `__init__.py` file:

```python
from flask import Blueprint
my_blueprint = Blueprint('my_blueprint', __name__)

from . import routes  # Import routes to register them with the blueprint
```
4. Create a `routes.py` file in the same directory to define your routes:

```python
from flask import render_template
from . import my_blueprint
@my_blueprint.route('/hello')
def hello():
    return render_template('hello.html')
```
5. In your main application file (e.g., `app.py`), register the blueprint:

```python
from flask import Flask

from my_blueprint import my_blueprint
app = Flask(__name__)
app.register_blueprint(my_blueprint, url_prefix='/my_blueprint')
```
6. Create a `templates` directory inside your blueprint directory to store your templates (e.g., `my_blueprint/templates/hello.html`):

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hello</title>
</head>
<body>
    <h1>Hello from the Blueprint!</h1>
</body>
</html>
```



## EXAMPLE OF A BLUEPRINT

```python
from flask import Flask, Blueprint, render_template
from flask_sqlalchemy import SQLAlchemy
from flask_migrate import Migrate
from flask_wtf import FlaskForm
from wtforms import StringField, TextAreaField, BooleanField, SubmitField
from wtforms.validators import DataRequired, Length
from flask import flash, redirect, url_for
from flask import request
from flask import jsonify
from flask import make_response
from flask import session