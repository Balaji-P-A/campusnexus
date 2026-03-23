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
