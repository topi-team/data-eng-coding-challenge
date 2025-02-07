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
You can use **Pipenv** or **venv** to manage dependencies. Pick your preferred method below:

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

---

## 🚀 Setting Up Your Environment

### 1️⃣ **Start PostgreSQL**
Run the following command to spin up a local PostgreSQL instance:

```shell
docker compose up
```

### 2️⃣ **Install dbt & PostgreSQL Adapter**
Once your environment is set up, install **dbt-core** and the **PostgreSQL adapter**:

```shell
pipenv sync
```

Then, activate the virtual environment:

```shell
pipenv shell
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

## ✅ Next Steps

Now that your environment is ready, you're all set to tackle the challenge! 💪

If you run into any issues, feel free to troubleshoot using the linked documentation above.

Good luck, and have fun! 🎯🚀

---
