# Django RestAPI
```
python manage.py startapp myapp
```
## add myapp to installed app in settings.py

make a serialize.py in myapp

### serialize.py
``` python
from rest_framework import serializers


class HelloWorldSerializer(serializers.Serializer):
    message = serializers.CharField()

```
## Create views
### myapp/views
``` python
from rest_framework.views import APIView
from rest_framework.response import Response

class HelloWorldView(APIView):
    return Response({"message: "Hello, world!"})

```
## Create route
### myapp/urls.py
```python
from django.urls import path
from .views import HelloworldView

urlpatterns = [path("", HelloWorldView.as_view(), name="hello-world")]

```

## add myapp urls to the project urls
### myproject/urls
``` python
from django.contrib import admin
from django.urls import path, include  # add include here

urlpatterns = [path("admin/", admin.site.urls), path("", include("myapp.urls"))]

```
