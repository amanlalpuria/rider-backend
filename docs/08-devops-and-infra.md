# 🛠️ DevOps & Infrastructure

This document outlines the CI/CD pipeline, hosting setup, monitoring, and infrastructure tools used to manage RiderX in production.

---

## 🧱 Infrastructure Stack

- **Cloud Provider**: AWS (EC2, RDS, S3, CloudWatch, IAM)
- **Database**: PostgreSQL (Amazon RDS)
- **Containerization**: Docker
- **Orchestration**: Docker Compose (initial), Kubernetes (future)
- **Domain & SSL**: Route53 + ACM

---

## 🔁 CI/CD Pipeline

- **Source Control**: GitHub
- **CI/CD Tool**: GitHub Actions

### Pipeline Steps
1. ✅ Lint, format, run tests
2. 🔐 Secrets loaded from GitHub Secrets
3. 🐳 Build & push Docker image to GHCR
4. 🚀 Deploy via SSH or Terraform on EC2

---

## 🔐 Secrets Management

- Stored securely in GitHub Secrets and EC2 env vars
- Example keys: `JWT_SECRET`, `AWS_ACCESS_KEY`, `DB_PASSWORD`

---

## 📦 Deployment Targets

- **Backend**: EC2 instance with Docker
- **Frontend**: GitHub Pages (initial), then S3 + CloudFront
- **Monitoring**: CloudWatch logs + UptimeRobot (basic alerts)

---

## 🧪 Environments

- **Development**: `.env.dev` with mock services
- **Staging**: Pre-prod replica, test payments enabled
- **Production**: Fully secure, audited logs, real payment integrations

---

## 📤 Backups & Rollbacks

- **PostgreSQL**: RDS snapshots daily
- **App Logs**: Shipped to CloudWatch + local S3 backup
- **Rollback Strategy**: Docker image version pinning