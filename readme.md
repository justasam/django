# Django & Postges install notes

## Virtual environment setup

> virtual environment, which is a feature built into Python that allows you to keep a separate directory of installed packages for each of your projects so that they don’t interfere with each other.

Create a new virtual environment by:

`$ python3 -m venv ~/.virtualenvs/django`

Activate it:

`$ source ~/.virtualenvs/django/bin/activate`

or:

`$ . ~/.virtualenvs/django/bin/activate`

or (Windows):

`$ ...\> %HOMEPATH%\.virtualenvs\djangodev\Scripts\activate.bat`

## Install Django

Official realease:

`$ pip install Django`

Development version:

`$ git clone https://github.com/django/django.git`

`$ pip install -e django/`

## Create a project (env)

`$ django-admin startproject mysite`

`$ python manage.py runserver`

## Create an app

`$ python manage.py startapp polls`

## Setup Postgres

Install Python Postgres driver:

`$ pip install psycopg2`


Install Postgres DB itself (following is for arch linux):

~~~~
$ yaourt -Sy postgresql-lts
$ initdb -D '/var/lib/postgres/data'
$ systemctl start postgresql.service
$ systemctl enable postgresql.service

$ createuser --interactive
$ createdb dbname -O username
~~~~

Change settings.py in mysite/settings.py

~~~~
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql_psycopg2',
        'NAME': 'dbname',
        'USER': 'username',
        'PASSWORD': '',
        'HOST': '',
        'PORT': '',
    }
}
~~~~