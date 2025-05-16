## Here are the steps for creating a login form in flask
 1) Create the login form
    # forms.py
from flask_wtf import FlaskForm
from wtforms import StringField, PasswordField, SubmitField
from wtforms.validators import DataRequired, Email

class LoginForm(FlaskForm):
    email = StringField('Email', validators=[DataRequired(), Email()])
    password = PasswordField('Password', validators=[DataRequired()])
    submit = SubmitField('Login')

2) Create a view in flask
# app.py
__init__.py
from flask import Flask, render_template, redirect, url_for, flash
from forms import LoginForm

app = Flask(__name__)
app.secret_key = 'your_secret_key'

# routes.py
@app.route('/login', methods=['GET', 'POST'])
def login():
    form = LoginForm()
    if form.validate_on_submit():
        # You would typically check the user's email/password here
        flash(f'Logged in as {form.email.data}', 'success')
        return redirect(url_for('dashboard'))
    return render_template('login.html', form=form)

@app.route('/dashboard')
def dashboard():
    return "Welcome to your dashboard!"


# Create the login template

<!-- templates/login.html -->
<!doctype html>
<html>
<head><title>Login</title></head>
<body>
  <h1>Login</h1>
  <form method="POST">
    {{ form.hidden_tag() }}

    <p>
      {{ form.email.label }}<br>
      {{ form.email(size=32) }}<br>
      {% for error in form.email.errors %}
        <span style="color: red;">[{{ error }}]</span>
      {% endfor %}
    </p>

    <p>
      {{ form.password.label }}<br>
      {{ form.password(size=32) }}<br>
      {% for error in form.password.errors %}
        <span style="color: red;">[{{ error }}]</span>
      {% endfor %}
    </p>

    <p>{{ form.submit() }}</p>
  </form>
</body>
</html>


# NB - Add Flask-Login for session management and access control.


## UserMixins
-UserMixin is a helper class provided by Flask-Login. When you add it to your user model, it automatically provides default implementations for the methods Flask-Login needs.


# - UserMixins are a set of mixin classes that can be used to add common user-related functionality to your models.
# - They are typically used in conjunction with Flask-Login to manage user authentication and authorization.
# - Common UserMixins include:
#   - UserMixin: Provides basic user authentication methods.
#   - AnonymousUserMixin: Represents an anonymous user.
#   - RoleMixin: Provides role-based access control.
# - You can create your own custom UserMixins to add specific functionality to your user models.
# - Example of a custom UserMixin:

## 🚀 Methods Provided by UserMixin

By inheriting from UserMixin, your user model gets:

Method/Property	Purpose
is_authenticated	Returns True if the user is authenticated.
is_active	Returns True if the user's account is active.
is_anonymous	Returns False for regular users (used for anonymous sessions).
get_id()	Returns a unique ID for the user, usually used to load them from a DB.

from flask_login import UserMixin

class User(UserMixin, db.Model):
    id = db.Column(db.Integer, primary_key=True)
    username = db.Column(db.String(150), unique=True, nullable=False)
    email = db.Column(db.String(150), unique=True, nullable=False)
    password = db.Column(db.String(150), nullable=False)
    # Other fields...
    def __repr__(self):
        return f'<User {self.username}>'