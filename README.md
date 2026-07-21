# Azure AI Cost Optimizer

An AI-powered Azure cloud cost optimization tool that automatically scans Azure Resource Groups, detects cost inefficiencies, and generates actionable recommendations to reduce cloud spending.

The application analyzes Azure resources using Azure CLI, leverages the OpenAI API for intelligent cost analysis, stores historical reports in Azure Database for PostgreSQL, and provides real-time progress updates through WebSockets.

---

## Features

- Azure Resource Group scanning
- AI-powered cost optimization analysis
- Detect over-provisioned resources
- Find unused and orphaned resources
- Identify cost-related misconfigurations
- Analyze storage and logging costs
- Live analysis progress using WebSockets
- JWT authentication
- Analysis history stored in PostgreSQL
- Responsive React dashboard

---

## Tech Stack

| Layer | Technology |
|--------|------------|
| Frontend | React + Vite + TypeScript + Tailwind CSS |
| Backend | FastAPI (Python) |
| Authentication | JWT + bcrypt + PyJWT |
| Cloud Provider | Microsoft Azure |
| Resource Discovery | Azure CLI |
| AI Analysis | OpenAI API |
| Database | Azure Database for PostgreSQL |
| Live Updates | FastAPI WebSockets |

---

# Architecture

```text
                           ┌──────────────┐
                           │     USER     │
                           └──────┬───────┘
                                  │
                                  ▼
                     ┌────────────────────────┐
                     │   React Frontend       │
                     └──────────┬─────────────┘
                                │
                     Login / Signup / Dashboard
                                │
                                ▼
                     ┌────────────────────────┐
                     │ FastAPI Backend        │
                     │ JWT Authentication     │
                     └──────┬────────┬────────┘
                            │        │
             ┌──────────────┘        └──────────────┐
             ▼                                     ▼
      Azure CLI                           FastAPI WebSocket
             │                                     │
             ▼                                     ▼
      Azure Resources                     Live Progress Updates
             │
             ▼
        OpenAI API
             │
             ▼
   AI Cost Optimization Engine
             │
             ▼
 Azure PostgreSQL Database
             │
             ▼
      Analysis History
             │
             ▼
      Final Dashboard Report
```

---

# Workflow

```
User
   │
   ▼
Login / Signup
   │
   ▼
JWT Authentication
   │
   ▼
Select Azure Resource Group
   │
   ▼
Azure CLI fetches resources
   │
   ▼
WebSocket streams progress
   │
   ▼
OpenAI analyzes infrastructure
   │
   ▼
Recommendations generated
   │
   ▼
Results stored in PostgreSQL
   │
   ▼
Interactive dashboard report
```

---

# Cost Checks

The analyzer detects:

### Compute

- Oversized Virtual Machines
- Oversized App Services
- Underutilized Databases

### Unused Resources

- Unattached Managed Disks
- Idle Public IP Addresses
- Unused Load Balancers
- Orphaned Resources

### Configuration Issues

- Incorrect Pricing Tiers
- Missing Auto Shutdown
- Missing Reserved Instances
- Inefficient Scaling

### Storage Optimization

- Long Log Retention
- Missing Blob Lifecycle Policies
- Unused Storage Accounts
- Inefficient Backup Policies

---

# Project Structure

```
azure-ai-cost-optimizer/
│
├── backend/
│   ├── api/
│   ├── auth/
│   ├── services/
│   ├── websocket/
│   ├── database/
│   ├── models/
│   ├── utils/
│   └── main.py
│
├── frontend/
│   ├── src/
│   ├── components/
│   ├── pages/
│   ├── hooks/
│   ├── services/
│   └── App.tsx
│
├── README.md
└── requirements.txt
```

---

# Prerequisites

Before running the project, ensure you have:

- Python 3.10+
- Node.js 18+
- Azure CLI
- Azure Subscription
- At least one Azure Resource Group
- Azure Database for PostgreSQL
- OpenAI API Key

Login to Azure:

```bash
az login
```

---

# Installation

## Clone Repository

```bash
git clone https://github.com/<username>/azure-ai-cost-optimizer.git

cd azure-ai-cost-optimizer
```

---

## Backend Setup

```bash
cd backend

pip install -r requirements.txt

cp .env.example .env
```

Update your `.env` file:

```env
DATABASE_URL=
JWT_SECRET=
OPENAI_API_KEY=
```

Run the server:

```bash
uvicorn main:app --reload
```

---

## Frontend Setup

```bash
cd frontend

npm install

npm run dev
```

---

# How It Works

1. User logs in using JWT authentication.
2. User selects an Azure Resource Group.
3. FastAPI invokes Azure CLI to enumerate resources.
4. WebSockets stream live analysis progress to the frontend.
5. Resource metadata is sent to the OpenAI API for intelligent cost analysis.
6. Findings and recommendations are stored in Azure PostgreSQL.
7. The dashboard displays optimization opportunities, estimated savings, and suggested fixes.

---

# Future Improvements

- Azure Cost Management API integration
- Azure Advisor integration
- Terraform remediation generation
- Automatic resource resizing
- Scheduled cost scans
- Email notifications
- PDF report export
- Multi-subscription support
- Azure Monitor metrics integration
- Role-Based Access Control (RBAC)

---

# Security

- JWT Authentication
- Password hashing using bcrypt
- Environment variable secrets
- Protected API endpoints
- SQL injection protection via ORM
- HTTPS-ready deployment

---

# License

This project is licensed under the MIT License.

---

## Author

**Saugat Kunwar**

If you found this project useful, consider giving it a ⭐ on GitHub.
