# 📝 Blog Application

A full-stack blog platform where users can register, write, edit, and publish blog posts, comment, like, and manage their profiles. Built with Node.js, Express, MongoDB, and optional React frontend.

---

## 🔗 Features

### ✅ Authentication & User Management

- Register / Login / Logout
- JWT-based session management
- Role-based access control (admin, user)
- Password reset via email

### ✍️ Blog Features

- Create, edit, delete blog posts
- Drafts & Published states
- Markdown/HTML support
- Tag-based filtering and search
- Comments with moderation
- Likes, views, and featured blogs

### 👤 User Profile

- View public profile & posts
- Update avatar, bio, and links
- Follow/unfollow authors

### 📈 Admin Features

- View all users/blogs
- Ban/spam users
- Approve or delete comments
- Analytics on blog views and likes

---

## 🛠️ Tech Stack

| Layer          | Technology                         |
| -------------- | ---------------------------------- |
| Backend        | Node.js, Express.js                |
| Database       | MongoDB, Mongoose                  |
| Authentication | JWT, bcrypt, cookie-parser         |
| Email          | Nodemailer                         |
| File Uploads   | Cloudinary or local multer storage |
| Frontend (opt) | React, Redux Toolkit, TailwindCSS  |
| Dev Tools      | ESLint, Prettier, Husky, Dotenv    |
| Testing        | Jest, Supertest                    |

---

## 📂 Project Structure (Backend)

blog-backend/
├── config/
│ ├── db.js # MongoDB connection logic
│ └── cloudinary.js # Cloudinary config (if using image upload)
│
├── controllers/
│ ├── auth.controller.js # Register, login, logout, password reset
│ ├── user.controller.js # Profile, update, avatar, follow/unfollow
│ ├── blog.controller.js # CRUD for blog posts
│ ├── comment.controller.js # Add, delete, get comments
│ └── admin.controller.js # Admin functions (e.g., user/blog management)
│
├── middlewares/
│ ├── auth.middleware.js # Auth check, role check, JWT validation
│ ├── error.middleware.js # Centralized error handling
│ ├── upload.middleware.js # Multer or Cloudinary upload logic
│ └── validate.middleware.js # Input validation logic (e.g. Joi or express-validator)
│
├── models/
│ ├── User.js # User schema with roles, avatar, bio, etc.
│ ├── Blog.js # Blog schema with title, content, tags, status
│ ├── Comment.js # Comment schema (linked to Blog and User)
│ └── Token.js # Optional: for refresh tokens, password reset, etc.
│
├── routes/
│ ├── auth.routes.js # /api/auth/_
│ ├── user.routes.js # /api/users/_
│ ├── blog.routes.js # /api/blogs/_
│ ├── comment.routes.js # /api/comments/_
│ └── admin.routes.js # /api/admin/\*
│
├── utils/
│ ├── generateToken.js # Generate JWTs
│ ├── sendEmail.js # Nodemailer config and email sending logic
│ └── formatResponse.js # Common response formatter (optional)
│
├── validators/
│ ├── auth.validator.js # Joi/express-validator for auth inputs
│ ├── user.validator.js
│ ├── blog.validator.js
│ └── comment.validator.js
│
├── docs/
│ └── blog-api.postman_collection.json # Postman collection
│
├── .env # Environment variables
├── .gitignore
├── package.json
├── server.js # Entry point (Express app + middlewares)
└── README.md
