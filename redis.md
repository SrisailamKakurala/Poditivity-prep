# 🚀 **Redis: Complete Guide (Windows + Node.js)**
> **Covers:** Installation, Commands, Node.js Examples  

---

## 📌 **1. Installing Redis on Windows**  
Redis does not have an official Windows version, but you can install it using **WSL (Windows Subsystem for Linux)** or an **Unofficial Port**.

### **🔥 Method 1: Install Redis on Windows using WSL (Recommended)**
1️⃣ **Enable WSL** (Windows Subsystem for Linux)  
Open **PowerShell as Admin** and run:  
```powershell
wsl --install
```
2️⃣ **Install Ubuntu from Microsoft Store**  
3️⃣ **Install Redis inside WSL:**  
```bash
sudo apt update && sudo apt install redis-server -y
sudo systemctl start redis
```
4️⃣ **Test Redis Connection:**  
```bash
redis-cli ping  # Response: PONG
```

---

### **🔥 Method 2: Install Redis on Windows (Unofficial Port)**
1️⃣ **Download Redis for Windows**  
- Go to **[Memurai](https://memurai.com/download)** (Redis-compatible Windows version)  
- Download & Install  

2️⃣ **Start Redis Server:**  
```powershell
redis-server.exe
```
3️⃣ **Open Redis CLI in Another Terminal:**  
```powershell
redis-cli
ping  # Response: PONG
```

---

## 🏗 **2. Redis CLI Commands (Full List)**

### **1️⃣ Basic Key-Value Commands**
```bash
SET name "Sri"  # Store a value
GET name        # Retrieve a value
DEL name        # Delete a key
EXISTS name     # Check if a key exists (1 = Yes, 0 = No)
```

### **2️⃣ Expiration & TTL**
```bash
SET session "active"
EXPIRE session 60  # Set TTL of 60 sec
TTL session        # Check TTL remaining
```

### **3️⃣ Lists (Ordered Collection)**
```bash
LPUSH queue "task1" "task2"  # Push elements (Left)
RPUSH queue "task3"          # Push element (Right)
LPOP queue                   # Remove first element
RPOP queue                   # Remove last element
LRANGE queue 0 -1            # Get all elements
```

### **4️⃣ Hashes (Key-Value Store Inside a Key)**
```bash
HSET user:100 name "Sri" age 25
HGET user:100 name
HGETALL user:100  # Get all fields
```

### **5️⃣ Sets (Unique Collection, No Duplicates)**
```bash
SADD fruits "apple" "banana" "orange"
SMEMBERS fruits
```

### **6️⃣ Sorted Sets (Ranking System)**
```bash
ZADD leaderboard 100 "player1"
ZADD leaderboard 200 "player2"
ZRANGE leaderboard 0 -1 WITHSCORES  # Get scores
```

### **7️⃣ Transactions (Atomic Execution)**
```bash
MULTI
SET count 1
INCR count
EXEC  # Execute all at once
```

### **8️⃣ Pub/Sub Messaging**
```bash
PUBLISH news "Breaking News!"
SUBSCRIBE news
```

---

## 🏗 **3. Using Redis in Node.js**  

### **🛠 Install Redis in Node.js**
```bash
npm install redis
```

---

### **1️⃣ Connecting to Redis**
```javascript
const redis = require("redis");
const client = redis.createClient({ url: "redis://localhost:6379" });

client.connect().then(() => console.log("Connected to Redis"));
```

---

### **2️⃣ Basic Key-Value Operations**
```javascript
await client.set("name", "Sri");
const value = await client.get("name");
console.log("Stored Name:", value);
```

---

### **3️⃣ Expiring Keys (TTL)**
```javascript
await client.setEx("session", 60, "active"); // Expires in 60s
```

---

### **4️⃣ Working with Lists**
```javascript
await client.lPush("queue", "task1");
await client.rPush("queue", "task2");
const tasks = await client.lRange("queue", 0, -1);
console.log(tasks); // Output: ["task1", "task2"]
```

---

### **5️⃣ Hashes (User Profiles)**
```javascript
await client.hSet("user:100", { name: "Sri", age: "25" });
const user = await client.hGetAll("user:100");
console.log(user); // { name: 'Sri', age: '25' }
```

---

### **6️⃣ Using Sets (Unique Values)**
```javascript
await client.sAdd("fruits", "apple", "banana", "orange");
const fruits = await client.sMembers("fruits");
console.log(fruits);
```

---

### **7️⃣ Sorted Sets (Leaderboards)**
```javascript
await client.zAdd("leaderboard", { score: 100, value: "player1" });
await client.zAdd("leaderboard", { score: 200, value: "player2" });
const topPlayers = await client.zRange("leaderboard", 0, -1, { withScores: true });
console.log(topPlayers);
```

---

### **8️⃣ Transactions (Atomic Execution)**
```javascript
await client.multi()
  .set("counter", 1)
  .incr("counter")
  .exec();
```

---

### **9️⃣ Pub/Sub Messaging**
```javascript
const subscriber = client.duplicate();
await subscriber.connect();

subscriber.subscribe("news", (message) => {
  console.log("Received:", message);
});

await client.publish("news", "Breaking News!");
```

---

## 🎯 **4. Redis Persistence: Saving Data Permanently**
🔹 **RDB (Snapshot-based persistence)**
```bash
SAVE    # Save snapshot manually
BGSAVE  # Save snapshot in background
```
🔹 **AOF (Append-Only File for Logging)**
```bash
CONFIG SET appendonly yes
```

---

## 🛡 **5. Security Best Practices**
✅ **Use Redis Password**  
```bash
requirepass "YourSecurePassword"
```
✅ **Disable Remote Access**  
Edit `redis.conf`:  
```bash
bind 127.0.0.1
```
✅ **Use TLS Encryption (for secure connections)**

---

## 🚀 **6. Redis Caching Strategies**
1️⃣ **Least Recently Used (LRU) Cache**
```bash
CONFIG SET maxmemory-policy allkeys-lru
```
2️⃣ **Time-to-Live (TTL) Cache**
```javascript
await client.setEx("session", 60, "active"); // Expires in 60s
```

---

## 🔥 **7. Redis vs Other Databases**
| Feature       | Redis  | MySQL  | MongoDB |
|--------------|--------|--------|---------|
| Speed       | ⚡ Super Fast (In-Memory) | 🐢 Slower | 🚀 Fast |
| Data Model  | Key-Value | Relational | NoSQL |
| Persistence | Yes (RDB, AOF) | Yes | Yes |
| Use Cases  | Caching, Realtime | Transactions | Big Data |

---

## 🎯 **8. Common Redis Interview Questions**
✅ **What is Redis used for?**  
✅ **How does Redis handle persistence?**  
✅ **Difference between Redis and Memcached?**  
✅ **What are the different types of caching policies in Redis?**  
✅ **How do you implement a leaderboard in Redis?**  
✅ **What is the purpose of Redis Streams?**  
✅ **How to handle Redis Failover?**  
✅ **Explain Redis Clustering.**  

---

## 🔥 **Conclusion**
✅ Redis is FAST ⚡  
✅ Best for Caching, Queues, and Real-Time Data  
✅ Supports Transactions, Pub/Sub, and Clustering  
✅ Works seamlessly with Node.js  

**Now you are a Redis PRO!** 🚀 Let me know if you need **practice problems** or **real-world use cases**!