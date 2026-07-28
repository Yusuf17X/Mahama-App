# Mahama App

A **sustainability gamification platform** for schools that empowers students to take on eco-friendly challenges, earn points, unlock achievement badges, and compete in a school leaderboard — turning environmental action into an engaging, measurable experience.

## Features

- **Eco-Challenges** — Students complete daily, weekly, or one-time challenges (e.g., planting, recycling, water conservation) in solo or school-wide modes, with trackable environmental impact (CO₂ saved, water saved, plastic reduced, energy saved).
- **Gamification & Progression** — Earn points for each completed challenge, maintain activity streaks, and unlock badges based on challenge count or points thresholds.
- **School Leaderboards** — school rankings with aggregate points and student participation, plus a public dashboard showing total platform-wide eco-impact.
- **Role-Based Access** — Three user roles (student, teacher, admin). Teachers can create and assign "school task" challenges; admins manage the full platform.
- **Interactive Dashboard** — Visualized eco-impact statistics and top-school leaderboard with medal-based rankings.
- **Secure Authentication** — JWT-based login/registration, password reset via email, and role-protected routes.

## Tech Stack

| Layer     | Technology |
|-----------|------------|
| **Frontend** | React 18, TypeScript, Vite, React Router v6, TanStack React Query |
| **UI & Styling** | Tailwind CSS, shadcn/ui (Radix UI primitives), class-variance-authority, lucide-react, embla-carousel |
| **Forms & Validation** | React Hook Form, Zod |
| **Charts** | Recharts |
| **State & Data** | React Context API, TanStack React Query |
| **Backend** | Node.js, Express 5 |
| **Database** | MongoDB (Mongoose ODM) |
| **Auth & Security** | JWT, bcryptjs, Helmet, rate limiting, HPP, NoSQL/XSS sanitization, CORS |
| **File Handling** | Multer, Sharp (image processing) |
| **Email** | Nodemailer |
| **Monorepo** | npm scripts + concurrently |

## Project Structure

```
.
├── frontend/          # React/Vite frontend application (port 8080)
├── backend/           # Node/Express backend API (port 5000)
├── package.json       # Root package.json for monorepo scripts
└── README.md         # This file
```

## Quick Start

### Prerequisites

- Node.js (v18 or higher recommended)
- npm
- MongoDB instance (local or remote)

### Initial Setup

1. **Install all dependencies** for both frontend and backend:

   ```bash
   npm run install:all
   ```

2. **Configure backend environment**:
   - Create `backend/config.env` file with required environment variables (MongoDB connection, etc.)
   - Refer to backend documentation for required variables

### Development

**Run both frontend and backend concurrently** with a single command:

```bash
npm run dev
```

This will start:

- Frontend development server at `http://localhost:8080`
- Backend API server at `http://localhost:5000`

### Individual Commands

If you need to run services separately:

- **Frontend only**:

  ```bash
  npm run dev:frontend
  ```

- **Backend only**:
  ```bash
  npm run dev:backend
  ```

## API Configuration

The frontend is configured to connect to the backend API at `http://localhost:5000/api/v1` by default.

You can override this by setting the `VITE_API_URL` environment variable in the frontend:

```bash
cd frontend
echo "VITE_API_URL=http://your-api-url" > .env
```

## Additional Information

- Backend test data seeder: `backend/dev-data/README.md`
