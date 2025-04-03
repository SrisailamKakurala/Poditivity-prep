## 🚀 **Flask - From Basics to Advanced**  

Flask is a **lightweight, Python-based web framework** used to build **web applications & APIs**. It is **easy to use, flexible**, and follows the **WSGI standard**.

---

## 📌 **1. Installation**
```sh
pip install flask
```

---

## 🏗 **2. Basic Flask App**
```python
from flask import Flask

app = Flask(__name__)

@app.route('/')
def home():
    return "Hello, Flask!"

if __name__ == '__main__':
    app.run(debug=True)
```
- **`@app.route('/')`** → Defines a URL route.
- **`debug=True`** → Enables auto-reload on code changes.

Run it:  
```sh
python app.py
```
Access:  
`http://127.0.0.1:5000/`

---

## 🛠 **3. Routing & URL Parameters**
```python
@app.route('/user/<name>')
def greet(name):
    return f"Hello, {name}!"
```
- `http://127.0.0.1:5000/user/Sri` → Output: **"Hello, Sri!"**

---

## 🏗 **4. Handling GET & POST Requests**
```python
from flask import request

@app.route('/login', methods=['GET', 'POST'])
def login():
    if request.method == 'POST':
        return "Login Successful!"
    return "Send a POST request to log in."
```
- **GET** → Displays login page.  
- **POST** → Processes login.

---

## 🔗 **5. JSON API with Flask**
```python
from flask import jsonify

@app.route('/api')
def api():
    return jsonify({"message": "Welcome to Flask API"})
```
**Output (JSON):**
```json
{"message": "Welcome to Flask API"}
```

---

## 📂 **6. Template Rendering (HTML)**
### Install Jinja2 (comes with Flask)
```sh
pip install jinja2
```
### **HTML Template (`templates/home.html`):**
```html
<!DOCTYPE html>
<html>
<body>
    <h1>Welcome, {{ name }}!</h1>
</body>
</html>
```
### **Flask Route**
```python
from flask import render_template

@app.route('/welcome/<name>')
def welcome(name):
    return render_template('home.html', name=name)
```

---

## 🗃 **7. Flask with Database (SQLite)**
### **Install SQLite**
```sh
pip install flask-sqlalchemy
```
### **Define Database Model**
```python
from flask_sqlalchemy import SQLAlchemy

app.config['SQLALCHEMY_DATABASE_URI'] = 'sqlite:///users.db'
db = SQLAlchemy(app)

class User(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    name = db.Column(db.String(80), nullable=False)

db.create_all()
```
### **Insert Data**
```python
@app.route('/add/<name>')
def add_user(name):
    user = User(name=name)
    db.session.add(user)
    db.session.commit()
    return f"User {name} added!"
```

---

## 🔐 **8. Flask Authentication (Login)**
```sh
pip install flask-login
```
```python
from flask_login import LoginManager, UserMixin

login_manager = LoginManager()
login_manager.init_app(app)

class User(UserMixin):
    pass  # Define User model
```

---

## 🔥 **9. Flask REST API**
```python
from flask import request

@app.route('/data', methods=['POST'])
def post_data():
    data = request.get_json()
    return jsonify({"received": data})
```

---

## 🎯 **10. Flask with Socket.IO (WebSockets)**
```sh
pip install flask-socketio
```
```python
from flask_socketio import SocketIO

socketio = SocketIO(app)

@socketio.on('message')
def handle_message(msg):
    print(f"Message: {msg}")
    socketio.send(f"Echo: {msg}")

if __name__ == '__main__':
    socketio.run(app)
```

---

## ⚡ **11. Deploy Flask App**
### **Using Gunicorn (Production)**
```sh
pip install gunicorn
gunicorn -w 4 app:app
```

---

## 📌 **12. Interview Questions**
- What is Flask?
- How does Flask differ from Django?
- How do you handle database connections in Flask?
- How to implement JWT authentication in Flask?
- What are Flask Blueprints?

---

🚀 **Master Flask & Build Scalable Apps!**