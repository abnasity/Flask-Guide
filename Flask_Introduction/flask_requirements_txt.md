## REQUIREMENTS.txt

in flask, requirements.txt is a file that lists the dependencies and packages required for your Flask application to run. It is commonly used in Python projects to manage package installations and ensure that the correct versions of libraries are installed.
#
# ## Creating a requirements.txt file
# -You can create a requirements.txt file manually or use the pip freeze command to generate it automatically.
# -To create it manually, you can simply create a text file named requirements.txt and list the required packages and their versions.
# -To generate it automatically, you can use the following command:
# ```bash
# pip freeze > requirements.txt
# ```
# -This command will create a requirements.txt file with all the currently installed packages and their versions in your virtual environment.
#
# ## Installing packages from requirements.txt
# -To install the packages listed in requirements.txt, you can use the following command:
# ```bash
# pip install -r requirements.txt
# ```
# -This command will read the requirements.txt file and install all the listed packages and their specified versions.
# -This is useful for setting up a new environment or sharing your project with others.

example of a requirements.txt file for a Flask project:
```plaintext
Flask==2.0.1    
Flask-SQLAlchemy==2.5.1
Flask-Migrate==3.1.0
Flask-WTF==0.15.1
Flask-Login==0.5.0
Flask-Mail==0.9.1
Flask-Cors==3.0.10
Flask-RESTful==0.3.9
Flask-Cache==0.13.1
Flask-Admin==1.5.8
Flask-Script==2.0.6
Flask-Testing==0.8.1
Flask-DebugToolbar==0.11.0
Flask-Babel==2.0.0 e.tc.