## 🚀 **Django - The High-Level Python Web Framework**  

Django is a **full-stack Python web framework** used for building secure, scalable, and maintainable web applications quickly.  

---

## 📌 **1. Installation**
```sh
pip install django
```
Create a Django project:  
```sh
django-admin startproject myproject
cd myproject
python manage.py runserver
```
Access: `http://127.0.0.1:8000/`

---

## 🏗 **2. Django Project Structure**
```
myproject/
│── myproject/      # Project settings
│── myapp/          # Django app
│── manage.py       # Django CLI tool
│── db.sqlite3      # Database (default SQLite)
```

Create an app:  
```sh
python manage.py startapp myapp
```

---

## 🔗 **3. Views & URLs**
### **views.py**
```python
from django.http import HttpResponse

def home(request):
    return HttpResponse("Hello, Django!")
```
### **urls.py**
```python
from django.urls import path
from myapp.views import home

urlpatterns = [
    path('', home),
]
```

---

## 📂 **4. Templates & Static Files**
### **views.py**
```python
from django.shortcuts import render

def home(request):
    return render(request, "index.html", {"name": "Sri"})
```
### **index.html**
```html
<h1>Hello, {{ name }}!</h1>
```
### **settings.py**
```python
TEMPLATES = [
    {
        'DIRS': [BASE_DIR / "templates"],
    },
]
```

---

## 🛠 **5. Models & Database**
### **models.py**
```python
from django.db import models

class User(models.Model):
    name = models.CharField(max_length=100)
    age = models.IntegerField()
```
Run migrations:  
```sh
python manage.py makemigrations
python manage.py migrate
```

---

## 🔑 **6. Django Admin**
Create superuser:  
```sh
python manage.py createsuperuser
```
Register model in **admin.py**:
```python
from django.contrib import admin
from .models import User

admin.site.register(User)
```
Access admin panel: `http://127.0.0.1:8000/admin/`

---

## 🏆 **7. Django ORM (Database Queries)**
```python
# Create a user
user = User.objects.create(name="Sri", age=25)

# Fetch all users
users = User.objects.all()

# Filter users
users = User.objects.filter(age__gte=18)

# Update a user
user.age = 30
user.save()

# Delete a user
user.delete()
```

---

## 🔒 **8. User Authentication**
```sh
python manage.py startapp accounts
```
### **settings.py**
```python
INSTALLED_APPS += ['accounts']
```
### **views.py**
```python
from django.contrib.auth import authenticate, login

def user_login(request):
    user = authenticate(username="admin", password="pass123")
    if user:
        login(request, user)
        return HttpResponse("Login Successful")
```

---

## 🔗 **9. Django REST Framework (DRF)**
```sh
pip install djangorestframework
```
### **settings.py**
```python
INSTALLED_APPS += ['rest_framework']
```
### **views.py**
```python
from rest_framework.decorators import api_view
from rest_framework.response import Response

@api_view(['GET'])
def api_home(request):
    return Response({"message": "Hello, DRF!"})
```
### **urls.py**
```python
from django.urls import path
from .views import api_home

urlpatterns = [
    path('api/', api_home),
]
```

---

## ⚡ **10. Deployment**
```sh
pip install gunicorn
gunicorn myproject.wsgi:application
```
- Deploy on AWS, Heroku, or DigitalOcean.

---

## 📌 **11. Interview Questions**
- What is Django?  
- How is Django different from Flask?  
- What is Django ORM?  
- How does Django handle authentication?  
- What is middleware in Django?

---

🚀 **Master Django & Build Scalable Web Apps!**