## Here are some of the steps of creating a registration form in flask
1) install flask wtf by using pip install flask-wtf

2) Create the registration form in forms.py

# forms.py
from flask_wtf import FlaskForm
from wtforms import StringField, PasswordField, SubmitField
from wtforms.validators import DataRequired, Email, EqualTo, Length

class RegistrationForm(FlaskForm):
    username = StringField('Username', validators=[DataRequired(), Length(min=3, max=25)])
    email = StringField('Email', validators=[DataRequired(), Email()])
    password = PasswordField('Password', validators=[DataRequired(), Length(min=6)])
    confirm_password = PasswordField('Confirm Password', validators=[
        DataRequired(), EqualTo('password', message='Passwords must match')
    ])
    submit = SubmitField('Register')

3) Create a view in flask

# app.py
__init__.py
from flask import Flask, render_template, redirect, url_for, flash
from forms import RegistrationForm

app = Flask(__name__)
app.secret_key = 'your_secret_key'

# routes.py
@app.route('/register', methods=['GET', 'POST'])
def register():
    form = RegistrationForm()
    if form.validate_on_submit():
        # Here you’d typically save the user to the database
        flash(f'Registration successful for {form.username.data}!', 'success')
        return redirect(url_for('login'))
    return render_template('register.html', form=form)

@app.route('/login')
def login():
    return "Login Page"


4) Create the Registration template

<!-- templates/register.html -->
<!doctype html>
<html>
<head><title>Register</title></head>
<body>
  <h1>Register</h1>
  <form method="POST">
    {{ form.hidden_tag() }}
    
    <p>
      {{ form.username.label }}<br>
      {{ form.username(size=32) }}<br>
      {% for error in form.username.errors %}
        <span style="color: red;">[{{ error }}]</span>
      {% endfor %}
    </p>
    
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

    <p>
      {{ form.confirm_password.label }}<br>
      {{ form.confirm_password(size=32) }}<br>
      {% for error in form.confirm_password.errors %}
        <span style="color: red;">[{{ error }}]</span>
      {% endfor %}
    </p>

    <p>{{ form.submit() }}</p>
  </form>
</body>
</html>

## NB - Use Flask-Login for user session management.

## ✅ Key Fixes

    Indentation: Both print(...) and return render_template(...) must be inside the register() function.

    Used username instead of first_name in flash() if first_name doesn’t exist on your model.

 ##   # REGISTRATION ROUTE
@app.route('/register', methods=['GET', 'POST'])
def register():
    form = RegistrationForm()
    
    if form.validate_on_submit():
        new_user = User(
            username=form.username.data,
            email=form.email.data,
            password=form.password.data
        )
        db.session.add(new_user)
        db.session.commit()
        flash(f'{new_user.username} successfully registered!', 'success')
        return redirect(url_for('register'))

    print(form.errors)  # ✅ Indented properly inside the function
    return render_template('register.html', title='Register', user_form=form)
