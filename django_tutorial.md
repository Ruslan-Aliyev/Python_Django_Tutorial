# Django Tutorial

https://www.youtube.com/watch?v=VuETrwKYLTM&list=PLsyeobzWxl7poL9JTVyndKe62ieoN-MZ3&index=87

## Setup

### Ubuntu

### Mac

```
cd ~/Documents
pip install django
django-admin startproject tutorial # Create a project called tutorial
cd tutorial
python manage.py startapp calc     # Create an app (feature in project) called calc
python manage.py runserver         # Launch 
```

### Windows

3. Install Django. `(test) C:\Users\{username}\Documents>pip install django`.
4. `mkdir djangoprojs` & `cd djangoprojs`.
5. Create a project `django-admin startproject tutorial`.
6. Create an app (an app is like a feature inside a project) `cd tutorial` & `python manage.py startapp calc`.
7. Take a look of what you have so far by launching server `python manage.py runserver`.

## Notes

- Use `python manage.py help` to show all available commands.
- Django follow MVT pattern. View is like the controller and Template is like the view.

![](/Illustrations/django/mvt.PNG)

## 1a Hello World

In the newly created calc app, let's just make it say "Hello world" first.

`tutorial/urls.py`
```py
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('calc.urls')),
]
```

`calc/urls.py`
```py
from django.urls import path
from . import views

urlpatterns = [
    path('', views.home, name='home'),
]
```

`calc/views.py`
```py
from django.http import HttpResponse

def home(request):
	return HttpResponse("Hello world");	
```

## 1b Hello World with template

Create `templates/home.html`
```html
<h1>Hello world</h1>
```

`tutorial/settings.py`
```py
import os
# ...
TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [os.path.join(BASE_DIR, 'templates')],
```

`calc/views.py`
```py
from django.shortcuts import render

def home(request):
	return render(request, 'home.html');	
```

## 1c Hello World with template with passed data

`templates/home.html`
```html
<h1>Hello {{name}}</h1>
```

`calc/views.py`
```py
from django.shortcuts import render

def home(request):
	return render(request, 'home.html', {'name':'someone'});	
```

## 1d Hello World with template with passed data

Create `templates/base.html`
```html
<!DOCTYPE html>
<html>
	<title>Django Tutorial</title>
	<body>

		{% block content %}
		
		{% endblock %}

	</body>
</html>
```

`templates/home.html`
```html
{% extends 'base.html' %}

{% block content %}
<h1>Hello {{name}}</h1>
{% endblock %}
```

## 2a Addition

`templates/home.html`
```html
{% extends 'base.html' %}

{% block content %}
<form action="add">
	<input type="number" name="no1"><br>
	<input type="number" name="no2"><br>
	<input type="submit">
</form> 
{% endblock %}
```

Create `templates/result.html`
```html
{% extends 'base.html' %}

{% block content %}
<h1>Hello {{name}}</h1>

Result: {{result}}
{% endblock %}
```

`calc/urls.py`
```py
urlpatterns = [
    path('', views.home, name='home'),
    path('add', views.add, name='add'), # add this route
]
```

`calc/views.py`
```py
# ...
def add(request):
	no1 = int(request.GET['no1'])
	no2 = int(request.GET['no2'])
	result = no1 + no2

	return render(request, 'result.html', {'result':result});	
```

## 2b Addition (using POST)

`templates/home.html`
```html
{% extends 'base.html' %}

{% block content %}
<form action="add" method="post">
	{% csrf_token %}
	<input type="number" name="no1"><br>
	<input type="number" name="no2"><br>
	<input type="submit">
</form> 
{% endblock %}
```

`calc/views.py`
```py
# ...
def add(request):
	no1 = int(request.POST['no1'])
	no2 = int(request.POST['no2'])
	result = no1 + no2

	return render(request, 'result.html', {'result':result});	
```
