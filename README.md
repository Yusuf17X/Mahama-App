# Mahama App — School Sustainability & Gamification Platform

**Mahama App** is a full-stack sustainability gamification platform for schools that turns eco-friendly actions into measurable, competitive challenges. The backend REST API manages school hierarchies, recurring challenge lifecycles, photo-verified submissions, achievement badges, and real-time environmental impact leaderboards.

## Key Backend Features

- **UTC Challenge Scheduling Engine:** Automated background scheduler (`challengeScheduler`) that manages and resets recurring daily (00:00 UTC) and weekly (Sunday 00:00 UTC) challenges alongside one-time and teacher-assigned school tasks.

- **Gamification, Streaks & Eco-Impact Analytics:** Tracks student points, consecutive completion streaks, automated badge unlocking thresholds, and aggregated environmental impact metrics (carbon emissions, water, plastic, and energy saved) across individual and school-wide leaderboards.

- **Role-Based Access Control (RBAC):** JWT-secured authentication and authorization supporting **3 user roles** (`student`, `teacher`, `admin`), complete with email-based password reset flows via **Nodemailer**.

- **Image Upload & Optimization Pipeline:** Handles challenge completion photo proofs using **Multer** for upload validation and **Sharp** for server-side resizing and compression.

- **Multi-Layer API Security:** Hardened Express 5 architecture with Helmet headers, rate limiting, HTTP Parameter Pollution (`HPP`) protection, CORS configuration, and custom NoSQL/XSS input sanitization.

## Tech Stack

- **Backend Runtime & Framework:** Node.js, Express 5

- **Database & ODM:** MongoDB, Mongoose

- **Authentication & Security:** JSON Web Tokens (JWT), bcryptjs, Helmet, Express Rate Limit, HPP, Custom Input Sanitization

- **Media & Notifications:** Multer, Sharp (image processing), Nodemailer

- **Client Interface:** React / Vite web client consuming the `/api/v1` REST API

## API Endpoints Overview (`/api/v1`)

| Resource Base Path        | Description                                                                 |
| ------------------------- | --------------------------------------------------------------------------- |
| `/api/v1/users`           | User registration, JWT login, password reset, and profile management        |
| `/api/v1/schools`         | School onboarding, management, and aggregate school statistics              |
| `/api/v1/challenges`      | CRUD operations for daily, weekly, one-time, and school-assigned challenges |
| `/api/v1/user-challenges` | Challenge submissions with photo proof, review status, and streak updates   |
| `/api/v1/badges`          | Achievement badge definitions and point/count thresholds                    |
| `/api/v1/user-badges`     | Earned badge records per student                                            |
| `/api/v1/dashboard`       | Public platform-wide environmental impact summary and school leaderboards   |

## Project Structure

```
.
├── backend/               # Node.js + Express 5 + MongoDB REST API (port 5000)
│   ├── controllers/       # Route handlers and factory controllers
│   ├── models/            # Mongoose schemas (User, School, Challenge, Badge, etc.)
│   ├── routes/            # Express API route definitions
│   ├── utils/             # UTC scheduler, eco-impact calculator, Sharp/sanitizer helpers
│   └── dev-data/          # Seed scripts and sample JSON datasets
├── frontend/              # Web client interface (port 8080)
└── package.json           # Root monorepo scripts

```

## Quick Start

### Prerequisites

- Node.js (v18 or higher)

- npm

- MongoDB instance (local or MongoDB Atlas)

### Installation & Setup

1. **Install dependencies** for the monorepo:

   ```
   npm run install:all

   ```

2. **Configure backend environment:**
   Create a `backend/config.env` file with your MongoDB URI, JWT secret, and SMTP credentials.

3. **Seed sample data (optional):**
   Refer to [`backend/dev-data/README.md`](./backend/dev-data/README.md) to populate sample schools, challenges, badges, and users.

### Running the Application

- **Run Backend API only (port 5000):**

  ```
  npm run dev:backend

  ```

- **Run Backend and Frontend concurrently:**

  ```
  npm run dev

  ```
