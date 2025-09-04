# Prisma Test Project

This is a simple project to connect to a PostgreSQL database (e.g., hosted on Render) using Prisma and explore the data with **Prisma Studio**.

---

## 🔹 Setup

1. **Clone the repo** (if needed) or create a new folder:

```bash
mkdir prisma-test
cd prisma-test
npm init -y
```

2. **Install Prisma:**

```bash
npm install prisma --save-dev
npx prisma init
```

---

## 🔹 Configure `.env`

Create a `.env` file in the root folder (or update the existing one).
Add your database connection string from Render:

```env
DATABASE_URL="postgresql://<USERNAME>:<PASSWORD>@<HOST>.render.com:5432/<DBNAME>"
```

**Example:**

```env
DATABASE_URL="postgresql://postgres:mysecretpassword@dpg-d2ochi0dl3ps73903adg-a.render.com:5432/prisma_bd_dj5b"
```

> Make sure to replace `<USERNAME>`, `<PASSWORD>`, `<HOST>`, and `<DBNAME>` with your actual credentials from Render.

---

## 🔹 Update Prisma Schema

Open `prisma/schema.prisma` and make sure it looks like this:

```prisma
datasource db {
  provider = "postgresql"
  url      = env("DATABASE_URL")
}

generator client {
  provider = "prisma-client-js"
}
```

---

## 🔹 Introspect the database

This command will read your existing database tables and update `schema.prisma`:

```bash
npx prisma db pull
```

---

## 🔹 Explore data with Prisma Studio

To view and interact with your data in a browser:

```bash
npx prisma studio
```

---

## 🔹 Notes

* If `db pull` fails, check your connection string and make sure the database allows external connections.
* The `host` in the connection string **must include `.render.com`**.
* Ensure the database is running and accessible from your machine.
