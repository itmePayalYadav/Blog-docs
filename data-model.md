# 📊 Data Model – Blog Application

This document describes the Mongoose schema structure, fields, types, and relationships between entities in the Blog Application.

---

## 👤 User Model

### Collection: `users`

| Field     | Type       | Description                          |
| --------- | ---------- | ------------------------------------ |
| \_id      | ObjectId   | Auto-generated MongoDB ObjectId      |
| name      | String     | Full name of the user                |
| email     | String     | Unique email address                 |
| password  | String     | Hashed password                      |
| avatar    | String     | Profile image URL (Cloudinary/local) |
| bio       | String     | Short user bio or about section      |
| role      | String     | 'user' or 'admin'                    |
| followers | [ObjectId] | List of users following this user    |
| following | [ObjectId] | List of users this user follows      |
| createdAt | Date       | Timestamp of user creation           |
| updatedAt | Date       | Timestamp of last update             |

### 🔗 Relationships

- A user **can create many blogs**
- A user **can like many blogs**
- A user **can comment on many blogs**
- A user **can follow and be followed by other users**

---

## 📝 Blog Model

### Collection: `blogs`

| Field      | Type       | Description                            |
| ---------- | ---------- | -------------------------------------- |
| \_id       | ObjectId   | Unique blog identifier                 |
| title      | String     | Title of the blog                      |
| content    | String     | Main body content of the blog          |
| coverImage | String     | Optional image URL                     |
| tags       | [String]   | List of tags or topics                 |
| author     | ObjectId   | Reference to `User` who wrote the blog |
| status     | String     | 'draft' or 'published'                 |
| likes      | [ObjectId] | References to users who liked the blog |
| views      | Number     | Total number of views                  |
| comments   | [ObjectId] | References to associated comments      |
| createdAt  | Date       | Creation timestamp                     |
| updatedAt  | Date       | Last update timestamp                  |

### 🔗 Relationships

- A blog **belongs to one user (author)**
- A blog **can have many comments**
- A blog **can be liked by many users**

---

## 💬 Comment Model

### Collection: `comments`

| Field     | Type     | Description                             |
| --------- | -------- | --------------------------------------- |
| \_id      | ObjectId | Unique comment identifier               |
| content   | String   | The text content of the comment         |
| blog      | ObjectId | Reference to the `Blog` being commented |
| user      | ObjectId | Reference to the `User` who commented   |
| createdAt | Date     | Timestamp of creation                   |

### 🔗 Relationships

- A comment **belongs to one blog**
- A comment **belongs to one user**

---

## 🛡️ Admin Notes

- Admin users (role: `admin`) have elevated permissions to:
  - Block/unblock users
  - Delete blogs or comments for moderation
  - Access all user/blog/comment data

---

## 🧩 Data Model Relationships (ER Diagram)

```text
User
 ├───< Blog (author)
 ├───< Comment (user)
 ├───< followers [User]
 ├───< following [User]
 └───< likedBlogs [Blog]

Blog
 ├───< Comment (blog)
 ├───< likes [User]
 └───< author (User)

Comment
 ├─── blog (Blog)
 └─── user (User)
```
