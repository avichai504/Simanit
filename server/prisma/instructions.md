# **Prisma and PostgreSQL Setup Guide**

This guide will walk you through setting up PostgreSQL with Prisma for the first time. It includes instructions on creating a PostgreSQL database and configuring Prisma to interact with it.

---

## **Step 1: Install and Set Up PostgreSQL**

If you haven’t installed PostgreSQL yet, follow these steps:

1. **Download PostgreSQL**:

   - Visit [PostgreSQL’s official website](https://www.postgresql.org/download/) and download the installer for your operating system.
2. **Install PostgreSQL**:

   - Run the installer and follow the prompts. Make note of the PostgreSQL username and password you create during installation.
   - During installation, you’ll be prompted to install **pgAdmin**, a graphical tool for managing PostgreSQL databases. This tool can be helpful for beginners.
3. **Open pgAdmin or connect via Command Line**:

   - **pgAdmin**: Open pgAdmin and connect to your PostgreSQL server using the username and password you set.
   - **Command Line**: Open your terminal or command prompt and connect by running:
     ``` psql -U your_username ```
   - Replace `your_username` with the PostgreSQL username you created.

## **Step 2: Create a New Database in PostgreSQL**

1. **Using pgAdmin**:

   - In pgAdmin, right-click on **Databases** and select **Create > Database**.
   - Enter a name for your database (e.g., `scheduling_app`) and click **Save**.
2. **Using Command Line**:

   - If you’re connected to PostgreSQL via the command line, run:
     ``` CREATE DATABASE scheduling_app; ```
   - Replace `scheduling_app` with your preferred database name.

Now, your PostgreSQL database is ready for use!

---

## **Step 3: Set Up Prisma in Your Project**

Navigate to your backend project directory:
``` cd Simanit/server ```

Initialize Prisma:
``` pnpm prisma init ```

This will create a `prisma/` folder containing `schema.prisma` and a `.env` file for environment variables.

---

## **Step 4: Configure the Database URL**

1. Open the `.env` file in the root of your project.
2. Set the `DATABASE_URL` variable to connect to your PostgreSQL database. Use the following format:
   ``` DATABASE_URL="postgresql://USER:PASSWORD@localhost:5432/scheduling_app" ```

   Replace:

   - `USER` with your PostgreSQL username.
   - `PASSWORD` with your PostgreSQL password.
   - `scheduling_app` with the name of the database you created.

---

## **Step 5: Configure Prisma Schema for PostgreSQL**

Open `prisma/schema.prisma` and ensure the datasource provider is set to PostgreSQL:

```
datasource db {
  provider = "postgresql"
  url      = env("DATABASE_URL")
}

generator client {
  provider = "prisma-client-js"
}
```

---

## **Step 6: Generate Prisma Client**

To generate the Prisma Client, which will let you query your database, run:

``` pnpm prisma generate ```

---

## **Step 7: Define Your Models (Optional)**

If your database is empty, you can define models directly in `schema.prisma`. Here’s an example model for a `User`:

``` model User {   id        Int      @id @default(autoincrement())   email     String   @unique   name      String?   createdAt DateTime @default(now()) } ```

After defining models, apply the changes to your database:

``` pnpm prisma migrate dev --name init ```

---

## **Step 8: Pull Existing Database Schema (Optional)**

If you already have tables in your PostgreSQL database and want Prisma to use them, run:

``` pnpm prisma db pull ```

This will introspect your existing database and update `schema.prisma` with the current structure.

---

## **Summary of Commands**

1. **Initialize Prisma**:
   ``` pnpm prisma init ```
2. **Set the Database URL**:
   ``` DATABASE_URL="postgresql://USER:PASSWORD@localhost:5432/scheduling_app" ```
3. **Generate Prisma Client**:
   ``` pnpm prisma generate ```
4. **Run Migrations** (if you added models to `schema.prisma`):
   ``` pnpm prisma migrate dev --name init ```

---

PS C:\Simanit\server> pnpm prisma init

✔ Your Prisma schema was created at prisma/schema.prisma
  You can now open it in your favorite editor.

Next steps:

1. Set the DATABASE_URL in the .env file to point to your existing database. If your database has no tables yet, read https://pris.ly/d/getting-started
2. Set the provider of the datasource block in schema.prisma to match your database: postgresql, mysql, sqlite, sqlserver, mongod5. Tip: Explore how you can extend the ORM with scalable connection pooling, global caching, and real-time database events. Read: https://pris.ly/cli/beyond-orm

More information in our documentation:
https://pris.ly/d/getting-started
