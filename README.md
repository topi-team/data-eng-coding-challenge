# Data Engineering Coding Challenge

Welcome! 🎉

We're excited to see how you approach this **Data Engineering Coding Challenge**. In our production environment, we use **BigQuery**, but for this challenge, you'll work locally with **PostgreSQL** to ensure a fully self-contained setup.

This document will guide you through setting up your environment so you can focus on solving the challenge. Let's get started! 🚀

---

## 🛠 Prerequisites

Before diving in, make sure you have the following installed:

### 1️⃣ **Docker Compose**
You'll need **Docker Compose** to run PostgreSQL locally.  
Follow the official installation guide: [Docker Compose Installation](https://docs.docker.com/compose/install/)

### 2️⃣ **Python Virtual Environment**
We use **Pipenv** to manage dependencies.

1. Install Pipenv:
    - macOS (using Homebrew):
      ```shell
      brew install pipenv
      ```
    - Other platforms: [Follow this guide](https://packaging.python.org/en/latest/tutorials/managing-dependencies/#installing-pipenv)
2. Install dependencies:
   ```shell
   pipenv sync
   ```
3. Activate the virtual environment:
   ```shell
   pipenv shell
   ```

---

## 🚀 Setting Up Your Environment

### 1️⃣ **Start PostgreSQL**
Run the following command to spin up a local PostgreSQL instance:

```shell
docker compose up
```

---

## 🖥️ Accessing the Database

We’ve set up **Adminer** so you can explore the database with a user-friendly UI.

1. Open **Adminer** in your browser:
   ```
   http://localhost:8080/?pgsql=db&username=coding_challenge&db=coding_challenge&ns=dbt_dev
   ```
2. Switch to the **coding_challenge** database and the **dbt_dev** schema.

---

## 🔍 Validating Your Setup

Before you start coding, ensure everything is working correctly with these checks:

### ✅ 1. Check if PostgreSQL is Running
Run:
```shell
docker ps
```
If PostgreSQL is running, you should see a container listed.

If it's not running, start it:
```shell
docker compose up
```

### ✅ 2. Connect to the Database
To manually test the database connection, run:
```shell
docker exec -it <container_id> psql -U coding_challenge -d coding_challenge
```
Replace `<container_id>` with the actual container ID from `docker ps`.

Alternatively, open **Adminer** and check if the `coding_challenge` database is accessible.

### ✅ 3. Run dbt Debug
Verify that **dbt** is installed and correctly configured:
```shell
dbt debug
```
If everything is set up correctly, you should see a success message.

---

## ⚠️ Troubleshooting Common Errors

If you run into any issues, here are some common problems and solutions:

### ❌ PostgreSQL Container Won't Start
**Error:**
```
ERROR: database system is in recovery mode
```
✅ **Solution:**  
Try restarting the container:
```shell
docker compose down
docker compose up --force-recreate
```

### ❌ Cannot Connect to Database
**Error:**
```
psql: could not connect to server: Connection refused
```
✅ **Solution:**  
Ensure the database container is running:
```shell
docker ps
```
If it's not listed, start it:
```shell
docker compose up -d
```

### ❌ dbt Debug Fails
**Error:**
```
Database connection failed
```
✅ **Solution:**  
Check your `profiles.yml` file for incorrect credentials. Ensure that dbt is using the correct database, schema, and user.

### ❌ Pipenv or venv Activation Issues
**Error:**
```
Command 'pipenv' not found
```
✅ **Solution:**  
Ensure **Pipenv** is installed (`pip install pipenv`) and try reactivating:
```shell
pipenv shell
```
For **venv**, re-run:
```shell
source env/bin/activate  # macOS/Linux  
env\Scripts\activate     # Windows  
```

---

## 📤 How to Submit Your Solution

Once you’ve completed the challenge, follow these steps to submit your work:

### 1️⃣ **Ensure Your Code is Clean and Documented**
- Format your code properly.
- Add comments where necessary to explain key logic.
- If applicable, include a `README.md` inside your submission with additional details on your approach.

### 2️⃣ **Package Your Work**
- If submitting via **ZIP file**:
    1. Remove unnecessary files (e.g., `__pycache__`, `.venv`).
    2. Create a zip archive of your project:
       ```shell
       zip -r data-eng-challenge.zip .
       ```
    3. Send the zip file per email.

### 3️⃣ **Provide Additional Context (Optional but Recommended)**
If you made specific design choices, encountered challenges, or have insights into possible optimizations, include them in a `NOTES.md` file or a comment in your submission email/message.

---

## 🎯 Final Steps

Once you’ve submitted your work, let us know, and we’ll review it! 🎯🚀

Good luck, and happy coding! 😊
