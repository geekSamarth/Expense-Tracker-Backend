# Expense Tracker API

A full-stack expense tracking application built with **TypeScript**, **Node.js**, **Express**, and **MongoDB**. Users can sign up, log in, create custom categories, track their expenses, and view spending summaries by category and by month.

---

## ✨ Features

- 🔐 User authentication (signup/login) with JWT
- 🏷️ Create, update, and delete custom expense categories
- 💸 Add, edit, delete, and filter expenses
- 📊 Spending summaries (total per month, total per category) via MongoDB aggregation
- 🛡️ Production-ready security (Helmet, CORS, input validation)
- 📝 Structured logging (Pino for production, Morgan for development)
- 🧱 Layered architecture (routes → validation → controller → service → repository → model)
- 📱 PWA-ready frontend (installable on mobile)

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Language | TypeScript |
| Runtime | Node.js |
| Framework | Express |
| Database | MongoDB (Mongoose) |
| Auth | JWT, bcrypt |
| Validation | Zod |
| Logging | Pino (prod), Morgan (dev) |
| Security | Helmet, CORS |
| Package Manager | pnpm |
| Dev Runner | tsx + nodemon |

---

## 📁 Project Structure

```
expense-tracker/
├── src/
│   ├── config/          # App configuration (env, constants)
│   ├── db/              # MongoDB connection setup
│   ├── controllers/     # Request handlers (HTTP layer)
│   ├── services/        # Business logic
│   ├── repository/      # Database queries (Mongoose calls)
│   ├── models/          # Mongoose schemas & TypeScript 
│   ├── routes/          # API route definitions
│   ├── middlewares/     # Auth guard, error handler, etc.
│   ├── validations/     # Zod request-body schemas
│   ├── utils/           # Logger, ApiError, ApiResponse, asyncHandler
│   ├── app.ts           # Express app setup (middleware, routes)
│   └── index.ts         # Server entry point
├── dist/                # Compiled JS output (generated, not committed)
├── .env                 # Environment variables (not committed)
|── pnpm-lock.yaml
├── .env.example         # Sample environment variables
├── tsconfig.json
├── package.json
└── README.md
```

---

## ⚙️ Prerequisites

Before you begin, make sure you have installed:

- **Node.js** (v18 or higher) — [Download](https://nodejs.org/)
- **pnpm** (v8 or higher)
  ```bash
  npm install -g pnpm
  ```
- **MongoDB** — either a local instance or a free [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) cluster

---

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/<your-username>/expense-tracker.git
cd expense-tracker
```

### 2. Install dependencies

```bash
pnpm install
```

### 3. Set up environment variables

Copy the example env file and fill in your own values:

```bash
cp .env.example .env
```

Update `.env` with your values:

```env
PORT=5000
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_secret_key
JWT_EXPIRY=7d
CORS_ORIGIN=http://localhost:5173
NODE_ENV=development
```

### 4. Run the app in development mode

```bash
pnpm run dev
```

The server will start on `http://localhost:5000` (or whatever `PORT` you set), auto-restarting on file changes.

### 5. Build for production

```bash
pnpm run build
pnpm run start
```

- `pnpm run build` compiles TypeScript into plain JavaScript inside `dist/`
- `pnpm run start` runs the compiled production build

---

## 📜 Available Scripts

| Command | Description |
|---|---|
| `pnpm run dev` | Run the app in development mode with auto-reload |
| `pnpm run build` | Compile TypeScript to JavaScript (`dist/`) |
| `pnpm run start` | Run the compiled production build |

---

## 🔑 Environment Variables

| Variable | Description |
|---|---|
| `PORT` | Port the server runs on |
| `MONGO_URI` | MongoDB connection string |
| `JWT_SECRET` | Secret key used to sign JWT tokens |
| `JWT_EXPIRY` | JWT token expiry duration (e.g. `7d`) |
| `CORS_ORIGIN` | Allowed frontend origin for CORS |
| `NODE_ENV` | `development` or `production` |

---

## 📡 API Overview

| Method | Endpoint | Description |
|---|---|---|
| POST | `/api/v1/auth/signup` | Register a new user |
| POST | `/api/v1/auth/login` | Log in and receive a token |
| GET | `/api/v1/categories` | Get all categories for logged-in user |
| POST | `/api/v1/categories` | Create a new category |
| PUT | `/api/v1/categories/:id` | Update a category |
| DELETE | `/api/v1/categories/:id` | Delete a category |
| GET | `/api/v1/expenses` | Get all expenses (supports category filter) |
| POST | `/api/v1/expenses` | Add a new expense |
| PUT | `/api/v1/expenses/:id` | Update an expense |
| DELETE | `/api/v1/expenses/:id` | Delete an expense |
| GET | `/api/v1/expenses/summary` | Get total spent (monthly & per category) |

> Full endpoint documentation with request/response examples coming soon.

---

## 🧪 Testing the API

You can test endpoints using [Postman](https://www.postman.com/) or [Thunder Client](https://www.thunderclient.com/) (VS Code extension). Import the base URL as `http://localhost:5000/api/v1`.

---

## 🗺️ Roadmap

- Complete auth flow (signup/login/JWT middleware)
- Category CRUD
- Expense CRUD
- Monthly & category-wise aggregation summary
- Frontend (React) integration
- Chart visualization for spending
- PWA support (installable on mobile)
- Deployment (backend: Render/Railway, frontend: Vercel/Netlify)

---

## 📄 License

This project is licensed under the ISC License.

---

## 🙋 Author

Built by **Samarth Goyal** as part of a self-driven full-stack development learning journey.
