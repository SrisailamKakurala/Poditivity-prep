# 🚀 **Firebase Firestore & Realtime Database (RDB) - Complete Guide**  
> **Covers:** Basics, Structure, Queries, Security, Node.js Code Examples  

---

## 📌 **1. Firestore vs. Realtime Database (RDB)**
| Feature               | Firestore 🔥 | Realtime Database 🌐 |
|-----------------------|-------------|----------------------|
| **Data Structure**    | NoSQL (Documents & Collections) | JSON (Nested Objects) |
| **Scalability**       | Better (Indexes, Queries) | Limited (Single JSON Tree) |
| **Offline Support**   | Yes ✅ | Yes ✅ |
| **Pricing**           | Per Read/Write | Per Bandwidth |
| **Best For**         | Large-scale Apps | Real-time Sync Apps |

---

## 🏗 **2. Firestore Basics (NoSQL - Documents & Collections)**  
Firestore uses **collections** and **documents** instead of JSON trees.

### **🔥 Firestore Data Model Example**
```
users (Collection)
 ├── userId_123 (Document)
 │    ├── name: "Sri"
 │    ├── age: 25
 │    ├── email: "sri@email.com"
```

### **🌐 Realtime Database Data Model Example**
```json
{
  "users": {
    "userId_123": {
      "name": "Sri",
      "age": 25,
      "email": "sri@email.com"
    }
  }
}
```

---

## 📌 **3. Firestore CRUD Operations (Node.js)**
### **📌 Install Firebase SDK**
```bash
npm install firebase-admin
```

### **📌 Initialize Firestore**
```javascript
const admin = require("firebase-admin");
const serviceAccount = require("./serviceAccountKey.json");

admin.initializeApp({
  credential: admin.credential.cert(serviceAccount)
});

const db = admin.firestore();
```

---

### **🔥 Create & Update Document**
```javascript
await db.collection("users").doc("userId_123").set({
  name: "Sri",
  age: 25,
  email: "sri@email.com"
});
```

---

### **🔥 Read Document**
```javascript
const doc = await db.collection("users").doc("userId_123").get();
console.log(doc.data());
```

---

### **🔥 Query Data**
```javascript
const users = await db.collection("users").where("age", ">", 20).get();
users.forEach(doc => console.log(doc.id, doc.data()));
```

---

### **🔥 Delete Document**
```javascript
await db.collection("users").doc("userId_123").delete();
```

---

## 📌 **4. Realtime Database (RDB) CRUD Operations (Node.js)**
### **📌 Initialize Realtime Database**
```javascript
const database = admin.database();
```

---

### **🔥 Create & Update Data**
```javascript
await database.ref("users/userId_123").set({
  name: "Sri",
  age: 25,
  email: "sri@email.com"
});
```

---

### **🔥 Read Data**
```javascript
database.ref("users/userId_123").once("value", (snapshot) => {
  console.log(snapshot.val());
});
```

---

### **🔥 Listen for Realtime Changes**
```javascript
database.ref("users").on("child_changed", (snapshot) => {
  console.log("Updated User:", snapshot.val());
});
```

---

### **🔥 Delete Data**
```javascript
await database.ref("users/userId_123").remove();
```

---

## 🔥 **5. Firestore Security Rules**
```json
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /users/{userId} {
      allow read, write: if request.auth.uid == userId;
    }
  }
}
```

---

## 🔥 **6. Realtime Database Security Rules**
```json
{
  "rules": {
    "users": {
      "$uid": {
        ".read": "$uid === auth.uid",
        ".write": "$uid === auth.uid"
      }
    }
  }
}
```

---

## 🎯 **7. Firestore vs. RDB - When to Use?**
| **Use Firestore When:** | **Use Realtime Database When:** |
|-------------------------|--------------------------------|
| Scalable apps, complex queries | Real-time sync, chat apps |
| Multi-region availability | IoT, low-latency apps |
| Indexed searching | Lightweight structure |

---

## 🎯 **8. Common Interview Questions**
✅ **Difference between Firestore and Realtime Database?**  
✅ **How does Firestore handle indexing?**  
✅ **How to optimize Firestore queries?**  
✅ **What are Firestore triggers in Cloud Functions?**  
✅ **How does Firestore pricing work?**  
✅ **How to secure Firestore database?**  

---

## 🔥 **9. Conclusion**
✅ **Firestore = Modern, Scalable, Best for Large Apps**  
✅ **Realtime Database = Simple, Best for Real-time Sync**  
✅ **Node.js integration is easy & scalable**  

Now you are **Firestore & RDB PRO** 🚀 Let me know if you need **practice problems** or **real-world use cases**!