# 🚀 **Next.js - The Ultimate Guide (From Basics to Advanced)**  

Next.js is a **React framework** that enables **server-side rendering (SSR), static site generation (SSG), and API routes**, making it powerful for full-stack applications.

---

## 📌 **1. Installation & Setup**
```sh
# Create a Next.js project
npx create-next-app my-next-app
cd my-next-app
npm run dev  # Start development server
```

Project structure:
```
my-next-app/
│── pages/          # Each file is a route
│── components/     # Reusable UI components
│── public/         # Static assets
│── styles/        # CSS files
│── next.config.js  # Configuration file
│── package.json
```

---

## 🌍 **2. Pages & Routing**
Next.js follows **file-based routing** inside the `pages/` directory.

- **Basic Page (pages/index.js)**
```jsx
export default function Home() {
  return <h1>Welcome to Next.js!</h1>;
}
```
- **Dynamic Route (`pages/product/[id].js`)**
```jsx
import { useRouter } from 'next/router';

export default function Product() {
  const router = useRouter();
  return <h1>Product ID: {router.query.id}</h1>;
}
```

- **API Routes (`pages/api/hello.js`)**
```jsx
export default function handler(req, res) {
  res.status(200).json({ message: "Hello API!" });
}
```

---

## 🚀 **3. Pre-rendering (SSR & SSG)**
### **Static Site Generation (SSG)**
```jsx
export async function getStaticProps() {
  return {
    props: { message: "Hello, SSG!" },
  };
}

export default function Page({ message }) {
  return <h1>{message}</h1>;
}
```

### **Server-Side Rendering (SSR)**
```jsx
export async function getServerSideProps() {
  return {
    props: { message: "Hello, SSR!" },
  };
}

export default function Page({ message }) {
  return <h1>{message}</h1>;
}
```

---

## ⚡ **4. API Calls (Fetching Data)**
### **Client-Side Fetching**
```jsx
import { useEffect, useState } from "react";

export default function Page() {
  const [data, setData] = useState(null);

  useEffect(() => {
    fetch("/api/hello")
      .then((res) => res.json())
      .then((data) => setData(data.message));
  }, []);

  return <h1>{data}</h1>;
}
```

### **Fetching Data at Build Time (SSG)**
```jsx
export async function getStaticProps() {
  const res = await fetch("https://jsonplaceholder.typicode.com/posts/1");
  const data = await res.json();

  return { props: { data } };
}

export default function Page({ data }) {
  return <h1>{data.title}</h1>;
}
```

---

## 📂 **5. Layouts & Custom App**
Create a **global layout** in `components/Layout.js`:
```jsx
export default function Layout({ children }) {
  return (
    <div>
      <nav>Navbar</nav>
      <main>{children}</main>
    </div>
  );
}
```
Apply it in `_app.js`:
```jsx
import Layout from "../components/Layout";
export default function MyApp({ Component, pageProps }) {
  return (
    <Layout>
      <Component {...pageProps} />
    </Layout>
  );
}
```

---

## 🌍 **6. API Routes (Backend in Next.js)**
Create an API in `pages/api/user.js`:
```jsx
export default function handler(req, res) {
  if (req.method === "GET") {
    res.status(200).json({ name: "Sri" });
  }
}
```

---

## 🎨 **7. Styling in Next.js**
- **Global Styles (styles/globals.css)**
```css
body {
  background-color: #f8f8f8;
}
```
Import in `_app.js`:
```jsx
import "../styles/globals.css";
```

- **CSS Modules**
```css
/* styles/Home.module.css */
.title {
  color: blue;
}
```
```jsx
import styles from "../styles/Home.module.css";
export default function Home() {
  return <h1 className={styles.title}>Styled Text</h1>;
}
```

---

## 🔑 **8. Authentication (NextAuth.js)**
```sh
npm install next-auth
```
- Setup API route in `pages/api/auth/[...nextauth].js`:
```jsx
import NextAuth from "next-auth";
import Providers from "next-auth/providers";

export default NextAuth({
  providers: [
    Providers.GitHub({
      clientId: process.env.GITHUB_CLIENT_ID,
      clientSecret: process.env.GITHUB_CLIENT_SECRET,
    }),
  ],
});
```
- Use in a page:
```jsx
import { signIn, signOut, useSession } from "next-auth/react";

export default function Page() {
  const { data: session } = useSession();

  return (
    <div>
      {session ? (
        <>
          <h1>Welcome, {session.user.name}</h1>
          <button onClick={() => signOut()}>Logout</button>
        </>
      ) : (
        <button onClick={() => signIn("github")}>Login with GitHub</button>
      )}
    </div>
  );
}
```

---

## 🚀 **9. Deploying Next.js**
### **Vercel**
```sh
npm run build
npm install -g vercel
vercel
```

### **Self-Hosting**
```sh
npm run build
npm start
```

---

## 🔥 **10. Interview Questions**
### **Basic**
- What is Next.js?
- How is it different from React?
- Explain SSR vs SSG vs CSR.
- What is `getStaticProps` and `getServerSideProps`?
- How does file-based routing work?

### **Advanced**
- How do you optimize performance in Next.js?
- What is ISR (Incremental Static Regeneration)?
- How do API routes work in Next.js?
- How to implement authentication in Next.js?

---

🚀 **Master Next.js & Build Production-Ready Apps!**