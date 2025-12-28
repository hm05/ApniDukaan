# ApniDukaan - Full Stack E-Commerce Platform

A comprehensive MERN stack e-commerce application with complete product management, user authentication, order processing, and payment integration.

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Environment Variables](#environment-variables)
- [Usage](#usage)
- [API Routes](#api-routes)
- [Key Features Documentation](#key-features-documentation)
- [Contributors](#contributors)

## Overview

ApniDukaan is a full-featured e-commerce platform built with the MERN (MongoDB, Express, React, Node.js) stack. The platform supports user authentication, product browsing, shopping cart management, favorites, and order processing with payment integration.

<!-- **Course:** IT264 - Full Stack Web Development   -->
**Author:** [@Harsh Murjani](https://github.com/hm05)

## ✨ Features

### User Features
- User registration and authentication with JWT
- Secure password hashing with bcryptjs
- User profile management
- Order history tracking
- Favorites/Wishlist functionality
- Shopping cart with persistent storage
- Product ratings and reviews

### Product Management
- Browse products with filtering and search
- Product categories
- Product details with images
- Product carousel display
- Ratings and reviews system
- Stock management

### Admin Features
- Admin dashboard
- User management (view, update, delete)
- Product management (CRUD operations)
- Category management
- Order management
- File upload for product images

### E-Commerce Features
- Shopping cart functionality
- Multiple items with quantity management
- Shipping information
- Order placement
- PayPal payment integration
- Order tracking

## 🛠 Tech Stack

### Backend
- **Runtime:** Node.js
- **Framework:** Express.js
- **Database:** MongoDB with Mongoose ODM
- **Authentication:** JWT (JSON Web Tokens)
- **Security:** bcryptjs for password hashing
- **Async Operations:** express-async-handler
- **File Upload:** express-formidable & multer
- **Environment:** dotenv

### Frontend
- **Library:** React.jsx
- **Build Tool:** Vite
- **State Management:** Redux Toolkit with RTK Query
- **Styling:** Tailwind CSS
- **PostCSS:** For advanced CSS processing

### Development Tools
- **Node Manager:** npm
- **Concurrency:** concurrently for running frontend and backend simultaneously
- **Auto-reload:** nodemon

## 📁 Project Structure

```
ApniDukaan/
├── backend/                          # Node.js Express API
│   ├── config/
│   │   └── db.js                    # MongoDB connection
│   ├── controllers/                  # Business logic
│   │   ├── userController.js
│   │   ├── productController.js
│   │   ├── categoryController.js
│   │   └── orderController.js
│   ├── models/                       # Mongoose schemas
│   │   ├── userModel.js
│   │   ├── productModel.js
│   │   ├── categoryModel.js
│   │   └── orderModel.js
│   ├── routes/                       # API endpoints
│   │   ├── userRoutes.js
│   │   ├── productRoutes.js
│   │   ├── categoryRoutes.js
│   │   ├── orderRoutes.js
│   │   └── uploadRoutes.js
│   ├── middlewares/                  # Custom middleware
│   │   ├── authMiddleware.js        # JWT authentication
│   │   ├── asyncHandler.js          # Async error handling
│   │   └── checkId.js               # ID validation
│   ├── utils/
│   │   └── createToken.js           # JWT token generation
│   └── index.js                      # Server entry point
│
├── frontend/                         # React.jsx + Vite
│   ├── src/
│   │   ├── components/              # Reusable components
│   │   │   ├── Header.jsx
│   │   │   ├── Modal.jsx
│   │   │   ├── Loader.jsx
│   │   │   ├── Message.jsx
│   │   │   ├── PrivateRoute.jsx
│   │   │   ├── ProgressSteps.jsx
│   │   │   └── CategoryForm.jsx
│   │   ├── pages/                   # Page components
│   │   │   ├── Home.jsx
│   │   │   ├── Shop.jsx
│   │   │   ├── Cart.jsx
│   │   │   ├── Auth/                # Authentication pages
│   │   │   ├── Products/            # Product pages
│   │   │   ├── Orders/              # Order pages
│   │   │   ├── User/                # User pages
│   │   │   └── Admin/               # Admin pages
│   │   ├── redux/                   # Redux Toolkit store
│   │   │   ├── store.js
│   │   │   ├── api/                 # RTK Query slices
│   │   │   └── features/            # Redux slices
│   │   ├── Utils/                   # Utility functions
│   │   ├── App.jsx
│   │   └── main.jsx
│   ├── vite.config.js
│   ├── tailwind.config.js
│   └── package.json
│
├── package.json                      # Root package configuration
└── README.md                         # This file
```

## 🚀 Installation

### Prerequisites
- Node.js (v14 or higher)
- npm or yarn
- MongoDB (local or MongoDB Atlas)

### Steps

1. **Clone the repository:**
   ```bash
   git clone https://github.com/hm05/ApniDukaan.git
   cd ApniDukaan
   ```

2. **Install root dependencies:**
   ```bash
   npm install
   ```

3. **Install backend dependencies:**
   ```bash
   cd backend
   npm install
   ```

4. **Install frontend dependencies:**
   ```bash
   cd ../frontend
   npm install
   ```

5. **Configure environment variables (see below)**

6. **Run the application:**
   ```bash
   npm run dev
   ```
   This starts both frontend (port 3000) and backend (port 5000) concurrently.

## 🔐 Environment Variables

Create `.env` file in the root directory:

```env
# Server Configuration
PORT=5000
NODE_ENV=development

# Database
MONGO_URI=mongodb://localhost:27017/apnidukaan
# OR use MongoDB Atlas
# MONGO_URI=mongodb+srv://username:password@cluster.mongodb.net/apnidukaan

# Authentication
JWT_SECRET=your_jwt_secret_key_here

# PayPal Integration
PAYPAL_CLIENT_ID=your_paypal_client_id_here

# File Upload (if using file storage)
UPLOAD_PATH=./uploads
```

## 📖 Usage

### Running in Development Mode
```bash
npm run dev              # Run both frontend and backend
npm run backend          # Run only backend
npm run frontend         # Run only frontend
```

### Building for Production
```bash
cd frontend
npm run build
```

## 🔌 API Routes

### User Routes (`/api/users`)
- `POST /` - Register new user
- `POST /auth` - Login user
- `POST /logout` - Logout user
- `GET /profile` - Get current user profile (protected)
- `PUT /profile` - Update current user profile (protected)
- `GET /` - Get all users (admin only)
- `GET /:id` - Get user by ID (admin only)
- `PUT /:id` - Update user by ID (admin only)
- `DELETE /:id` - Delete user (admin only)

### Product Routes (`/api/products`)
- `GET /` - Get all products with filtering
- `GET /:id` - Get product details
- `POST /` - Create product (admin only)
- `PUT /:id` - Update product (admin only)
- `DELETE /:id` - Delete product (admin only)

### Category Routes (`/api/category`)
- `GET /` - Get all categories
- `POST /` - Create category (admin only)
- `PUT /:id` - Update category (admin only)
- `DELETE /:id` - Delete category (admin only)

### Order Routes (`/api/orders`)
- `POST /` - Create order
- `GET /mine` - Get user's orders (protected)
- `GET /:id` - Get order details
- `PUT /:id/pay` - Update order payment status
- `GET /` - Get all orders (admin only)

### Upload Routes (`/api/upload`)
- `POST /` - Upload product image

## 🎯 Key Features Documentation

### Authentication & Authorization
- **JWT-based authentication** with HTTP-only cookies
- **Role-based access control** (Admin vs User)
- **Password security** with bcryptjs hashing (10-round salt)
- Token expiration: 30 days

### Error Handling
- **Async error handler middleware** for consistent error responses
- **Try-catch wrapped async operations** in controllers
- **Input validation** at route level

### Database Design
- **Mongoose schemas** with validation and timestamps
- **Model relationships** (User → Orders, Products → Categories)
- **Indexed fields** for optimized queries

### Frontend State Management
- **Redux Toolkit** for global state
- **RTK Query** for server state and caching
- **Persistent storage** for cart and preferences

## 👥 Contributors

<a href="https://github.com/hm05/ApniDukaan/graphs/contributors">
  <img src="https://contributors-img.web.app/image?repo=hm05/ApniDukaan" />
</a>

---

**Made with ❤️ from Harsh Murjani**
