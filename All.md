## Install virtual environment in terminal of  IDE like visual studio code or PyCharm 
```

```

```
pip install virtualenv
```
```
virtualenv venv
```
### Activate the virtual environment for windows
```
venv/Scripts/activate
```
### Activate the virtual environment for linux
```
source venv/bin/activate
```
### installing django
```
pip install django
```
### create a project in django
```
django-admin startproject science_project .
```
### create a app in django
```
python manage.py startapp science_app
```
## Do all the setup and configuration in Project settings.py in one go
### Register app in project settings.py inside Installed apps 
```
'science_app.apps.ScienceAppConfig',
```
### setup static files 
```
STATIC_URL = 'static/'
STATICFILES_DIRS= [

    os.path.join(BASE_DIR / 'static'),
]
STATIC_ROOT = os.path.join(BASE_DIR, 'staticfiles')
```
### setup media files
```
MEDIA_URL = "/media/"
MEDIA_ROOT = BASE_DIR / "media"
```
## Now setup the urls.py of project to newly created urls.py in apps  full setup
### Configuration in projects urls.py

```
from django.contrib import admin
from django.conf import settings
from django.urls import path,include
from django.conf.urls.static import static


urlpatterns = [
    path('admin/', admin.site.urls),
    path('',include('science_app.urls')),
] 

if settings.DEBUG:  # new (media setup)
    urlpatterns += static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)

```
### Configuration in app urls.py (function based view)
```
from django.urls import path
from . import views
urlpatterns = [
    path('',views.home, name ='home'),
] 
```
### Configuration in app urls.py (class based view)
```
from django.urls import path
from . import views
urlpatterns = [
    path('',home.as_view(), name ='home'),
] 
```
## Inside app models.py

 

