# 🏗️ Implementation Plan: Project Setup & Foundation (Milestone 1)

This implementation plan outlines the setup of **NotarisPro**, a comprehensive web application for Notary & PPAT office management in Indonesia. We will initiate the first phase (Milestone 1: MVP Foundation) by bootstrapping the codebase, configuring a direct **PostgreSQL database connection**, and setting up the project structure.

## User Review Required

> [!IMPORTANT]
> Based on your feedback, we are using a **standard PostgreSQL database** instead of Supabase. This means all database operations, migrations, and user sessions will run directly on your own PostgreSQL instance via Prisma.
> 
> For authentication, we will use **NextAuth.js (Auth.js)** with the Prisma Adapter, storing all user credentials, sessions, and roles directly in your PostgreSQL database.

## Open Questions

> [!IMPORTANT]
> 1. **Styling Framework Selection:** The previous planning phase (`plan.md`) proposed using **Tailwind CSS + shadcn/ui**. Under our standard guidelines, we default to **Vanilla CSS** unless you explicitly request Tailwind CSS. 
>    * Would you like us to proceed with **Tailwind CSS v4** (recommended for modern Next.js projects) along with shadcn/ui? Or do you prefer **Vanilla CSS**?
> 2. **Next.js & React Version:** Do you prefer using **Next.js 15 (React 19)** (latest stable) or **Next.js 14 (React 18)**? Next.js 15 has the latest optimizations and React Compiler support.
> 3. **File Storage:** Since we are not using Supabase Storage, for document uploads we can use:
>    * **Option A:** Direct integration with **Google Drive API** (storing files securely in a shared office Drive, which fits our plan's USP).
>    * **Option B:** Local file storage on the server (simplest for MVP, but less scalable).
>    * **Option C:** Standard Object Storage (e.g., Cloudflare R2 / AWS S3 / MinIO).
>    * Which option do you prefer?
> 4. **PostgreSQL Connection Details:** Should we configure the project with local/placeholder environment variables first (e.g., `postgresql://localhost:5432/...`), or do you have an active PostgreSQL connection string ready to use?

## Proposed Changes

We will set up the foundational project files in the workspace directory: `c:\Users\Han\Desktop\project notaris`.

### Project Scaffolding

#### [NEW] [package.json](file:///c:/Users/Han/Desktop/project%20notaris/package.json)
- Main project manifest containing dependencies: `next`, `react`, `react-dom`, `typescript`, `@types/react`, `next-auth`, `@prisma/client`, `bcryptjs` (for hashing passwords), etc.

#### [NEW] [tsconfig.json](file:///c:/Users/Han/Desktop/project%20notaris/tsconfig.json)
- TypeScript configuration tailored for Next.js App Router and import aliases (`@/*`).

#### [NEW] [next.config.mjs](file:///c:/Users/Han/Desktop/project%20notaris/next.config.mjs)
- Next.js configuration.

#### [NEW] [src/app/layout.tsx](file:///c:/Users/Han/Desktop/project%20notaris/src/app/layout.tsx)
- Root layout file, implementing responsive metadata, SEO-friendly tags, and loading global styling.

#### [NEW] [src/app/page.tsx](file:///c:/Users/Han/Desktop/project%20notaris/src/app/page.tsx)
- Premium, stunning Landing Page/Dashboard entry point featuring a sleek dark mode, vibrant gradients, and mock metrics to showcase a premium look from day one.

---

### Database Setup

#### [NEW] [prisma/schema.prisma](file:///c:/Users/Han/Desktop/project%20notaris/prisma/schema.prisma)
- Prisma schema file mapping the relational database structure (Users, Roles, Clients, Jobs, Invoices, Cash Transactions, Audit Logs, plus NextAuth Session and Account tables) directly to your **PostgreSQL database**.

#### [NEW] [.env.example](file:///c:/Users/Han/Desktop/project%20notaris/.env.example)
- Example environment template listing required variables (`DATABASE_URL`, `NEXTAUTH_SECRET`, `NEXTAUTH_URL`, etc.).

---

### UI & Styling Setup

#### [NEW] [src/app/globals.css](file:///c:/Users/Han/Desktop/project%20notaris/src/app/globals.css)
- Central style file. If Tailwind is approved, it will import Tailwind directives. If Vanilla CSS is chosen, it will establish our sleek global color system (harmonious HSL palettes, smooth gradients, and interactive micro-animations).

---

## Verification Plan

### Automated Tests
- `npm run lint` to verify TypeScript and ESLint compliance.
- `npm run build` to ensure the Next.js application compiles cleanly.
- `npx prisma validate` to confirm the Prisma schema is syntax-error free.

### Manual Verification
- Launch the development server using `npm run dev`.
- Render the page to verify:
  - Responsive layout (mobile & desktop).
  - Rich aesthetics (vibrant colors, gradients, and micro-animations on interactive elements).
  - Clean routing.
