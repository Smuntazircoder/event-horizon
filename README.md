# Event Horizon

Event Horizon is a full-stack event discovery and management platform. It includes location-aware event search, AI-style natural language search, JWT authentication, roles, event creation, registration, bookmarks, admin stats, PostgreSQL/Prisma persistence, and responsive React UI.

## Quick start

1. Copy `.env.example` to `.env` and set `DATABASE_URL` and `JWT_SECRET`.
2. Run `npm install` from this folder.
3. Run `npm run db:generate`, then `npm run prisma:migrate -w backend -- --name init`.
4. Run `npm run db:seed` to load 36 realistic events. Demo organizer: `organizer@eventhorizon.dev` / `DemoPass123!`.
5. Run `npm run dev`, then visit the Vite URL (normally `http://localhost:5173`).

## API

- `POST /api/auth/register`, `POST /api/auth/login`
- `GET /api/categories`, `GET /api/events`, `GET /api/events/:slug`
- `POST /api/events` (organizer), `POST /api/events/:id/register`, `POST /api/events/:id/bookmark`
- `POST /api/ai/search` and `GET /api/admin/stats` (admin)

Event search accepts `q`, `city`, `category`, `price=free|paid`, `date=today`, and nearby `lat`, `lng`, `distance` in km. The AI endpoint is intentionally an abstraction point: connect an LLM provider using `LLM_API_URL` and `LLM_API_KEY`; no key is hard-coded.

## Production

Run `npm run build`, set secure production environment values, run migrations in CI/CD, and serve `frontend/dist` behind a TLS reverse proxy. Rate limiting, validation, password hashing, JWT auth, and role checks are in the API baseline.
