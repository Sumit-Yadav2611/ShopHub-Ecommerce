# ShopHub - Full-Stack E-Commerce Platform

ShopHub is a modern full-stack e-commerce platform built with React, Node.js, Express.js, MongoDB, and Razorpay.

The application provides a complete online shopping experience with user authentication, product management, shopping cart, wishlist, reviews, order management, user profiles, admin dashboard, and Razorpay Test Mode payment integration.

---

## Live Demo

Coming soon.

The application will be deployed after the production deployment setup is completed.

---

## Screenshots

Screenshots will be added after the production deployment.

---

## Features

### Authentication

- User registration
- User login
- JWT-based authentication
- Protected routes
- Admin authentication
- Role-based authorization
- Secure password hashing using bcryptjs

---

### Product Management

- Browse products
- Product details
- Product categories
- Product images
- Product descriptions
- Product pricing
- Product inventory
- Admin product management

---

### Shopping Cart

- Add products to cart
- View cart items
- Remove products from cart
- Quantity management
- Automatic total price calculation
- Cart automatically clears after successful online payment

---

### Wishlist

- Add products to wishlist
- Remove products from wishlist
- View wishlist
- Protected wishlist routes

---

### Product Reviews

- Add product reviews
- Product ratings
- View product reviews
- User-based review system

---

### Order Management

- Place orders
- Cash on Delivery
- Online payment
- Order history
- Order cancellation
- Order status tracking
- Shipping address management
- User-specific orders
- Admin order management

Order status workflow:
           Pending
           ↓
           Processing
           ↓
           Shipped
           ↓
           Delivered

Orders can also be cancelled when applicable.

---
### Online Payment

ShopHub currently uses Razorpay Test Mode for online payment testing.

Payment features include:

- Razorpay Checkout
- Razorpay Test Mode
- Razorpay order creation
- Payment signature verification
- Razorpay Order ID storage
- Razorpay Payment ID storage
- Payment status tracking
- Automatic cart clearing after successful payment
- Secure server-side payment verification

> Important: Razorpay is currently configured in Test Mode. No real money is processed.

---

### User Profile

Users can manage:

- Name
- Email
- Phone number
- Address
- City
- State
- PIN code
- Shipping information

Shipping information is automatically used when creating orders.

---

### Admin Dashboard

The admin dashboard provides:

- Product management
- Add products
- Edit products
- Delete products
- Inventory management
- Order management
- Update order status
- Admin-only protected routes

---

### User Interface

- Responsive design
- Mobile-friendly layout
- Desktop-friendly layout
- Modern navigation bar
- Hero carousel
- Product cards
- Toast notifications
- Responsive shopping cart
- Responsive order pages
- Clean and modern UI

---
# Tech Stack

## Frontend

- React
- React Router
- Tailwind CSS
- Axios
- React Hot Toast
- Vite

## Backend

- Node.js
- Express.js
- MongoDB
- Mongoose
- JWT Authentication
- bcryptjs

## External Services

- MongoDB Atlas
- Cloudinary
- Razorpay

## Development Tools

- Git
- GitHub
- VS Code
- Postman
- Nodemon

---
# Project Architecture

```text
                         ShopHub
                            |
             +--------------+--------------+
             |                             |
             v                             v
       React Frontend                Node.js Backend
             |                             |
             |                        Express.js
             |                             |
             |              +--------------+--------------+
             |              |              |              |
             |              v              v              v
             |          MongoDB        Cloudinary      Razorpay
             |           Atlas
             |              |
             +---------- REST API ----------+

# Project Structure

```text
ShopHub-Ecommerce/
│
├── backend/
│   ├── config/
│   │   ├── cloudinary.js
│   │   ├── db.js
│   │   └── razorpay.js
│   │
│   ├── controllers/
│   │   ├── authController.js
│   │   ├── cartController.js
│   │   ├── orderController.js
│   │   ├── paymentController.js
│   │   ├── productController.js
│   │   ├── reviewController.js
│   │   ├── uploadController.js
│   │   ├── userController.js
│   │   └── wishlistController.js
│   │
│   ├── middleware/
│   │   ├── adminMiddleware.js
│   │   ├── authMiddleware.js
│   │   └── upload.js
│   │
│   ├── models/
│   │   ├── Cart.js
│   │   ├── Order.js
│   │   ├── Product.js
│   │   ├── Review.js
│   │   ├── User.js
│   │   └── Wishlist.js
│   │
│   ├── routes/
│   │   ├── authRoutes.js
│   │   ├── cartRoutes.js
│   │   ├── orderRoutes.js
│   │   ├── paymentRoutes.js
│   │   ├── productRoutes.js
│   │   ├── reviewRoutes.js
│   │   ├── uploadRoutes.js
│   │   ├── userRoutes.js
│   │   └── wishlistRoutes.js
│   │
│   ├── package.json
│   └── server.js
│
├── frontend/
│   ├── public/
│   │
│   ├── src/
│   │   ├── components/
│   │   ├── context/
│   │   ├── pages/
│   │   └── services/
│   │
│   ├── package.json
│   └── vite.config.js
│
├── .gitignore
└── README.md          
# Environment Variables

Environment variables are required to run ShopHub locally and in production.

## Backend Environment Variables

Created a file:

```text
backend/.env
PORT=5000

MONGO_URI=mongodb_connection_string

JWT_SECRET=jwt_secret

CLOUDINARY_CLOUD_NAME=cloudinary_cloud_name
CLOUDINARY_API_KEY=cloudinary_api_key
CLOUDINARY_API_SECRET=cloudinary_api_secret

RAZORPAY_KEY_ID=razorpay_test_key_id
RAZORPAY_KEY_SECRET=razorpay_test_key_secret 
```text
frontend/.env
VITE_API_URL=http://localhost:5000/api
# Local Development

## Prerequisites

Make sure you have installed:

- Node.js
- npm
- MongoDB Atlas account
- Cloudinary account
- Razorpay account (Test Mode)
- Git

---

## Clone Repository

```bash
git clone https://github.com/Sumit-Yadav2611/ShopHub-Ecommerce.git

# API Overview

## Authentication

```http
POST /api/auth/register
POST /api/auth/login
Products
GET    /api/products
GET    /api/products/:id
POST   /api/products
PUT    /api/products/:id
DELETE /api/products/:id
Cart
GET    /api/cart
POST   /api/cart
DELETE /api/cart/:id
Wishlist
GET    /api/wishlist
POST   /api/wishlist
DELETE /api/wishlist/:id
Orders
POST /api/orders
GET  /api/orders/myorders
GET  /api/orders
PUT  /api/orders/:id/status
PUT  /api/orders/:id/cancel
Payments
POST /api/payment/create-order
POST /api/payment/verify
# Razorpay Payment Flow

ShopHub uses Razorpay Test Mode for online payment processing.

The complete payment workflow:

```text
User
 |
 | Clicks "Pay Online"
 v
React Frontend
 |
 | Create Payment Order
 v
Express Backend
 |
 | Generate Razorpay Order
 v
Razorpay Checkout
 |
 | User completes Test Payment
 v
Payment Response
 |
 | Payment ID + Signature
 v
Backend Verification
 |
 | Verify Razorpay Signature
 v
MongoDB
 |
 | Create Paid Order
 |
 | Update Payment Status
 |
 | Clear Cart
 v
Orders Page
# Deployment

ShopHub will be deployed using Render.

Deployment architecture:

```text
                 GitHub Repository
                        |
          +-------------+-------------+
          |                           |
          v                           v
   Render Frontend              Render Backend
   React + Vite                 Node + Express
          |                           |
          +-------------+-------------+
                        |
                        v
                 MongoDB Atlas
                        |
                        v
                    Razorpay
# Project Status                    
Authentication              Completed
Product Management          Completed
Shopping Cart               Completed
Wishlist                    Completed
Product Reviews             Completed
Order Management            Completed
Admin Dashboard             Completed
User Profile                Completed
MongoDB Atlas               Completed
Cloudinary                  Completed
Razorpay Test Payment       Completed
Payment Verification        Completed
Automatic Cart Clearing     Completed
Production Deployment       In Progress

# Disclaimer
This project is created for educational, learning, and portfolio purposes.

Razorpay is currently configured in Test Mode. Real customer payments should only be enabled after production payment configuration and security review.
# Author
Sumit Yadav

B.Tech Computer Science & Engineering

GitHub:

https://github.com/Sumit-Yadav2611