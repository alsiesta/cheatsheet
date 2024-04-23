## Django Deploy to Azure Web App

Get reliable results by **always deploy via Github Actions**. 

Github actions execute .zip package deployment by pushing a release.zip to azure.

Somehow, this is not happening the same way when using Azure Tools in VSC when doing a simple PUSH deployment directly to the Azure Web App.

According to this article, you can only deploy via Github actually:
https://stackoverflow.com/questions/57666646/how-do-you-pip-install-libraries-to-the-antenv-venv-on-an-azure-web-app

#### Read how to handle LOCAL ENV for deploy to Python Web App on Azure.
https://learn.microsoft.com/en-us/azure/developer/python/configure-python-web-app-local-environment?tabs=terminal-bash%2Cdjango

_________
#### Tips Django Settings.py 
***Study more about Oryx*** the MS tool for build and deploy processing. Learn how Oryx builds and runs under the hood. 

Add Azure App Service's default suffix to the list of allowed hosts in  settings.py: 
```
// settings.py
ALLOWED_HOSTS = [
    '.azurewebsites.net', '127.0.0.1', 'some_domain.com'
]
```
Or simply set `ALLOWED_HOSTS = ['*']` for testing


Set `DEBUG = True` if you want verbose ERRORS for debuging. 
For Production  `DEBUG = False`, so the frontend only produces simple 404 errors that don't unveil any confidential code.
```
// settings.py
DEBUG = True
```
__________

## IMPORTANT
#### If Push Deployment from VSC, you need to set Environment Variable: DJANGO_SETTINGS_MODULE in Azure!
*(this is not necessary, if you push code via Github Actions, because Git takes better care of proper Env. Setup!)*

You need to set `DJANGO_SETTINGS_MODULE = <projectname>.settings` in WebApp Configuration as Env. Variable or Oryx Build process won't find the Django settings to include in Container Root

______________
### add CSRF TRUSTE DOMAIN
Also add trusted Origin Parameters to allow the Azure Web App to access Django's default Admin page. Make sure the domain doesn't contain a trailing slash like `"....domain.net/"`
```
// settings.py
CSRF_TRUSTED_ORIGINS = ['https://www.domain.net'] //For Django 4.0 and above "scheme and host" are needed
CSRF_TRUSTED_ORIGINS = ['www.domain.net'] //For Django 3.2 and lower only "host" is needed
```

Some helpful links:
https://stackoverflow.com/questions/38841109/csrf-validation-does-not-work-on-django-using-https

https://learn.microsoft.com/en-us/training/modules/django-deployment/3-deployment-considerations

_____

### APP Setting (crispy_forms, crispy_bootstrap etc.)

```
//settings.py
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'crispy_forms',
    "crispy_bootstrap4",
    'relecloud.apps.RelecloudConfig',
]

CRISPY_ALLOWED_TEMPLATE_PACKS = "bootstrap4"  // important 
CRISPY_TEMPLATE_PACK = 'bootstrap4'  // important 
```

##### Important!
The requirements.txt have to be on root level like manage.py, .git, .gitignore venv .vscode etc.
```
//requirements.txt
django
django-crispy-forms
crispy-bootstrap4
whitenoise
```

##### Whitenoise 
Packages static files during deployment
https://whitenoise.readthedocs.io/en/stable/
`pip install whitenoise` 

```
//settings.py
MIDDLEWARE = [
    'django.middleware.security.SecurityMiddleware',
    'django.contrib.sessions.middleware.SessionMiddleware',
    'django.middleware.common.CommonMiddleware',
    'django.middleware.csrf.CsrfViewMiddleware',
    'django.contrib.auth.middleware.AuthenticationMiddleware',
    'django.contrib.messages.middleware.MessageMiddleware',
    'django.middleware.clickjacking.XFrameOptionsMiddleware',
    'whitenoise.middleware.WhiteNoiseMiddleware',
]
```
Whitenoise takes care of the static files and puts them at the right spot in HOST directory.
```
// settings.py (close to bottom file)

STATIC_URL = '/static/'

STATICFILES_STORAGE = 'whitenoise.storage.CompressedManifestStaticFilesStorage'
STATIC_ROOT = BASE_DIR / 'staticfiles'
```

Oryx runs manage.py ***collectstatic*** on your behalf unless you specify the DISABLE_COLLECTSTATIC env var. 
Make sure you've set STATIC_ROOT in settings.py
```
// settings.py
STATIC_ROOT = './static/'
```

#### Database changes
To apply database schema migrations following a build, create a post-build shell script and set its repo-relative path in the POST_BUILD_SCRIPT_PATH environment variable, e.g. `` `POST_BUILD_SCRIPT_PATH=./scripts/post.sh` The script should contain the following:
```
#! /usr/bin/env sh

python manage.py migrate
```


Further helpful links:
https://github.com/microsoft/Oryx/wiki/Django-Tips
