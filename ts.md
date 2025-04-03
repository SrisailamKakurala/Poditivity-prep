# 🚀 **TypeScript - The Complete Guide (Beginner to Advanced)**  

**TypeScript (TS)** is a **superset of JavaScript** that adds **static typing** and other powerful features. It helps catch errors at compile-time, making code more robust and maintainable.  

---

## 📌 **1. Installation & Setup**  
### **Install TypeScript**  
```sh
npm install -g typescript
```
Check the version:  
```sh
tsc -v
```

### **Compile a TypeScript File**  
```sh
tsc index.ts   # Compiles index.ts to index.js
```

### **Initialize a TypeScript Project**
```sh
tsc --init  # Creates tsconfig.json
```

---

## ✨ **2. Type Annotations**
```ts
let username: string = "Sri";
let age: number = 22;
let isAdmin: boolean = true;
```

---

## 🔥 **3. Functions in TypeScript**
```ts
function add(a: number, b: number): number {
  return a + b;
}
console.log(add(2, 3));  // Output: 5
```
### **Optional & Default Parameters**
```ts
function greet(name: string = "User", age?: number): string {
  return `Hello, ${name}. Age: ${age ?? "Unknown"}`;
}
console.log(greet("Sri", 22)); // Hello, Sri. Age: 22
console.log(greet());          // Hello, User. Age: Unknown
```

---

## 🏗 **4. Arrays & Tuples**
```ts
let numbers: number[] = [1, 2, 3];
let names: Array<string> = ["Alice", "Bob"];
```

### **Tuple (Fixed Array)**
```ts
let user: [string, number] = ["Sri", 22];
```

---

## 🎭 **5. Objects & Interfaces**
```ts
interface User {
  name: string;
  age: number;
  isAdmin?: boolean;
}
const user: User = { name: "Sri", age: 22 };
```

### **Readonly & Optional Properties**
```ts
interface Car {
  readonly model: string;
  year?: number;
}
let car: Car = { model: "Tesla" };
```

---

## 🔁 **6. Enums**
```ts
enum Role { User, Admin, SuperAdmin }
let myRole: Role = Role.Admin;
console.log(myRole); // Output: 1
```

---

## 🔄 **7. Type Aliases & Unions**
```ts
type ID = string | number;
let userId: ID = 123;
userId = "ABC123";
```

---

## 🔥 **8. Classes in TypeScript**
```ts
class Person {
  constructor(public name: string, private age: number) {}
  getAge() {
    return this.age;
  }
}
const p = new Person("Sri", 22);
console.log(p.getAge());
```

### **Inheritance**
```ts
class Employee extends Person {
  constructor(name: string, age: number, public role: string) {
    super(name, age);
  }
}
const e = new Employee("Sri", 22, "Developer");
console.log(e.role);  // Developer
```

---

## 🔌 **9. Generics**
```ts
function identity<T>(value: T): T {
  return value;
}
console.log(identity<string>("Hello")); // Hello
console.log(identity<number>(100));     // 100
```

---

## 🎭 **10. TypeScript with Node.js**
Install dependencies:
```sh
npm init -y
npm install typescript ts-node @types/node
```

Run TypeScript files directly:
```sh
ts-node index.ts
```

---

## 🚀 **11. TypeScript with React**
Install TypeScript in React:
```sh
npx create-react-app my-app --template typescript
```
Example component:
```tsx
import React from "react";

interface Props {
  name: string;
}

const Greeting: React.FC<Props> = ({ name }) => {
  return <h1>Hello, {name}!</h1>;
};

export default Greeting;
```

---

## 🎯 **12. TypeScript Interview Questions**
### **Basic**
- What is TypeScript?
- How is TypeScript different from JavaScript?
- What are interfaces in TypeScript?
- Explain the use of `readonly` in TypeScript.
- What is `tsconfig.json`?

### **Advanced**
- Explain **Generics** in TypeScript.
- How do you define **tuples** in TypeScript?
- How does TypeScript handle **null** and **undefined**?
- What is the difference between **Type Aliases** and **Interfaces**?
- What is the `unknown` type in TypeScript?

---

## 🎉 **13. Conclusion**
TypeScript is a **powerful** language that improves **JavaScript** by adding **type safety, interfaces, and better tooling support**. It is widely used in **React, Angular, and Node.js**.

🚀 **Start using TypeScript to write better, scalable, and error-free applications!**