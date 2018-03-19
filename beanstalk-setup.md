1. create new python environment
```bash
virtualenv my-env
```
```bash
cd my-env
```
2. intall django
```bash
pip install django
```

3. create a django project
```bash
python startproject myproject
```
or clone the the project and skip step 4.
if you cloned the project also install the requirements

```bash
cd myproject
pip install -r requirements.txt
```
4. build the django app
```bash
cd myproject
python manage.py migrate
```

5. use git to commit
```bash
git init
git add .
git commit -m "initial commit"
```
6. create configuration file for eb
```bash
mkdir .ebextensions
nano .ebextensions/python.config
```
and enter
```bash
option_settings:
  aws:elasticbeanstalk:container:python:
    WSGIPath: realestate/wsgi.py
  "aws:elasticbeanstalk:container:python:staticfiles":
            /static/: "wowa/static/"
```
7. create and deploy project 
```bash
eb init
eb create myproject
