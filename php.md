# 🚀 **PHP - The Ultimate Guide (From Basics to Advanced)**  

PHP (**Hypertext Preprocessor**) is a **server-side scripting language** used for web development and backend logic.

---

## 📌 **1. Installation & Setup**
### **Windows**
1. Download **XAMPP**: [https://www.apachefriends.org](https://www.apachefriends.org)
2. Start Apache & MySQL from XAMPP Control Panel.
3. Place PHP files inside `C:\xampp\htdocs\`.
4. Open a browser and go to `http://localhost/`.

### **Linux / Mac**
```sh
sudo apt install php  # Ubuntu
brew install php      # Mac
php -v               # Check version
```

Run a PHP script:
```sh
php myscript.php
```

---

## 🏗 **2. Basic Syntax**
- **PHP inside HTML**
```php
<!DOCTYPE html>
<html>
<body>
    <h1><?php echo "Hello, World!"; ?></h1>
</body>
</html>
```
- **Basic PHP Script**
```php
<?php
echo "Hello, PHP!";
?>
```

---

## ✨ **3. Variables & Data Types**
```php
<?php
$name = "Sri";  // String
$age = 22;      // Integer
$price = 10.5;  // Float
$isAdmin = true; // Boolean
?>
```

- **Constants**
```php
define("SITE_NAME", "MyWebsite");
echo SITE_NAME;
```

---

## 🔄 **4. Control Structures**
### **If-Else**
```php
<?php
$age = 18;
if ($age >= 18) {
    echo "You are an adult!";
} else {
    echo "You are a minor!";
}
?>
```

### **Loops**
```php
// For Loop
for ($i = 1; $i <= 5; $i++) {
    echo "Number: $i <br>";
}

// While Loop
$i = 1;
while ($i <= 5) {
    echo "While Loop: $i <br>";
    $i++;
}

// Foreach Loop (for arrays)
$colors = ["Red", "Green", "Blue"];
foreach ($colors as $color) {
    echo "$color <br>";
}
```

---

## 📚 **5. Arrays**
```php
// Indexed Array
$fruits = ["Apple", "Banana", "Mango"];
echo $fruits[1]; // Banana

// Associative Array
$person = ["name" => "Sri", "age" => 22];
echo $person["name"]; // Sri

// Multidimensional Array
$users = [
    ["Sri", 22],
    ["John", 30]
];
echo $users[0][0]; // Sri
```

---

## 🛠 **6. Functions**
```php
<?php
function greet($name) {
    return "Hello, $name!";
}
echo greet("Sri");
?>
```

---

## 🔥 **7. Superglobals**
PHP provides built-in global arrays like:
- `$_GET` → Get request data.
- `$_POST` → Post request data.
- `$_SESSION` → Store session data.
- `$_COOKIE` → Store small data in browser.

### **Example: Form Handling**
```php
<form method="post" action="process.php">
    Name: <input type="text" name="name">
    <input type="submit">
</form>
```
**process.php**
```php
<?php
echo "Hello, " . $_POST["name"];
?>
```

---

## 🛑 **8. Sessions & Cookies**
### **Session (Store User Data)**
```php
session_start();
$_SESSION["username"] = "Sri";
echo $_SESSION["username"];
```

### **Cookies (Small Data Stored in Browser)**
```php
setcookie("user", "Sri", time() + 3600); // Expires in 1 hour
echo $_COOKIE["user"];
```

---

## 🗄 **9. File Handling**
### **Read a File**
```php
$content = file_get_contents("test.txt");
echo $content;
```
### **Write to a File**
```php
file_put_contents("test.txt", "Hello World!");
```

---

## 🔌 **10. Database (MySQL)**
### **Connect to Database**
```php
$pdo = new PDO("mysql:host=localhost;dbname=test", "root", "");
```

### **Create Table**
```php
$pdo->exec("CREATE TABLE users (id INT AUTO_INCREMENT, name VARCHAR(50), PRIMARY KEY(id))");
```

### **Insert Data**
```php
$pdo->exec("INSERT INTO users (name) VALUES ('Sri')");
```

### **Fetch Data**
```php
$result = $pdo->query("SELECT * FROM users");
foreach ($result as $row) {
    echo $row['name'];
}
```

---

## 🚀 **11. PHP with Node.js Example**
Use **PHP as a backend** and **Node.js as a frontend** to communicate via API.

### **PHP (API)**
```php
<?php
header("Content-Type: application/json");
echo json_encode(["message" => "Hello from PHP"]);
?>
```

### **Node.js (Fetch Data from PHP API)**
```js
fetch("http://localhost/api.php")
  .then(res => res.json())
  .then(data => console.log(data.message));
```

---

## 🔥 **12. PHP Frameworks**
| Framework | Use Case |
|-----------|----------|
| Laravel  | Full-stack web apps |
| CodeIgniter | Lightweight MVC framework |
| Symfony | Enterprise-level apps |

---

## 🎯 **13. Interview Questions**
### **Basic**
- What is PHP?
- Explain the difference between `GET` and `POST`.
- What are sessions and cookies?
- How do you connect PHP to MySQL?
- Explain the difference between `==` and `===` in PHP.

### **Advanced**
- What is PDO in PHP?
- How does PHP handle file uploads?
- Explain the difference between **static** and **dynamic** websites.
- How can you prevent SQL Injection in PHP?
- How does PHP handle memory management?

---

## 🚀 **14. Deploying PHP**
### **1. XAMPP (Local)**
- Place PHP files in `htdocs/`
- Run `http://localhost/file.php`

### **2. Deploy on a Web Server**
- Use Apache or Nginx.
- Upload PHP files to a server.
- Run `php index.php`.

---

## 🎉 **15. Conclusion**
PHP is still a **powerful** and **widely used** language for web development. By mastering PHP, you can build **dynamic web applications, APIs, and full-stack applications**.

🚀 **Keep learning & start building!**