## 🚀 **FastAPI - The Modern Python Web Framework**  

FastAPI is a **high-performance web framework** for building APIs with **Python 3.7+**. It is **asynchronous, fast, and easy to use**.

---

## 📌 **1. Installation**
```sh
pip install fastapi uvicorn
```
- **FastAPI** → Web framework.  
- **Uvicorn** → ASGI server to run FastAPI.

---

## 🏗 **2. Basic FastAPI App**
```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def read_root():
    return {"message": "Hello, FastAPI!"}
```
Run the app:  
```sh
uvicorn app:app --reload
```
Access:  
`http://127.0.0.1:8000/`

---

## 📄 **3. Automatic Documentation**  
FastAPI provides **built-in Swagger UI & Redoc**:  
- **Swagger UI** → `http://127.0.0.1:8000/docs`
- **ReDoc UI** → `http://127.0.0.1:8000/redoc`

---

## 📌 **4. Path & Query Parameters**
```python
@app.get("/user/{user_id}")
def get_user(user_id: int):
    return {"user_id": user_id}

@app.get("/items/")
def get_items(q: str = "default"):
    return {"query": q}
```
- `http://127.0.0.1:8000/user/123` → `{ "user_id": 123 }`
- `http://127.0.0.1:8000/items/?q=phone` → `{ "query": "phone" }`

---

## 🔗 **5. Request Body (POST)**
```python
from pydantic import BaseModel

class User(BaseModel):
    name: str
    age: int

@app.post("/users/")
def create_user(user: User):
    return {"user": user}
```
Test it in **Swagger UI**!

---

## 📡 **6. Async & Await**
FastAPI supports async operations for better performance.  
```python
import asyncio

@app.get("/async_example")
async def async_example():
    await asyncio.sleep(1)
    return {"message": "This is async"}
```

---

## 🗃 **7. Database (SQLite + SQLAlchemy)**
```sh
pip install sqlalchemy databases sqlite
```
```python
from sqlalchemy import create_engine, Column, Integer, String
from sqlalchemy.ext.declarative import declarative_base
from sqlalchemy.orm import sessionmaker

DATABASE_URL = "sqlite:///./test.db"

engine = create_engine(DATABASE_URL)
SessionLocal = sessionmaker(autocommit=False, autoflush=False, bind=engine)
Base = declarative_base()

class User(Base):
    __tablename__ = "users"
    id = Column(Integer, primary_key=True, index=True)
    name = Column(String, index=True)
```

---

## 🔑 **8. JWT Authentication**
```sh
pip install pyjwt
```
```python
import jwt

SECRET_KEY = "your_secret"

def create_token(data: dict):
    return jwt.encode(data, SECRET_KEY, algorithm="HS256")

@app.post("/token")
def get_token(username: str):
    token = create_token({"user": username})
    return {"token": token}
```

---

## 🏆 **9. FastAPI with WebSockets**
```python
from fastapi import WebSocket

@app.websocket("/ws")
async def websocket_endpoint(websocket: WebSocket):
    await websocket.accept()
    await websocket.send_text("Hello WebSocket!")
    await websocket.close()
```

---

## 🚀 **10. Deployment with Uvicorn**
```sh
uvicorn app:app --host 0.0.0.0 --port 8000
```

---

## 📌 **11. Interview Questions**
- What is FastAPI?  
- How is FastAPI different from Flask?  
- How does FastAPI handle async requests?  
- How to implement authentication in FastAPI?  
- Explain Dependency Injection in FastAPI.

---

🚀 **Master FastAPI & Build High-Performance APIs!**