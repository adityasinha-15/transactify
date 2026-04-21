# 🚀 Transactify — Transaction Processing Backend

Transactify is a backend system that simulates **real-world banking and financial transactions** using a **ledger-based architecture**.
It ensures **data integrity, consistency, and auditability** — just like modern fintech systems.

---

## 📌 Overview

Transactify is designed to handle **secure money transfers between accounts**.

Instead of storing balances directly, it records **every transaction as ledger entries (credit/debit)** and computes balances dynamically.

This approach ensures:

* No data corruption
* Full transaction history
* High reliability

---

## ✨ Key Features

### 🔐 Authentication System

* User Registration & Login
* JWT-based authentication
* Token blacklist for secure logout

---

### 💳 Account Management

* Create user accounts
* Fetch all accounts
* Get real-time balance

---

### 💸 Transaction Engine (Core)

* Transfer funds between accounts
* Atomic operations using MongoDB transactions
* Transaction lifecycle:

  * PENDING
  * COMPLETED
  * FAILED
  * REVERSED

---

### 📒 Ledger-Based Accounting (Core Concept)

* Immutable ledger entries
* Balance = Credits − Debits
* Full audit trail (bank-level logic)

---

### 🔁 Idempotency Handling

* Prevents duplicate transactions
* Ensures safe retry of requests

---

### 📧 Email Notifications

* Welcome emails on registration
* Transaction confirmation emails

---

## 🧠 Architecture

```id="arch1"
Client → Routes → Middleware → Controllers → Models → Database
```

---

## ⚙️ Tech Stack

* Backend: Node.js, Express.js
* Database: MongoDB (Mongoose)
* Authentication: JWT
* Security: bcrypt, cookie-parser
* Email: Nodemailer
* Config: dotenv

---

## 📁 Project Structure

```id="struct1"
src/
│
├── config/         # Database connection
├── controllers/    # Business logic
├── middleware/     # Authentication
├── models/         # Schemas
├── routes/         # API endpoints
├── services/       # Email services
└── app.js          # Express setup

server.js           # Entry point
```

---

## 🔄 Transaction Flow

1. Request validation
2. Authentication via middleware
3. Idempotency check
4. Account validation
5. Balance calculation via ledger
6. Start DB transaction
7. Create transaction (PENDING)
8. Debit sender
9. Credit receiver
10. Mark COMPLETED
11. Commit DB transaction
12. Send email

---

## 🔐 Security

* Password hashing (bcrypt)
* JWT authentication
* Token blacklist (logout security)
* Protected routes

---

## 📡 API Endpoints

### Auth

* POST `/api/auth/register`
* POST `/api/auth/login`
* POST `/api/auth/logout`

---

### Accounts

* POST `/api/accounts`
* GET `/api/accounts`
* GET `/api/accounts/balance/:accountId`

---

### Transactions

* POST `/api/transactions`
* POST `/api/transactions/system/initial-funds`

---

## 🧠 Core Concepts Implemented

* Ledger-based accounting
* Idempotent API design
* Atomic database transactions
* Middleware architecture
* Modular backend structure

---

## 🚀 Setup Instructions

### Clone repository

```bash id="c1"
git clone https://github.com/your-username/transactify.git
cd transactify
```

---

### Install dependencies

```bash id="c2"
npm install
```

---

### Create `.env`

```id="c3"
MONGO_URI=your_mongodb_uri
JWT_SECRET=your_secret

EMAIL_USER=your_email
CLIENT_ID=your_client_id
CLIENT_SECRET=your_client_secret
REFRESH_TOKEN=your_refresh_token
```

---

### Run server

```bash id="c4"
node server.js
```

---

## ⚠️ Improvements (Planned)

* Service layer architecture
* Global error handling
* Background job queue for emails
* Request validation (Joi/Zod)
* Logging system
* Rate limiting & security enhancements

---

## 👨‍💻 Author

Aditya Sinha

---
