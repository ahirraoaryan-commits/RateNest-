# RateNest ⭐️

> **A secure, role-based store rating and discovery platform for customers, store owners, and administrators.**

[![GitHub Repository](https://img.shields.io/badge/GitHub-RateNest-black?logo=github)](https://github.com/ahirraoaryan-commits/RateNest-)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.x-blue?logo=typescript)](https://www.typescriptlang.org/)
[![React](https://img.shields.io/badge/React-19-61DAFB?logo=react)](https://react.dev/)
[![Node.js](https://img.shields.io/badge/Node.js-20%2B-green?logo=node.js)](https://nodejs.org/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-Database-4169E1?logo=postgresql)](https://www.postgresql.org/)
[![Prisma](https://img.shields.io/badge/Prisma-ORM-2D3748?logo=prisma)](https://www.prisma.io/)

---

## 📌 Overview

**RateNest** is a full-stack web application that allows users to discover registered stores, view ratings, and submit or update their own ratings.

The platform provides separate experiences and permissions for:

* 👤 **Normal Users**
* 🏪 **Store Owners**
* 🛡️ **Administrators**

The application focuses on secure authentication, role-based authorization, store management, rating management, email verification, invitation-based privileged onboarding, and administrative analytics.

---

## 🔗 Repository

**GitHub:**
https://github.com/ahirraoaryan-commits/RateNest-

Clone the project:

```bash
git clone https://github.com/ahirraoaryan-commits/RateNest-.git
cd RateNest-
```

---

## ✨ Features

### 👤 Normal Users

* Create an account with email verification
* OTP-based registration verification
* Secure sign in and sign out
* Browse registered stores
* Search stores by name or address
* Sort stores by supported fields
* View overall store ratings
* Submit ratings from **1–5**
* Update existing ratings
* Change account password
* Access a dedicated user workspace

### 🏪 Store Owners

* Secure role-based authentication
* Dedicated store-owner dashboard
* View owned store information
* View average store rating
* View total number of ratings
* View users who rated the store
* Sort raters by:

  * Name
  * Email
  * Address
  * Rating
* Change account password
* Secure logout

### 🛡️ Administrators

* Administrative dashboard
* View platform statistics
* View total users
* View registered stores
* View total ratings
* Create and manage users
* Manage user roles
* Search and filter users
* Sort users
* View detailed user information
* Create and manage stores
* View store ownership information
* View store rating statistics
* Search and sort stores
* Create privileged invitations
* Invite Administrators
* Invite Store Owners
* Manage privileged onboarding
* Audit important administrative actions

---

## 🔐 Security

Security is an important part of RateNest's architecture.

The application includes:

* Role-based access control
* Server-side authorization
* HTTP-only authentication cookies
* JWT-based authentication
* Password hashing with `bcrypt`
* Request validation with `Zod`
* Rate limiting
* Helmet security headers
* CORS configuration
* OTP hashing
* Invitation token hashing
* Invitation code hashing
* Expiring OTP verification codes
* Expiring privileged invitations
* Limited OTP attempts
* Limited invitation-code attempts
* Email-bound privileged invitations
* Transaction-safe invitation redemption
* Audit logging
* Database constraints and indexes
* Centralized error handling
* Input sanitization

### Email Verification

Normal-user registration uses a verification OTP.

* OTP lifetime: **10 minutes**
* Maximum verification attempts: **5**
* Resend cooldown: **60 seconds**

### Privileged Invitations

Administrators and Store Owners can be onboarded using secure invitations.

* Invitation lifetime: **72 hours**
* Invitation tokens are securely hashed
* Invitation codes are securely hashed
* Invitations are bound to specific email addresses
* Maximum incorrect code attempts: **5**
* Previous unused invitations can be invalidated
* Invitation redemption is transaction-safe

---

## 🏗️ System Architecture

```text
┌──────────────────────────────┐
│        React Frontend        │
│          Vite + TS           │
└──────────────┬───────────────┘
               │
               │ HTTP / JSON
               ▼
┌──────────────────────────────┐
│       Express REST API       │
│                              │
│ Authentication               │
│ Authorization                │
│ Validation                   │
│ Business Logic               │
└──────────────┬───────────────┘
               │
               │ Prisma ORM
               ▼
┌──────────────────────────────┐
│        PostgreSQL DB         │
│                              │
│ Users                        │
│ Stores                       │
│ Ratings                      │
│ Registrations                │
│ Invitations                  │
└──────────────────────────────┘
               │
               │ SMTP
               ▼
┌──────────────────────────────┐
│      Email Infrastructure    │
│       MailHog / SMTP         │
└──────────────────────────────┘
```

---

## 🧰 Tech Stack

### Frontend

* React 19
* TypeScript
* Vite
* React Router
* Context API
* Responsive UI
* Client-side validation

### Backend

* Node.js 20+
* Express 5
* TypeScript
* REST API
* JWT authentication
* HTTP-only cookies
* Zod validation
* Nodemailer
* Swagger/OpenAPI

### Database

* PostgreSQL
* Prisma ORM
* Prisma migrations
* Database constraints
* Database indexes

### Security

* bcrypt
* JWT
* Helmet
* CORS
* Rate limiting
* Zod
* Secure cookies
* Hash-based OTP and invitation secrets

### Testing & Code Quality

* Vitest
* Supertest
* ESLint
* Prettier
* TypeScript strict checking
* Integration testing
* GitHub Actions CI

### Deployment

* Docker
* Docker Compose
* PostgreSQL
* SMTP
* Vercel-compatible configuration

---

## 📁 Project Structure

```text
RateNest-/
│
├── api/
│   ├── [...path].ts
│   └── tsconfig.json
│
├── client/
│   ├── index.html
│   ├── src/
│   │   ├── components/
│   │   │   ├── AppShell.tsx
│   │   │   └── ui.tsx
│   │   │
│   │   ├── context/
│   │   │   ├── AuthContext.tsx
│   │   │   └── ToastContext.tsx
│   │   │
│   │   ├── lib/
│   │   │   ├── api.ts
│   │   │   └── validation.ts
│   │   │
│   │   ├── pages/
│   │   │   ├── AccountPages.tsx
│   │   │   ├── AdminPages.tsx
│   │   │   ├── AuthPages.tsx
│   │   │   ├── OwnerDashboardPage.tsx
│   │   │   ├── StatusPages.tsx
│   │   │   └── StoreDirectoryPage.tsx
│   │   │
│   │   ├── App.tsx
│   │   ├── main.tsx
│   │   ├── styles.css
│   │   └── types.ts
│   │
│   └── vite.config.ts
│
├── prisma/
│   ├── migrations/
│   ├── schema.prisma
│   └── seed.ts
│
├── server/
│   └── src/
│       ├── config/
│       ├── lib/
│       ├── middleware/
│       ├── routes/
│       ├── schemas/
│       ├── app.ts
│       └── index.ts
│
├── .github/
│   └── workflows/
│       └── ci.yml
│
├── Dockerfile
├── compose.yaml
├── DEPLOYMENT.md
├── PROJECT_DOCUMENTATION.md
├── REQUIREMENTS.md
├── .env.example
├── package.json
└── README.md
```

---

## 🗃️ Database Design

RateNest uses PostgreSQL with Prisma ORM.

### User

```text
User
├── id
├── name
├── email
├── address
├── passwordHash
├── role
├── emailVerified
├── createdAt
└── updatedAt
```

Supported roles:

```text
ADMIN
NORMAL_USER
STORE_OWNER
```

### Store

```text
Store
├── id
├── name
├── email
├── address
├── ownerId
├── createdAt
└── updatedAt
```

### Rating

```text
Rating
├── id
├── value
├── userId
├── storeId
├── createdAt
└── updatedAt
```

Each user can have only one rating per store:

```text
Unique(userId, storeId)
```

---

## 🔄 Application Flow

### User Registration

```text
User enters registration details
            │
            ▼
      Validate request
            │
            ▼
       Generate OTP
            │
            ▼
       Hash OTP
            │
            ▼
    Send verification email
            │
            ▼
       User enters OTP
            │
            ▼
       Verify OTP
            │
            ▼
    Create verified account
            │
            ▼
        Sign in
```

### Store Rating

```text
User signs in
      │
      ▼
Store Directory
      │
      ├── Search
      ├── Sort
      └── View ratings
              │
              ▼
        Select store
              │
              ▼
        Choose 1–5
              │
              ▼
       Submit / Update
              │
              ▼
       Store rating updated
```

### Privileged User Onboarding

```text
Administrator
      │
      ▼
Create invitation
      │
      ├──────────────┐
      ▼              ▼
   ADMIN        STORE_OWNER
      │              │
      └──────┬───────┘
             ▼
    Generate secure invitation
             │
             ▼
      Recipient opens link
             │
             ▼
       Verify invitation
             │
             ▼
      Complete registration
             │
             ▼
      Create privileged user
```

---

## ⚙️ Prerequisites

Before running RateNest locally, install:

* **Node.js 20+**
* **npm**
* **PostgreSQL**
* **Git**

For email testing:

* MailHog or another SMTP server

Optional:

* Docker
* Docker Compose

---

## 🚀 Installation

### 1. Clone the repository

```bash
git clone https://github.com/ahirraoaryan-commits/RateNest-.git
cd RateNest-
```

### 2. Install dependencies

```bash
npm install
```

### 3. Configure environment variables

Create the environment file:

```bash
cp .env.example .env
```

Update `.env` with your local configuration.

Example:

```env
NODE_ENV=development
PORT=4000
CLIENT_ORIGIN=http://localhost:5173

DATABASE_URL="postgresql://postgres:postgres@localhost:5432/storefront_ratings?schema=public"

JWT_SECRET=replace-with-a-long-random-secret
JWT_EXPIRES_IN=8h

SMTP_HOST=localhost
SMTP_PORT=1025
SMTP_USER=
SMTP_PASSWORD=
SMTP_FROM="RateNest <no-reply@ratenest.local>"
```

> **Never commit `.env` or production secrets to GitHub.**

---

## 🐘 Database Setup

Make sure PostgreSQL is running.

Generate the Prisma client:

```bash
npm run prisma:generate
```

Run migrations:

```bash
npm run prisma:migrate
```

Seed the database:

```bash
npm run prisma:seed
```

For production:

```bash
npm run prisma:deploy
```

---

## 📧 Email Testing with MailHog

RateNest can use MailHog during local development.

Example configuration:

```env
SMTP_HOST=localhost
SMTP_PORT=1025
```

MailHog's web interface is generally available at:

```text
http://localhost:8025
```

This makes it possible to test OTP and invitation emails locally without sending real emails.

---

## 💻 Running the Application

Start the development environment:

```bash
npm run dev
```

Typical local endpoints:

```text
Frontend → http://localhost:5173
Backend  → http://localhost:4000
```

---

## 🏭 Production Build

Build the project:

```bash
npm run build
```

Start the production server:

```bash
npm start
```

---

## 🐳 Docker

Build the Docker image:

```bash
docker build -t ratenest .
```

Start the application using Docker Compose:

```bash
docker compose up --build
```

Stop the containers:

```bash
docker compose down
```

---

## 🧪 Testing

Run the test suite:

```bash
npm test
```

Run tests in watch mode:

```bash
npm run test:watch
```

Run TypeScript checks:

```bash
npm run typecheck
```

Run ESLint:

```bash
npm run lint
```

Automatically fix lint issues:

```bash
npm run lint:fix
```

Check formatting:

```bash
npm run format:check
```

Format the project:

```bash
npm run format
```

---

## 🔍 API Documentation

RateNest includes API documentation through OpenAPI/Swagger.

The backend exposes REST endpoints for areas including:

```text
/auth
/stores
/admin
/owner
/health
/docs
```

Protected endpoints require appropriate authentication and authorization.

---

## 👥 Role-Based Access Control

| Role                  | Capabilities                                              |
| --------------------- | --------------------------------------------------------- |
| 👤 **Normal User**    | Browse stores, view ratings, submit/update ratings        |
| 🏪 **Store Owner**    | View owned store performance and raters                   |
| 🛡️ **Administrator** | Manage users, stores, invitations and platform statistics |

Authorization is enforced on the **server side**.

This means users cannot bypass permissions simply by manually calling protected API endpoints.

---

## ⭐ Rating System

Users can rate stores using a **1–5** scale:

```text
1 ★
2 ★★
3 ★★★
4 ★★★★
5 ★★★★★
```

A user cannot create duplicate ratings for the same store.

If a rating already exists, the user can update it.

---

## ✅ Validation

RateNest validates input on both the client and server.

| Field    | Requirement                                        |
| -------- | -------------------------------------------------- |
| Name     | 20–60 characters                                   |
| Address  | Maximum 400 characters                             |
| Email    | Valid email format                                 |
| Password | 8–16 characters with uppercase + special character |
| Rating   | Integer from 1–5                                   |

Server-side validation remains authoritative.

---

## 🔑 Environment Variables

| Variable                     | Description                          |
| ---------------------------- | ------------------------------------ |
| `NODE_ENV`                   | Application environment              |
| `PORT`                       | Backend server port                  |
| `CLIENT_ORIGIN`              | Allowed frontend origin              |
| `TRUST_PROXY`                | Reverse proxy configuration          |
| `DATABASE_URL`               | PostgreSQL connection string         |
| `JWT_SECRET`                 | JWT signing secret                   |
| `JWT_EXPIRES_IN`             | Authentication session duration      |
| `SMTP_HOST`                  | SMTP hostname                        |
| `SMTP_PORT`                  | SMTP port                            |
| `SMTP_USER`                  | SMTP username                        |
| `SMTP_PASSWORD`              | SMTP password                        |
| `SMTP_FROM`                  | Sender email                         |
| `ADMIN_BOOTSTRAP_TOKEN`      | Optional first-admin bootstrap token |
| `ADMIN_BOOTSTRAP_CODE`       | Optional first-admin bootstrap code  |
| `ADMIN_BOOTSTRAP_EXPIRES_AT` | Optional bootstrap expiration        |

---

## 🛡️ Administrator Bootstrap

For a fresh deployment where no Administrator account exists, RateNest can support an initial administrator bootstrap process.

Configure:

```env
ADMIN_BOOTSTRAP_TOKEN=...
ADMIN_BOOTSTRAP_CODE=...
ADMIN_BOOTSTRAP_EXPIRES_AT=...
```

The bootstrap process should only be available when:

1. Required bootstrap variables are configured.
2. The bootstrap credentials have not expired.
3. No Administrator account currently exists.

After creating the first Administrator, remove the bootstrap credentials from the environment.

---

## 🔄 CI/CD

The project includes GitHub Actions:

```text
.github/
└── workflows/
    └── ci.yml
```

The CI pipeline can verify:

* Dependency installation
* TypeScript compilation
* Linting
* Tests
* Production build

This helps maintain code quality and prevents broken changes from being merged.

---

## 📚 Documentation

Additional documentation is available in the repository:

| File                        | Description                                     |
| --------------------------- | ----------------------------------------------- |
| `REQUIREMENTS.md`           | Project requirements and implementation details |
| `PROJECT_DOCUMENTATION.md`  | Detailed project documentation                  |
| `DEPLOYMENT.md`             | Deployment instructions                         |
| `REGISTRATION_ERROR_FIX.md` | Registration troubleshooting                    |
| `.env.example`              | Environment configuration template              |

---

## 📈 Future Improvements

Potential future enhancements include:

* 📍 Location-based store discovery
* 🏷️ Store categories and tags
* 📊 Advanced rating analytics
* 📈 Rating distribution charts
* 👤 Enhanced user profiles
* 🖼️ Store image uploads
* 📄 Pagination for large datasets
* 🔔 Notification system
* 📊 Advanced administrator analytics
* ☁️ Cloud object storage
* 🌐 Production deployment automation
* 🧪 Expanded browser-based E2E testing

---

## 🤝 Contributing

Contributions are welcome.

### Development Workflow

1. Fork the repository.
2. Clone your fork.
3. Create a feature branch:

```bash
git checkout -b feature/your-feature
```

4. Make your changes.
5. Run the quality checks:

```bash
npm run typecheck
npm run lint
npm test
npm run build
```

6. Commit your changes:

```bash
git commit -m "feat: add your feature"
```

7. Push your branch:

```bash
git push origin feature/your-feature
```

8. Open a Pull Request.

Please keep pull requests focused and include appropriate tests for new functionality.

---

## 📄 License

This project currently does not specify an open-source license.

If you intend to release RateNest as an open-source project, add a `LICENSE` file and update this section accordingly.

---

## 👨‍💻 Author

**Aryan Ahirrao**

GitHub:
https://github.com/ahirraoaryan-commits

---

## ⭐ Support the Project

If you find RateNest useful:

* ⭐ Star the repository
* 🍴 Fork the project
* 🐛 Report bugs
* 💡 Suggest improvements
* 🤝 Contribute to the project

---

## 📌 Project Summary

RateNest brings together:

```text
React
   +
TypeScript
   +
Express
   +
PostgreSQL
   +
Prisma
   +
JWT Authentication
   +
Role-Based Access Control
   +
Email Verification
   +
Store Management
   +
5-Star Ratings
   +
Admin Dashboard
   +
Store Owner Dashboard
   +
Automated Testing
   +
Docker
   +
CI/CD
```

### 🌟 RateNest

> **Discover stores. Share experiences. Build trust.**

**Repository:**
https://github.com/ahirraoaryan-commits/RateNest-
