# 🔐 Complete Authentication System

A secure, production-ready authentication REST API built with **Node.js**, **Express**, and **MongoDB**. Features JWT-based session management, OTP email verification, and full multi-device logout support.

---

## 🚀 Features

- User registration with email OTP verification
- Secure login with hashed passwords (SHA-256)
- Access token (15min) + Refresh token (7d) strategy
- HTTP-only cookie-based refresh tokens
- Session tracking with IP and User-Agent logging
- Logout from current device or all devices
- Gmail OAuth2 email delivery via Nodemailer

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Runtime | Node.js (ESM) |
| Framework | Express.js |
| Database | MongoDB + Mongoose |
| Auth | JSON Web Tokens (JWT) |
| Email | Nodemailer + Gmail OAuth2 |
| Logging | Morgan |

---

## 📁 Project Structure

```
├── app.js                   # Express app setup
├── config/
│   └── config.js            # Environment variable validation & export
├── controllers/
│   └── auth.controller.js   # Route handler logic
├── models/
│   ├── user.model.js        # User schema
│   ├── otp.model.js         # OTP schema
│   └── sessions.model.js    # Session schema
├── routes/
│   └── auth.routes.js       # Auth route definitions
├── services/
│   └── email.service.js     # Nodemailer email sending
└── utils/
    └── utils.js             # OTP generation & HTML template
```

---

## ⚙️ Environment Variables

Create a `.env` file in the root directory with the following keys:

```env
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret_key

GOOGLE_CLIENT_ID=your_google_oauth_client_id
GOOGLE_CLIENT_SECRET=your_google_oauth_client_secret
GOOGLE_REFRESH_TOKEN=your_google_oauth_refresh_token
GOOGLE_USER=your_gmail_address
```

> All variables are required. The app will throw an error on startup if any are missing.

---

## 📦 Installation

```bash
# Clone the repository
git clone https://github.com/Kushaligupta/complete-authentication-system.git
cd complete-authentication-system

# Install dependencies
npm install

# Set up environment variables
cp .env.example .env
# Fill in your values in .env

# Start the server
npm start
```

---

## 📡 API Reference

All routes are prefixed with `/api/auth`.

### Register
```
POST /api/auth/register
```
**Body:**
```json
{
  "username": "johndoe",
  "email": "john@example.com",
  "password": "yourpassword"
}
```
Creates a new user and sends a 6-digit OTP to the provided email for verification.

---

### Verify Email
```
GET /api/auth/verify-email
```
**Body:**
```json
{
  "email": "john@example.com",
  "otp": "123456"
}
```
Verifies the user's email using the OTP sent during registration.

---

### Login
```
POST /api/auth/login
```
**Body:**
```json
{
  "email": "john@example.com",
  "password": "yourpassword"
}
```
Returns an `accessToken` in the response body and sets a `refreshToken` as an HTTP-only cookie.

---

### Get Current User
```
GET /api/auth/get-me
```
**Headers:** `Authorization: Bearer <accessToken>`

Returns the authenticated user's profile.

---

### Refresh Access Token
```
GET /api/auth/refresh-token
```
Uses the `refreshToken` cookie to issue a new access token and rotate the refresh token.

---

### Logout
```
GET /api/auth/logout
```
Revokes the current session and clears the refresh token cookie.

---

### Logout All Devices
```
GET /api/auth/logout-all
```
Revokes all active sessions for the user across all devices.

---

## 🔒 Security Notes

- Passwords are hashed with SHA-256 before storage.
- Refresh tokens are stored as SHA-256 hashes in the database — the raw token is never persisted.
- Refresh token cookies are `httpOnly`, `secure`, and `sameSite: strict`.
- Each session records the client IP and User-Agent for audit purposes.


