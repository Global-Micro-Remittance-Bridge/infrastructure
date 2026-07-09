# Production Deployment Guide

This guide explains how to deploy the Global Micro-Remittance Bridge to a production environment.

## 🚀 Deployment Architecture
- **Frontend:** Deployed to Vercel (Next.js).
- **Backend API:** Containerized via Docker and deployed to a VPS or Kubernetes cluster.
- **Database:** PostgreSQL (Managed instance like Neon or Supabase recommended).
- **Cache:** Redis (Managed instance like Redis Cloud recommended).
- **Blockchain:** Connected to Stellar Mainnet.

## 🛠️ Setup Steps

### 1. Environment Variables
Create a `.env` file in your production environment with the following:
- `DB_USER`, `DB_PASSWORD`
- `JWT_SECRET`
- `STELLAR_SECRET` (Your production Stellar key)

### 2. Backend Deployment (VPS/Docker)
1. Clone the `infrastructure` repository.
2. Run the production compose file:
   ```bash
   docker-compose -f docker-compose.prod.yml up -d
   ```

### 3. Frontend Deployment (Vercel)
1. Connect your GitHub repository to Vercel.
2. Set the environment variable `NEXT_PUBLIC_API_URL` to your backend URL.
3. Deploy.

### 4. CI/CD Pipeline
The project includes GitHub Actions in `.github/workflows` that automatically build and push images to GHCR on every push to `main`.
