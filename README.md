# ARS-Kart (E-commerce Platform)

## Overview



ARS E-commerce is a full-stack web application for buying and selling electronics and accessories. It features a modern React frontend, a robust Node.js/Express backend, and a PostgreSQL (or MySQL) database. The platform supports user authentication, product browsing, cart and wishlist management, order processing, and an admin dashboard for managing products, users, orders, and categories.

---

## Table of Contents
- [Features](#features)
- [Project Structure](#project-structure.
- [Frontend](#frontend)
- [Backend](#backend.
- [Database Schema](#database-schema)
- [Scripts](#scripts)
- [Deployment](#deployment)
- [Setup & Installation](#setup--installation)
- [Environment Variables](#environment-variables)
- [License](#license)
- 
---

## Features
- User registration, login, and profile management
- Product catalog with categories and subcategories
- Search, filter, and browse products
- Shopping cart and wishlist functionality
- Secure checkout and order placement
- Payment options (card, cash on delivery)
- Order history and status tracking
- Admin dashboard for managing products, users, orders, and categories
- Responsive, modern UI

---

## Project Structure
```
/ (root)
├── backend/         # Express.js API, models, routes, config
├── frontend/        # React app (src, public, build)
├── scripts/         # Utility scripts (e.g., createAdmin.js)
├── database.sql     # SQL schema for database setup
├── render.yaml      # Render.com deployment config
├── railway.json     # Railway deployment config
├── package.json     # Root scripts and dependencies
└── ...
```

---

## Frontend
- **Framework:** React 19, React Router v7
- **Styling:** CSS Modules, MUI, FontAwesome, TailwindCSS
- **Key Features:**
  - Home, Products, Category, Subcategory, Cart, Wishlist, Checkout, Profile pages
  - Admin panel for product, user, order, and category management
  - Context providers for cart and wishlist
  - Responsive design
- **Scripts:**
  - `npm start` — Start development server
  - `npm run build` — Build for production
- **Location:** `frontend/`

## Backend
- **Framework:** Node.js, Express.js
- **Database:** PostgreSQL (default), supports MySQL
- **ORM:** Mongoose (for MongoDB, if used)
- **Key Features:**
  - RESTful API for products, users, cart, wishlist, orders, categories
  - JWT-based authentication and authorization
  - Admin and user roles
  - Email notifications (via Nodemailer)
- **Scripts:**
  - `npm start` — Start backend server
- **Location:** `backend/`

### Main API Endpoints
- `/api/auth` — User authentication (login, register)
- `/api/products` — Product catalog (CRUD)
- `/api/cart` — Cart management
- `/api/wishlist` — Wishlist management
- `/api/orders` — Order processing
- `/api/users` — User management
- `/api/admin` — Admin operations (users, products, categories, orders)

---

## Database Schema
- **Tables:**
  - `users` — User accounts (with admin flag)
  - `products` — Product catalog
  - `categories` — Product categories
  - `cart` — User shopping carts
  - `wishlist` — User wishlists
  - `orders` — Orders placed by users
  - `order_items` — Items in each order
  - `payments` — Payment records
  - `user_addresses` — User shipping addresses

See [`database.sql`](database.sql) and [`backend/models/init-db.sql`](backend/models/init-db.sql) for full schema.

---

## Scripts
- **scripts/createAdmin.js** — Creates an admin user in the database. Edit the script to set your admin credentials, then run:
  ```sh
  node scripts/createAdmin.js
  ```
- **backend/scripts/createAdmin.js** — Alternative script for backend DB admin creation.

---

## Deployment

### Render.com
- See [`render.yaml`](render.yaml) for service configuration.
- Two services: `backend` (Node.js) and `frontend` (static build)
- Set environment variables as shown in the config (e.g., `DATABASE_URL`, `REACT_APP_API_URL`)

### Railway
- See [`railway.json`](railway.json) for build and deploy commands.

---

## Setup & Installation

### Prerequisites
- Node.js (v18+ recommended)
- npm
- PostgreSQL or MySQL database

### 1. Clone the repository
```sh
git clone <repo-url>
cd arc_commerce-main
```

### 2. Install dependencies
```sh
npm run install-all
```

### 3. Configure environment variables
- Copy `.env.example` to `.env` in both `backend/` and `frontend/` (create if missing)
- Set database connection strings, JWT secrets, etc.

### 4. Set up the database
- Run the SQL in `database.sql` or `backend/models/init-db.sql` on your database server

### 5. Start the application
- **Development:**
  ```sh
  npm start
  # or run backend and frontend separately
  cd backend && npm start
  cd frontend && npm start
  ```
- **Production:**
  - Build frontend: `cd frontend && npm run build`
  - Deploy backend and serve frontend build

---

## Environment Variables
- `DATABASE_URL` — Database connection string
- `PORT` — Backend server port
- `REACT_APP_API_URL` — Frontend API base URL
- `NODE_ENV` — Environment (development/production)
- `JWT_SECRET` — JWT signing key (backend)

---

## License

This project is licensed under the MIT License. 
