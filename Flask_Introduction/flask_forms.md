## CREATING FORMS IN FLASK
- Forms are used to collect user input in web applications.
- Flask-WTF is an extension that simplifies form handling in Flask.
- It integrates WTForms with Flask, providing features like CSRF protection, validation, and rendering.
- Flask-WTF is built on top of WTForms, which is a flexible forms validation and rendering library for Python web development.
- WTForms allows you to define forms in Python code, handle form submissions, and validate user input.
- Flask-WTF provides additional features like CSRF protection, file uploads, and integration with Flask's request context.
- Flask-WTF provides a convenient way to create and manage forms in Flask applications.
- It simplifies the process of creating forms, validating user input, and rendering forms in templates.


## STEPS TO CREATE A FORM IN FLASK
1. Install Flask-WTF:
   
   pip install Flask-WTF

# 2. Create the Form Class

Create a file like forms.py:

# forms.py
from flask_wtf import FlaskForm
from wtforms import StringField, TextAreaField, BooleanField, SubmitField
from wtforms.validators import DataRequired, Length

class TaskForm(FlaskForm):
    title = StringField('Title', validators=[DataRequired(), Length(max=100)])
    description = TextAreaField('Description')
    completed = BooleanField('Completed')
    submit = SubmitField('Create Task')

# 3. Update Your App Config (for CSRF)

In your app/__init__.py or config section:

app.config['SECRET_KEY'] = 'your_secret_key_here'




# 4. Create a Route and View

In your Flask view (routes.py or in your main file):

from flask import render_template, redirect, url_for, flash
from app.forms import TaskForm
from app.models import Task, db

@app.route('/create-task', methods=['GET', 'POST'])
def create_task():
    form = TaskForm()
    if form.validate_on_submit():
        new_task = Task(
            title=form.title.data,
            description=form.description.data,
            completed=form.completed.data,
            user_id=1  # Replace with actual user ID logic
        )
        db.session.add(new_task)
        db.session.commit()
        flash('Task created successfully!')
        return redirect(url_for('create_task'))
    return render_template('create_task.html', form=form)

# 5. Create a template for the form (create_task.html):



<!DOCTYPE html>
<html lang="en">
<head>
    <title>Create Task</title>
</head>
<body>
    <h1>Create a New Task</h1>
    <form method="POST">
        {{ form.hidden_tag() }}
        <p>{{ form.title.label }} {{ form.title() }}</p>
        <p>{{ form.description.label }} {{ form.description() }}</p>
        <p>{{ form.completed.label }} {{ form.completed() }}</p>
        <p>{{ form.submit() }}</p>
    </form>
</body>
</html>
