# Django

## Creating a new project

1. Install Django in global python so the django-admin utility is available
```shell
pip install Django
```
2. Run django-admin startproject YOUR_PROJECT_NAME which creates the skeleton directores of a Django project and cd into it.

```shell
django-admin startproject project
cd project
```
3. Initialize git as usual
```shell
git init
```
4. Create a virtual environment specific to the current application. When you install libraries and other tools, you'll want them only installed for this app and not your global python installation.
Activate the virtual environment by sourcing the activate script. *All python commands from now* on use the python / pip in the virtual env.

```shell
python -m venv venv
. ./venv/bin/activate
```

5. Upgrade pip and install django locally
```shell
pip install --upgrade pip
pip install Django
```

6. Always save your local pip installs to the requirements.txt file so the project can be reinstalled on another machine.
```shell
pip freeze > requirements.txt
```

7. Commit the application to git.
```shell
git commit -am "Initial Commit"
```

## Loading a project

```shell
cd project
. ./venv/bin/activate
pip install -r requirements.txt
```
