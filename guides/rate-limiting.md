# 🧱 Rate Limiting – Blog Application

This document explains the implementation of API rate limiting to protect the Blog Application from abuse, brute-force attacks, and excessive resource usage.

---

## 🎯 Purpose

Rate limiting restricts the number of requests a client (typically identified by IP) can make to the API within a certain time window.

### ✅ Benefits

- Prevents brute-force login attempts
- Mitigates denial-of-service (DoS) attacks
- Controls abuse of public APIs
- Preserves server performance and bandwidth

---

## 🧰 Implementation Tool

We use [`express-rate-limit`](https://www.npmjs.com/package/express-rate-limit), a middleware for Express.js.

### 📦 Installation

```bash
npm install express-rate-limit
```
