# 🛠️ Error Handling – Blog Application

This document describes how errors are managed across the backend, ensuring consistent structure, clarity, and maintainability.

---

## 📦 Goals of Error Handling

- Provide meaningful error messages to clients
- Avoid leaking sensitive internal details
- Log detailed errors for debugging
- Maintain consistent response format
- Support HTTP status codes correctly

---

## 📐 Standard Error Format

All API error responses follow this format:

```json
{
  "success": false,
  "statusCode": 400,
  "error": "ValidationError",
  "message": "Email is already in use."
}
```
