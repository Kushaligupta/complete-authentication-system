# 🔐 Complete Authentication System

A **production-ready authentication system** built with **Node.js, Express.js, MongoDB, JWT, Refresh Tokens, OTP Verification, and Session Management**.

This project demonstrates how modern backend systems securely manage **user authentication**, including **Access Tokens**, **Refresh Tokens**, **Token Rotation**, **OTP-Based Authentication**, **Session Management**, and **Logout from All Devices**.

---

## 🚀 Features

- 🔐 User Registration
- 🔓 User Login
- 🪪 JWT Authentication
- ♻️ Access Token & Refresh Token Flow
- 🔄 Refresh Token Rotation
- 📱 Session Management
- 🚪 Logout from Current Device
- 🌍 Logout from All Devices
- 📩 OTP-Based Email Verification
- 🛡 Protected Routes
- 🍪 Cookie-Based Token Handling
- 📄 Request Logging with Morgan
- 🧩 Clean MVC-Based Backend Architecture

---

## 🛠 Tech Stack

### Backend
- **Node.js**
- **Express.js**

### Database
- **MongoDB**
- **Mongoose**

### Authentication & Security
- **JWT (JSON Web Token)**
- **Access Token**
- **Refresh Token**
- **Token Rotation**
- **Session Management**
- **OTP Verification**

### Utilities / Middleware
- **Morgan**
- **Cookie Parser**
- **dotenv**
- **Nodemailer**

---

## 📂 Project Structure

```bash
complete-authentication-system/
│── node_modules/
│── src/
│   │── config/
│   │   │── config.js
│   │   │── database.js
│   │
│   │── controllers/
│   │   │── auth.controller.js
│   │
│   │── models/
│   │   │── otp.model.js
│   │   │── sessions.model.js
│   │   │── user.model.js
│   │
│   │── routes/
│   │   │── auth.routes.js
│   │
│   │── services/
│   │   │── email.service.js
│   │
│   │── utils/
│   │   │── utils.js
│   │
│   │── app.js
│
│── .env
│── package.json
│── package-lock.json
│── server.js
│── README.md





