---
layout: post
title: "Mental Note: Django 1.4.x and Storm .19"
date: 2013-02-21 15:52
comments: true
categories: [ubuntu, django]
---

Some notes on getting Storm used as a database backend for Django. Props to James Henstridge for doing the heavy lifting.

### Setup virtualenv and install dependencies: ###

``` console
$ virtualenv --prompt=stormy venv
$ source venv/bin/activate
$ pip install django storm psycopg2 pytz python-dateutil
$ pip freeze > requirements.txt
```

### Setup django skeleton ###

``` console
$ django-admin.py startproject myproject
$ cd myproject
$ python manage.py startapp common
```

### Edit **settings.py** to include the proper middleware and STORM_STORES ###

``` python settings.py
MIDDLEWARE_CLASSES = (
    'django.middleware.common.CommonMiddleware',
    'django.contrib.sessions.middleware.SessionMiddleware',
    'django.middleware.csrf.CsrfViewMiddleware',
    'django.contrib.auth.middleware.AuthenticationMiddleware',
    'django.contrib.messages.middleware.MessageMiddleware',
    'storm.django.middleware.ZopeTransactionMiddleware',       # Added this line
    # Uncomment the next line for simple clickjacking pro
)

STORM_STORES = { 'default' : "postgres://adam@localhost/testdb" }
```

### Next in my app add some models ###

``` python common/models.py
from django.db import models
from storm.sqlobject import StringCol, UtcDateTimeCol, BoolCol, IntCol
from storm.locals import Int
from storm.expr import SQL
from datetime import datetime
from pytz import UTC
import dateutil.parser

class Bug(models.Model):
    __storm_table__ = "bug"
    id = Int(primary=True,)
    date_created = UtcDateTimeCol(notNull=True,)
    date_last_message = UtcDateTimeCol()
    date_last_updated = UtcDateTimeCol()
    date_made_private = UtcDateTimeCol()
    description = StringCol(notNull=True,)
    duplicate_of = IntCol()
    heat = IntCol()
    gravity = IntCol()
    information_type = StringCol()
    latest_patch_uploaded = UtcDateTimeCol()
    message_count = IntCol(notNull=True,)
    number_of_duplicates = IntCol()
    other_users_affected_count_with_dupes = IntCol()
    owner = IntCol(notNull=True,)
    private = BoolCol(notNull=True, default=False,)
    security_related = BoolCol(notNull=True, default=True,)
    tags = StringCol()
    title = StringCol(notNull=True,)
    users_affected_count = IntCol()
    users_affected_count_with_dupes = IntCol()
    web_link = StringCol()
    who_made_private = IntCol()
```

### Pull the data into the view ###

``` python common/views.py
from django.core.context_processors import csrf
from django.shortcuts import render_to_response, HttpResponseRedirect
from storm.django.stores import *
from myproject.common.models import *

def index(request):
    store = get_store('default')
    bug = store.find(Bug)
    return render_to_response("common/index.html", { 'bug' : bug })
```

### Finally, edit the template to display the data ###

``` html templates/common/index.html
{% raw %}
{% extends 'layout.html' %}

{% block page_name %}Home{% endblock %}

{% block content %}
<ul>
{% for b in bug %}
<li>{{ b.id }} : {{ b.title }}</li>
{% endfor %}
</ul>
{% endblock content %}
{% endraw %}
```

Things to do:

* Have **get_store** persisted when the application starts
* Integrate migrations with South
* Integrate with something like celery for running some background jobs

I haven't done anything major other than a few queries so time will tell how well this does when this project really gets into making use of Storm.
