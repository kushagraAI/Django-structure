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
| Model Type                         |          Usages                                                 |
| ---------------------------------- | -----------------------------------------------------------------|
|    |     |
| models.BinaryField()      |   store binary data (e.g. images, audio or other multimedia objects      |       
|  	models.BooleanField()  |    boolean field to store True/False (or 0/1) values  |
| models.NullBooleanField()   |  BooleanField but also allows NULL values   |
| models.DateField()   | Creates a date field to store dates    |
|  models.TimeField()  | Creates a time field to store times.    |
| models.DateTimeField()   |  Creates a datetime field to store dates with times   |
| models.DurationField()   |   Creates a field to store periods of time.  |
| models.AutoField()   |  Creates an integer that autoincrements, primarly used for custom primary keys   |
|  models.BigIntegerField()  |  big integer numbers between -9223372036854775808 to 9223372036854775807. depending DB brand   |
| 	models.DecimalField(decimal_places=X,max_digits=Y)   |   number have a maximum X digits and Y decimal points. X and Y arguments are required.   |
|  models.FloatField()  |  Creates a column to store floating-point numbers.   |
| models.IntegerField()   |  Creates a column to store integer numbers.   |
| models.PositiveIntegerField()   | values from 0 to 2147483647 Works just like IntegerField but limits values to positive number    |
| models.PositiveSmallIntegerField()   |   values from 0 to 32767 Works just like IntegerField and the specialized PositiveIntegerField  |
| options.SmallIntegerField()   |  number is in the range from -32768 to 32767   |
| models.CharField(max_length=N)  |  Creates a text column, where the max_length argument is required   |
| models.TextField()    | Creates a text field to store text.    |
|models.CommaSeparatedIntegerField(max_length=50)    |  Django enforces the string be a comma separated value of integers prior to interacting with the database (e.g. 3,54,54,664,65)   |
|models.EmailField()   |text is a valid email with the internal Django EmailValidator to determine what is and isn't a valid     |
|models.FileField()  |  opening/closing file, upload location,etc). defaulting to a max_length of 100 characters   |
|models.FilePathField()    | limit choices of filenames in certain filesystem directories. max_length of 100 characters    |
|models.ImageField()   | image files (e.g. getting the height & width) . defaulting to a max_length of 100 characters requires the presence of the Pillow Python library (e.g. pip install Pillow).    |
|models.GenericIPAddressField()    |  only accept valid IPv4 or IPv6 addresses (e.g. 198.10.22.64 and FE80::0202:B3FF:FE1E:8329, as well as utilities like unpack_ipv4 and protocol) defaulting to a max_length of 39 characters   |
|models.SlugField()    | string that only contains letters, numbers, underscores or hyphens. defaulting to a max_length of 50 characters   |
|models.URLField()   |  text value is a valid URL Works just like CharField defaulting to a max_length of 200 characters  |
|models.UUIDField()  |   text is a Universally unique identifiers (UUID) Works just like CharField defaulting to a max_length of 32 characters   |
|    |     |


 

