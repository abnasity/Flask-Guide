## utilizing .gitignore file in Flask project
python files and __pycache__ files needs to be untracked
-You can use a .gitignore file to specify files and directories that Git should ignore.
-Create a .gitignore file in the root directory of your Flask project.
-Add the following lines to the .gitignore file to ignore Python files and __pycache__ directories:
```plaintext
*.pyc
__pycache__/
```
-This will prevent these files from being tracked by Git.
-You can also add other files or directories that you want to ignore.
-For example, if you have a virtual environment directory named venv, you can add it to the .gitignore file:
```plaintext
venv/
```
-This will prevent the virtual environment from being tracked by Git.
-You can also add other files or directories that you want to ignore.
-For example, if you have a configuration file named config.py that contains sensitive information, you can add it to the .gitignore file:
```plaintext
config.py
```
-This will prevent the configuration file from being tracked by Git.
-You can also add other files or directories that you want to ignore.
-For example, if you have a database file named database.db that you don't want to track, you can add it to the .gitignore file:
```plaintext
database.db
```
-This will prevent the database file from being tracked by Git.
-You can also add other files or directories that you want to ignore.
-For example, if you have a log file named app.log that you don't want to track, you can add it to the .gitignore file:
```plaintext
app.log
```

## WHAT IF YOU HAVE ALRAEDT STAGED THE FILES?
-If you have already staged the files that you want to ignore, you need to unstage them first.
-You can use the following command to unstage the files:
```bash
git reset HEAD <file>
```
-Replace <file> with the name of the file that you want to unstage.
-For example, if you have staged the file app.py and you want to unstage it, you can use the following command:
```bash
git reset HEAD app.py
```
-This will unstage the file app.py and prevent it from being tracked by Git.
## OR
# USE THESE COMMANDS IN YOUR TERMINAL
# to remove all cached files that are in .gitignore
# This will remove all cached files that are in .gitignore
# and add all files that are not in .gitignore
git rm -r --cached .
git add .
git commit -m "Remove cached files that are in .gitignore"