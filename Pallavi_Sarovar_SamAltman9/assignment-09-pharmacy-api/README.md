# Assignment 09 - Pharmacy & Healthcare Store API

A REST API built with Node.js, Express.js, MongoDB Atlas, Mongoose, JWT and bcryptjs.

## Features

- Customer, Pharmacist and Admin roles
- JWT authentication
- Password hashing with bcryptjs
- Medicine inventory CRUD
- Medicine search and category filtering
- Expiring medicine query
- Customer medicine orders
- Pharmacist/Admin order approval
- Automatic stock deduction when an order is approved
- Prescription notes for prescription medicines
- Role-based access control

## Requirements

Install these first:

- Node.js 18+ recommended
- MongoDB Atlas account
- Postman for API testing

## Setup

1. Open the project folder in Terminal.
2. Run:

npm install

3. Create a `.env` file from `.env.example`.

Mac/Linux:

cp .env.example .env

Windows CMD:

copy .env.example .env

4. Put your MongoDB Atlas connection string in `.env`.

Example:

MONGO_URI=mongodb+srv://USERNAME:PASSWORD@cluster.mongodb.net/pharmacy_db
JWT_SECRET=your_secret_key
PORT=5000
ADMIN_KEY=admin123

5. Start the server:

npm run dev

Or:

npm start

The API runs at:

http://localhost:5000

## Main Endpoints

POST /api/auth/register
POST /api/auth/register-staff
POST /api/auth/login
GET /api/auth/profile

GET /api/medicines
GET /api/medicines/expiring
POST /api/medicines
PUT /api/medicines/:id
DELETE /api/medicines/:id

POST /api/orders
GET /api/orders/my-orders
GET /api/orders
PATCH /api/orders/:id/status

## Staff Registration

Use the ADMIN_KEY from `.env` when registering a pharmacist or admin.

Example JSON:

{
  "name": "Pharmacist One",
  "email": "pharmacist@example.com",
  "password": "password123",
  "role": "pharmacist",
  "adminKey": "admin123"
}

## Authentication

For protected endpoints use:

Authorization: Bearer YOUR_JWT_TOKEN

## Testing Order Flow

1. Register a customer.
2. Register a pharmacist using the staff registration endpoint.
3. Register an admin using the staff registration endpoint.
4. Add a medicine with the pharmacist token.
5. Try adding a medicine with the customer token and confirm 403 Forbidden.
6. Place an order as the customer.
7. Approve the order as pharmacist/admin.
8. Confirm that stockQuantity decreases automatically.

## Important

Do not commit `.env` to GitHub. The `.gitignore` file already excludes it.
