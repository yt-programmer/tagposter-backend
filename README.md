# Tag Poster Backend

A Node.js/Express REST API backend for the Tag Poster e-commerce application with MongoDB database integration.

## 🚀 Features

- **Products Management**: Full CRUD operations for products (create, read, update, delete)
- **Admin Authentication**: Secure login/logout with JWT tokens
- **Security**: Helmet, CORS, rate limiting, input validation, and sanitization
- **MongoDB Integration**: Using Mongoose for object modeling

## 🛠️ Tech Stack

- **Runtime**: Node.js
- **Framework**: Express.js
- **Database**: MongoDB with Mongoose
- **Authentication**: JWT (JSON Web Tokens)
- **Security**:
  - Helmet (HTTP headers security)
  - CORS (Cross-Origin Resource Sharing)
  - express-rate-limit (Rate limiting)
  - express-validator (Input validation)
  - bcryptjs (Password hashing)
- **Utilities**:
  - dotenv (Environment variables)
  - cookie-parser (Cookie handling)

## 📁 Project Structure

```
backend/
├── controllers/
│   ├── admin.controller.js      # Admin authentication logic
│   └── products.controller.js   # Product CRUD operations
├── middlewares/
│   ├── asyncWrapper.js          # Async error handling wrapper
│   └── verifyToken.js           # JWT token verification
├── models/
│   ├── admin.model.js           # Admin Mongoose schema
│   └── product.model.js         # Product Mongoose schema
├── routes/
│   ├── admin.route.js           # Admin authentication routes
│   └── products.route.js        # Product API routes
├── utils/
│   ├── appError.js              # Custom error class
│   └── httpStatus.js            # HTTP status codes
├── .env                         # Environment variables
├── index.js                     # Application entry point
└── package.json                 # Dependencies
```

## 📦 Installation

```bash
# Install dependencies
npm install
```

## ⚙️ Configuration

Create a `.env` file in the root directory with the following variables:

```env
# Server Configuration
PORT=5000
ORIGIN=http://localhost:5173

# Database
MONGO_URL=your_mongodb_connection_string

# JWT
JWT_SECRET=your_jwt_secret_key
JWT_EXPIRE=30d
```

## 🏃‍♂️ Running the Server

```bash
# Development mode (with nodemon)
npm run server
```

The server will run on `http://localhost:3000` (or the port specified in .env)

## 📡 API Endpoints

### Products API (`/api/products`)

| Method | Endpoint            | Description          | Auth Required |
| ------ | ------------------- | -------------------- | ------------- |
| GET    | `/api/products`     | Get all products     | No            |
| POST   | `/api/products`     | Create a new product | Yes           |
| PATCH  | `/api/products/:id` | Update a product     | Yes           |
| DELETE | `/api/products/:id` | Delete a product     | Yes           |

### Admin API (`/api/auth`)

| Method | Endpoint           | Description       | Auth Required |
| ------ | ------------------ | ----------------- | ------------- |
| POST   | `/api/auth/login`  | Admin login       | No            |
| POST   | `/api/auth/logout` | Admin logout      | Yes           |
| GET    | `/api/auth/me`     | Get current admin | Yes           |

## 🔐 Authentication

The API uses JWT (JSON Web Tokens) for authentication. Protected routes require a valid JWT token in cookies or Authorization header.

### Login Flow

1. Send POST request to `/api/auth/login` with email and password
2. Server returns JWT token in HTTP-only cookie
3. Include the cookie in subsequent authenticated requests

## 🧪 Testing

You can test the API using tools like Postman or curl:

````bash
# Get all products
curl http://localhost:3000/api/products

# Login as admin
curl -X POST http://localhost:3000/api/auth/login

## ⚠️ Error Handling

The API uses a centralized error handling middleware that returns consistent JSON responses:

```json
{
  "status": "error",
  "message": "Error message here",
  "code": 500
}
````

## 📝 License

ISC
