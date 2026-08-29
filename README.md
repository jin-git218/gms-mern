# GMS MERN - Grant Management System

## What this is
A full-stack grant management system built with the MERN stack that enables organizations to manage grant applications, announcements, and reviews in real-time. Users can submit grant applications, reviewers can provide feedback, and administrators can manage the entire workflow with live updates via WebSocket connections.

### Stack
- **Language(s):** TypeScript (frontend and backend)
- **Framework / runtime:** React 18.3 (Vite 6), Node.js/Express 4.21 (with TypeScript)
- **Notable libraries:** Redux Toolkit (state management), Material-UI (component library), Mongoose (MongoDB ODM), Socket.IO (real-time communication), JWT (authentication)

## How it's organized

```
frontend/                   React SPA with Vite
  src/
    components/             Reusable UI components
    pages/                  Route-based page components
    sections/               Grouped feature sections
    layouts/                Page layout wrappers
    routes/                 Route definitions and navigation
    services/               API client services
    redux/                  Redux store, slices, and state management
    hooks/                  Custom React hooks
    theme/                  Material-UI theme configuration
    types/                  TypeScript type definitions
    utils/                  Utility functions and helpers
    config/                 Configuration (axios, global settings)
    constants/              App constants

server/                     Express API server
  src/
    routes/                 API endpoints (auth, grants, announcements, reviews)
      user/                 User authentication and profiles
      grantApplication/     Grant application and review processes
      announcement/         Announcements for users
    models/                 Mongoose schemas (User, Application, Comment, Announcement)
    services/               Business logic and integrations
    middleware/             Express middleware (auth verification)
    types/                  TypeScript type definitions
    utils/                  Utility functions
    validator/              Request validation
    constant/               App constants
```

**How it fits together:** Requests flow from the React frontend through Axios-configured API calls to Express routes, which are protected by JWT authentication middleware. The server connects to MongoDB via Mongoose for persistence and broadcasts real-time updates (connections, disconnects, reviews) to all connected clients via Socket.IO on the same port. Redux manages frontend state for user sessions and grant data, while Material-UI provides the component library for a consistent dashboard experience.

## How to run it

**Prerequisites:**
- Node.js 16+
- MongoDB running locally (or update `DB_URI` in `server/.env`)

**Backend:**
```bash
cd server
npm install
npm run dev
```
Server runs on `http://localhost:8000` with Socket.IO on the same port.

**Frontend:**
```bash
cd frontend
npm install
npm run dev
```
Frontend runs on `http://localhost:5173` and connects to the backend at `http://127.0.0.1:8000` (see `frontend/.env`).

**Build for production:**
```bash
# Frontend
cd frontend
npm run build

# Backend
cd server
npm run build  # (if applicable; currently uses ts-node with nodemon)
```

## Try asking

- How do I add a new grant application field to the form and update the Mongoose schema?
- What Socket.IO events are emitted when a grant application is reviewed?
- How does the JWT authentication middleware protect the `/api/grant-application` routes?
