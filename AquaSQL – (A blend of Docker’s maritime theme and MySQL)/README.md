# 🐳 Setting Up MySQL in a Docker Container with Auto-Initialization 🚀

---

## 🔗 Prerequisites

✔️ Install **Docker** on your system.
✔️ Ensure **Docker** is running.
✔️ Create an SQL initialization script (e.g., `aryan_demo.sql`) with database and table definitions.

---

## 📂 Project Directory Structure

Organize your project directory as follows:

```
project-directory/
│── Dockerfile
│── aryan_demo.sql
```

This structure ensures an efficient setup with all necessary files in one place. 🗂️

---

## ⚙️ Step 1: Create a Dockerfile

Create a `Dockerfile` inside your project directory:

```dockerfile
# 🏗 Use the official MySQL image
FROM mysql:latest

# 📂 Copy initialization script to the container
COPY aryan_demo.sql /docker-entrypoint-initdb.d/

# 🔥 Expose MySQL port
EXPOSE 3306
```

This setup ensures that MySQL initializes with the predefined schema and data. 📊

---

## 📜 Step 2: Define the SQL Initialization Script

Create a file named **`aryan_demo.sql`** in the same directory and add:

```sql
CREATE DATABASE aryan;
USE aryan;

CREATE TABLE students (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    age INT
);

INSERT INTO students (name, age) VALUES ('Alice', 22), ('Bob', 24);
```

This script ensures MySQL initializes with a database and sample data. 🏗

---

## 🛠 Step 3: Build the Docker Image

Run the following command to build your custom MySQL image:

```sh
docker build -t mysql-custom .
```

💡 This command creates a Docker image named **`mysql-custom`**. 🏗

---

## 🚀 Step 4: Run the MySQL Container

Launch a MySQL container with the custom image:

```sh
docker run --name mysql-container -e MYSQL_ROOT_PASSWORD=root -d mysql-custom
```

🔍 **Explanation:**

-   🏷 **`--name mysql-container`** → Assigns a name to the container.
-   🔐 **`-e MYSQL_ROOT_PASSWORD=root`** → Sets the root password.
-   🏃 **`-d`** → Runs the container in detached mode.
-   🛠 **`mysql-custom`** → Uses the custom-built MySQL image.

---

## 🔍 Step 5: Access the Running Container

To open a shell inside the running container:

```sh
docker exec -it mysql-container bash
```

💡 This command provides interactive access to the MySQL container. 🖥️

---

## 💻 Step 6: Connect to MySQL

Once inside the container, access the MySQL CLI:

```sh
mysql -u root -p
```

🔑 **Enter the password** (`root`) when prompted.

---

## 🏗 Step 7: Verify Database and Tables

Check available databases:

```sql
SHOW DATABASES;
```

Switch to the **`aryan`** database:

```sql
USE aryan;
```

Query the **students** table:

```sql
SELECT * FROM students;
```

📊 This will display the pre-inserted sample data. 🎯

---

## 🎉 Conclusion

✅ You have successfully **set up MySQL in a Docker container** with an auto-initialization script.
✅ Every time the container starts, the database and schema will be preloaded.
✅ Perfect for development and testing environments! 🚀

**Happy Coding!** 🎨💡
