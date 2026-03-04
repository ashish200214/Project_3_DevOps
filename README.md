# Project_3_DevOps# Node.js + AWS Secrets Manager + MySQL Demo

## Overview

This project shows how to connect a Node.js backend to a MySQL database **without hardcoding credentials** in the code.
Instead, the database username and password are stored securely in **AWS Secrets Manager** and fetched by the application at runtime.

The backend exposes a simple API endpoint to verify that the server can successfully connect to the database.

---

## Architecture

React (Vite)
↓
Node.js (Express)
↓
AWS Secrets Manager
↓
MySQL Database

---

## Why Secret Rotation Matters

Secret rotation means **changing sensitive credentials regularly**, such as database passwords.

This helps improve security because even if a credential is exposed, it becomes useless after rotation.
With AWS Secrets Manager, passwords can be rotated **without changing the application code**, since the application always fetches the latest value from the secret.

---

## Security Improvements

This approach improves security in several ways:

* **No hardcoded credentials** – database passwords are not stored in the code.
* **Secure storage** – credentials are encrypted and stored in AWS Secrets Manager.
* **IAM role access** – the application uses an IAM role instead of storing AWS access keys.
* **Centralized management** – secrets can be updated or rotated without modifying the application.

The IAM role only needs minimal permission:

```
secretsmanager:GetSecretValue
```

---

## API Endpoint

Check backend and database connection:

```
GET /api/status
```

Example response:

```
{
  "status": "SUCCESS",
  "message": "Connected using AWS Secrets Manager"
}
```

---

## Technologies Used

* Node.js
* Express
* MySQL
* AWS Secrets Manager
* AWS IAM Roles
* React (Vite)

---

## Key Idea

Using AWS Secrets Manager helps keep database credentials secure and prevents sensitive information from being exposed in the codebase.
