######
README
######

Twitter Bootstrap layout for `django-allauth
<https://github.com/pennersr/django-allauth>`_.

.. note::

   The current version 0.2 supports **Django's** registration and
   login via ``django-allauth``. Support for **social accounts**
   will be added in one of the upcoming versions.


Requirements
============

* Python 2.7 or >=3.3.
* Django >=1.9


Installation
============

Installation via::

   pip install django-allauth-bootstrap

The templates extend ``base.html``, so the ``templates`` folder of the
project should provide one, together with the Twitter Bootstrap and a JQuery
library.

Then add ``'bootstrapform'`` and ``'allauth_bootstrap'`` to
``INSTALLED_APPS``, *before* ``'allauth'``.  The order is important because
following apps are overwritten::

   INSTALLED_APPS = [
       # ...
       'django.contrib.sites',  # For ``allauth``.

       'bootstrapform',
       'allauth_bootstrap',
       'allauth',
       'allauth.account',
       # ...
   ]

For allauth itself, remember to add the following settings::

   TEMPLATES = [
       {
           'BACKEND': 'django.template.backends.django.DjangoTemplates',
           'DIRS': [],
           'APP_DIRS': True,
           'OPTIONS': {
               'context_processors': [
                   # Already defined Django-related contexts here

                   # `allauth` needs this from django
                   'django.template.context_processors.request',
               ],
           },
       },
   ]

   SITE_ID = 1

   LOGIN_REDIRECT_URL = '/'


Example Project
===============

The example project can be run to have a quick look and to check out a
running setup. Download the source files and run::

   virtualenv -p /usr/bin/python3 ~/myenv
   source ~/myenv/bin/activate
   pip install -r requirements.txt
   ./manage.py migrate
   ./manage.py runserver


Customization
=============

To use custom templates, there are two ways to accomplish that:

1. Overwrite a template at ``templates/account`` to replace them completely.
2. Inherit a template at ``templates/account`` to overwrite only one or more
   of its blocks. Defining a custom URL pointing at the custom template is
   necessary then.
