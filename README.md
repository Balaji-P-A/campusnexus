# campusnexus
AI-powered campus opportunity platform that helps students discover verified internships, scholarships, hackathons, and ambassador roles, match eligibility, generate application drafts, and track deadlines in one place.
---
# CampusNexus

AI-powered student support and opportunity platform for college campuses.

## 🚀 Overview

CampusNexus helps college students discover verified opportunities, check eligibility, generate tailored application drafts, and track deadlines in one place.

The product is designed for a fast MVP pilot with one campus and a few hundred users, while keeping the architecture clean enough to scale later. The core experience is built around three surfaces:

- **Student experience** for discovery, matching, drafting, and tracking
- **Admin experience** for opportunity verification and moderation
- **Employer experience** for submitting opportunities for review

## ✨ Features

### Student MVP
- Email/password sign-up and login
- College verification
- Student profile setup
- Resume upload and parsing
- Verified opportunity listings
- Search and filtering
- Deterministic eligibility match score
- AI draft generation for applications
- Editable draft workspace
- Saved opportunities
- Deadline tracking and reminders

### Admin MVP
- Review submitted opportunities
- Approve, reject, or request changes
- Publish verified listings
- View basic usage analytics

### Employer MVP
- Submit opportunity listings
- Track submission status
- Wait for admin approval

## 🧠 Problem It Solves

Students miss opportunities because important information is spread across college email, WhatsApp groups, portals, and social media. Even when they find a relevant opportunity, they still need to check eligibility, prepare an application, and remember deadlines.

That creates avoidable friction and lost chances.

## 💡 Solution

CampusNexus centralizes the full workflow:

1. Students discover verified opportunities
2. The system computes a simple eligibility match score
3. Students generate tailored drafts for resumes, SOPs, or emails
4. Deadlines are tracked automatically
5. Admins keep the listings clean and verified

The result is a practical MVP that is easy to demo and useful from day one.

## 🏗️ Architecture (High-Level)

CampusNexus uses a **modular monolith** for the MVP.

### Core modules
- Auth & Identity
- Student Profiles
- Opportunity Management
- Matching Engine
- Draft Generation
- Notifications
- Admin Moderation
- Analytics

### Data flow
1. A student signs up and completes a profile.
2. The backend stores profile data and optionally parses a resume asynchronously.
3. Admins publish verified opportunities.
4. The matching engine calculates an explainable score based on profile and eligibility rules.
5. When a student requests a draft, the backend sends profile and opportunity context to the AI provider.
6. Background jobs handle reminders and scheduled notifications.

This keeps the system simple, reliable, and easy to extend.

## 📦 Tech Stack

### Frontend
- Next.js
- React
- TypeScript
- Tailwind CSS
- shadcn/ui
- TanStack Query
- React Hook Form
- Zod

### Backend
- NestJS
- TypeScript
- Prisma
- PostgreSQL
- BullMQ
- Redis

### Infrastructure
- Docker
- GitHub Actions
- S3-compatible object storage
- Sentry
- Email provider for transactional messages
- LLM provider for draft generation

## ⚙️ Installation

### Prerequisites
- Node.js 20+
- pnpm
- Docker and Docker Compose
- PostgreSQL
- Redis

### 1. Clone the repository
```bash
git clone https://github.com/<your-org>/campusnexus.git
cd campusnexus
```

### 2. Install dependencies
```bash
pnpm install
```

### 3. Create environment files

Create .env files for the web app, API, and worker based on the example files:
```bash
cp apps/web/.env.example apps/web/.env.local
cp apps/api/.env.example apps/api/.env
cp apps/worker/.env.example apps/worker/.env
```

### 4. Start infrastructure
```bash
docker compose up -d
```

### 5. Run database migrations
```bash
pnpm prisma migrate dev
```

### 6. Start the development servers
```bash
pnpm dev
```

## ▶️ Usage

### Student flow

1. Sign up and verify your college identity  
2. Complete your profile  
3. Browse verified opportunities  
4. Save relevant listings  
5. Check eligibility match scores  
6. Generate a draft for the selected opportunity  
7. Edit and export the draft  
8. Track deadlines from the dashboard  


### Admin flow

1. Log in to the admin panel  
2. Review submitted opportunities  
3. Approve or reject listings  
4. Publish verified opportunities  
5. View basic analytics  


### Employer flow

1. Register or sign in  
2. Submit an opportunity  
3. Wait for admin review  
4. Track approval status  


## 📁 Project Structure

.
├── apps/
│   ├── web/                  # Student-facing web app
│   ├── api/                  # REST API and business logic
│   └── worker/               # Background jobs and scheduled tasks
├── packages/
│   ├── ui/                   # Shared UI components
│   ├── shared/               # Shared types, constants, utilities
│   └── config/               # Shared lint/tsconfig/tooling config
├── prisma/                   # Database schema and migrations
├── docs/                     # Product, architecture, and process docs
├── scripts/                  # Utility scripts
└── docker/                   # Local development infrastructure

### Key Design Principle

Keep business logic in the backend, keep UI lightweight, and keep AI behind a provider abstraction so the app remains usable even if the LLM is unavailable.


## 🔐 Permissions / Security Notes

- Role-based access control is required for students, admins, and employers
- Email verification is required at sign-up
- College verification should be enforced for campus access
- Resume files must be stored securely and only exposed to authorized users
- AI-generated drafts should be treated as assistive content, not authoritative data
- Rate limiting should be enabled on auth and draft-generation endpoints
- Admin actions should be audited


## 🛣️ Roadmap (V1 focused)

- Add stronger resume parsing and profile enrichment
- Improve match-score explanations
- Add notification preferences and reminder controls
- Add advanced admin moderation tools
- Add employer review workflows and posting analytics
- Add better search and filtering as listings grow
- Add mentor and teammate matching only after the MVP proves traction


## 🤝 Contributing

Contributions are welcome.

1. Fork the repository  
2. Create a feature branch  
3. Make a focused change  
4. Add tests where relevant  
5. Open a pull request with a clear description  

Please keep changes aligned with the MVP scope and maintainable architecture.


## 📄 License

Licensed under the **Apache License 2.0**.

This license is a good fit if the repository is made public later and you want permissive commercial use with clear patent protection.

---

# 5. Optional Enhancements

**Suggested GitHub topics (tags):**
- `student-platform`
- `campus-tech`
- `opportunity-discovery`
- `ai-assisted-writing`
- `edtech`
- `nextjs`
- `nestjs`
- `typescript`
- `postgresql`
- `modular-monolith`

**Suggested repo color/theme idea:**  
Deep indigo + slate + white, with a single bright accent color for primary CTAs.

**Suggested logo idea (text-based concept):**  
A clean wordmark: **CampusNexus** with a subtle connected-node icon or an “N” built from linking lines, signaling discovery and connection.

If you want, I can turn this into an actual repo scaffold next: folder tree, starter files, env templates, and a ready-to-paste `package.json`/`docker-compose.yml`.

## 📚 Documentation

- [Idea](https://docs.google.com/document/d/1urMH_g4loW4QplVSbdDPX6dDo4r6v214MG-VxmfAhh0/edit?usp=sharing)
- [Product Overview](./docs/00-overview.md)
- [Product Requirements Document (PRD)](./docs/01-prd.md)
- [Technical Requirements Document (TRD)](./docs/02-trd.md)
- [UI Flows](./docs/03-ui-flows.md)
- [Screen Breakdown](./docs/04-screen-breakdown.md)
- [Architecture](./docs/05-architecture.md)
- [API Spec](./docs/06-api-spec.md)
- [Database Schema](./docs/07-database-schema.md)
- [Security & Privacy](./docs/08-security-privacy.md)
- [Roadmap](./docs/09-roadmap.md)
- [Demo Script](./docs/10-demo-script.md)
