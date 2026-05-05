## What is ShipIt?

ShipIt is a community feedback and roadmap platform. Users submit ideas, vote on what matters most, and follow every feature from concept to shipped — all in one place.

Built as a portfolio project to demonstrate a full-stack TypeScript application with real-world features and learn claudecode in a real environment.

## Features

- **Idea board** — submit, vote, comment, tag and filter ideas
- **Kanban roadmap** — drag and drop ideas between status columns, reorder within columns
- **Global roadmap** — overview of all workspaces in one aggregated view
- **Changelog** — publish release notes linked to shipped ideas
- **Multi-workspace** — separate communities with role-based access (admin/moderator/member)
- **Real-time notifications** — SSE-powered live updates
- **Admin panel** — analytics, growth report, user management, audit log
- **i18n** — Swedish and English, switchable without page reload
- **Dark/light mode** — system preference detection
- **Email digest** — weekly summary of top ideas

## Tech Stack

| Layer          | Technology                                   |
| -------------- | -------------------------------------------- |
| Frontend       | React 18, Vite 5, React Query v5, TypeScript |
| Backend        | Node.js 20, Express, TypeScript              |
| Database       | PostgreSQL 15                                |
| Auth           | JWT (access tokens), bcrypt                  |
| Real-time      | Server-Sent Events (SSE)                     |
| Infrastructure | Docker Compose, nginx                        |

## Getting Started

### Prerequisites

- [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- Git

### Run locally

```bash
git clone https://github.com/YOUR_USERNAME/shipit.git
cd shipit

cp .env.example .env

docker compose up -d

open http://localhost:3000
```

### Demo account

| Email             | Password   | Role  |
| ----------------- | ---------- | ----- |
| `demo@shipit.app` | `demo1234` | Admin |

### Run seed data (optional)

To populate the database with example ideas, users and workspaces:

```bash
docker cp seed.sql voxboard-full-postgres-1:/seed.sql
docker exec voxboard-full-postgres-1 psql -U vox -d voxboard -f /seed.sql
```

## Project Structure

```
shipit/
├── backend/
│   ├── src/
│   │   ├── controllers/   # Route handlers
│   │   ├── middleware/    # Auth, rate limiting, workspace context
│   │   ├── routes/        # Express router
│   │   ├── config/        # DB connection, schema
│   │   └── types/         # Shared TypeScript types
│   └── Dockerfile
├── frontend/
│   ├── src/
│   │   ├── components/    # Reusable UI components
│   │   ├── pages/         # Route-level page components
│   │   ├── context/       # React context (Auth, Workspace, Theme, Lang)
│   │   ├── hooks/         # React Query hooks
│   │   └── i18n.ts        # Translations (sv/en)
│   └── Dockerfile
├── docker-compose.yml
└── seed.sql
```

## Environment Variables

Copy `.env.example` to `.env` and configure:

```env
JWT_SECRET=your-secret-here
POSTGRES_PASSWORD=your-db-password
```

## License

MIT
