# 🔐 Authentication Guide – Blog Application

This document explains how user authentication and authorization are implemented in the Blog Application using **JWT (JSON Web Tokens)**, **bcrypt**, and standard REST practices.

---

## 🧾 Overview

- User credentials are securely stored and authenticated using hashed passwords (`bcrypt`).
- JWT is used for session-less authentication.
- Access and refresh tokens are issued on login.
- Middleware protects private routes.
- Role-based access control is available (`user`, `admin`).

---

## 🔑 Token Strategy

- **Access Token**:
  - Short-lived (e.g., 15 minutes)
  - Sent in `Authorization: Bearer <token>` header
- **Refresh Token**:
  - Long-lived (e.g., 7 days)
  - Stored in an HTTP-only cookie or local storage
  - Used to issue a new access token

---

## 🔄 Authentication Flow

1. **Register**
2. **Login** → Get access + refresh tokens
3. **Use access token** to access protected routes
4. **Refresh access token** using refresh token if expired
5. **Logout** → Invalidate session or clear token

---

## ✍️ Register

**Endpoint**: `POST /api/auth/register`

```json
{
  "name": "Jane Doe",
  "email": "jane@example.com",
  "password": "SecureP@ss123"
}
```
