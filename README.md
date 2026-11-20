# LeadDesk — Deployment & Infrastructure Skeleton

This repository manages multi-container Docker orchestration, environment configurations, and deployment automation for **LeadDesk**.

It orchestrates:
- **`postgres`**: PostgreSQL 15 database container with persistent data volume.
- **`backend`**: Node.js + Express + Prisma API service (`../leaddesk-backend`).
- **`frontend`**: Angular 20+ PWA client served via Nginx (`../leaddesk-frontend`).

---

## Quick Start (Local Development)

### 1. Prerequisites
- Docker & Docker Compose v2+
- Node.js v20+

### 2. Environment Setup
Copy the example environment file if not already present:
```bash
cp .env.example .env
```

### 3. Start Local Environment
```bash
# Start all containers in detached mode
docker compose up -d

# Check container status
docker compose ps

# View logs
docker compose logs -f
```

### 4. Running Migrations & Seeding (First-time setup)
Once the database container is healthy:
```bash
cd ../leaddesk-backend
npm run prisma:migrate
npm run prisma:seed
```

### 5. Access Points
- **Frontend App:** http://localhost:4200
- **Backend API:** http://localhost:4000/api/v1/health
- **PostgreSQL Database:** `localhost:5432` (`user: leaddesk`, `password: leaddesk_secret`, `db: leaddesk_dev`)
