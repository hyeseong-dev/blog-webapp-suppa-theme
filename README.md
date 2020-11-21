# Project 소개 
---
- This is a simple Django 3.1 blog project. This project is deployed on Heroku. Not that difficult but it is not necessary.

## Features
---
- Django 3.1
- Uses `venv` - Python packagin tool from Python.org
- Development,Staging and Production settings with [Django settings](https://docs.djangoproject.com/en/3.1/topics/settings/#calling-django-setup-is-required-for-standalone-django-usage)
- MySQL8.0 database support with mysqlclinet
- Gunicorn webserver instead of using uwsgi.much fatster, simpler and easy to us.

## How to install 
```
$ git clone https://github.com/hyeseong-dev/blog-webapp-suppa-theme.git
$ python -m venv env
$ source env/Scripts/activate
$ pip install -r requirements.txt
$ python manage.py migrate
$ python manage.py runserver
```

## settings.py
```
DEBUG = True # Change `False` when deployed!

ALLOWED_HOSTS = ['0.0.0.0','127.0.0.1',] # additional hosts you want to add.


# Application definition

INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',

    "blog.apps.BlogConfig",
    "widget_tweaks", 
]


...
...
...

STATIC_ROOT = BASE_DIR/'staticfiles'
STATIC_URL = '/static/'
    
STATICFILES_DIRS = [
    os.path.join(BASE_DIR, "static"),
]

MEDIA_URL = "/media/"
MEDIA_ROOT = os.path.join(BASE_DIR, "media")
```

## Deployment
It is possible to deploy to Heroku or to you own server.

### Heroku
- It is not difficult just follow the instruction on the Heroku document website >> [install heroku](https://devcenter.heroku.com/articles/heroku-cli)

#### Procfile
```
web: gunicorn django_project.wsgi
```


```
$ heroku --version
$ heroku login 
$ git add . 
$ git commit -m 'Hello World!'
$ heroku create          # you can find your app name after this.
$ heroku git:remote -a 'your app name'
$ git push heroku master 

```

