# Technical Specification
## Multi-Tenant SaaS Platform – Project & Task Management System

---

## 1. Project Structure

### Backend Structure

```text
backend/
├── src/
│   ├── controllers/   # Business logic for APIs
│   ├── routes/        # API route definitions
│   ├── middleware/    # Auth, RBAC, tenant isolation
│   ├── models/        # Database query logic
│   ├── utils/         # Helper functions (JWT, audit logs)
│   ├── config/        # Database and environment config
│   └── app.js         # Express app entry point
├── migrations/        # SQL migration files
├── seeds/             # Seed data SQL
├── Dockerfile         # Backend Docker configuration
├── package.json
└── .env
```

### Frontend Structure

```text
frontend/
├── src/
│   ├── components/    # Reusable UI components
│   ├── pages/         # Page-level components
│   ├── services/      # API calls (Axios)
│   ├── context/       # Auth and global state
│   ├── routes/        # Protected routes
│   ├── utils/         # Helper utilities
│   └── App.js
├── public/
├── Dockerfile         # Frontend Docker configuration
└── package.json
```

---

## 2. Development Setup Guide

### Prerequisites
- **Node.js:** v18+
- **Docker & Docker Compose**
- **Git**

---

## 3. Environment Variables

Create a `.env` file in the backend directory with the following values:

### Backend Environment Variables

```env
DB_HOST=database
DB_PORT=5432
DB_NAME=saas_db
DB_USER=postgres
DB_PASSWORD=postgres

JWT_SECRET=your_jwt_secret_key
JWT_EXPIRES_IN=24h

PORT=5000
NODE_ENV=development

FRONTEND_URL=http://frontend:3000
```

---

## 4. Local Development Setup

### Step 1: Clone Repository

```bash
git clone [https://github.com/Lova-Reddy/multi-tenant-saas.git](https://github.com/Lova-Reddy/multi-tenant-saas.git)
cd multi-tenant-saas
```

### Step 2: Start Application with Docker

Run the following command in the root directory to build and start the containers:

```bash
docker-compose up --build
```

### Step 3: Verify Services

- **Backend Health Check:** [http://localhost:5000/api/health](http://localhost:5000/api/health)
- **Frontend Application:** [http://localhost:3000](http://localhost:3000)

---

## 5. Database Setup

- **Automatic Migrations:** SQL migrations run automatically on backend startup.
- **Seeding:** Seed data loads automatically upon initialization.
- **Note:** No manual database commands are required for initial setup.

---

## 6. Testing

- **API Testing:** APIs can be tested using Postman or Swagger.
- **Authentication:** A valid JWT token is required for all protected routes.
- **RBAC:** Role-based access must be validated manually by switching user accounts.