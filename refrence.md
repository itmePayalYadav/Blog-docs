# 📘 Blog Application – Reference Guide

This document outlines the key structures, API references, roles, and utilities used in the backend of the Blog Application.

---

## 🧩 Core Models & Relationships

### 🔹 User

```js
{
  _id: ObjectId,
  name: String,
  email: String,
  password: HashedString,
  avatar: String,
  bio: String,
  role: 'user' | 'admin',
  followers: [ObjectId],
  following: [ObjectId],
  createdAt: Date,
  updatedAt: Date
}
```

{
\_id: ObjectId,
title: String,
content: String,
coverImage: String,
tags: [String],
author: ObjectId (User),
status: 'draft' | 'published',
likes: [ObjectId], // users who liked
views: Number,
comments: [ObjectId],
createdAt: Date,
updatedAt: Date
}

{
\_id: ObjectId,
content: String,
blog: ObjectId (Blog),
user: ObjectId (User),
createdAt: Date
}
