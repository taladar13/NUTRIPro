# NutriPro Product Requirements Document (PRD)

**Version:** 1.0  
**Date:** December 30, 2025  
**Author:** PM Agent (John)  
**Status:** Ready for Architecture

---

## Table of Contents

1. [Goals and Background Context](#1-goals-and-background-context)
2. [Requirements](#2-requirements)
3. [User Interface Design Goals](#3-user-interface-design-goals)
4. [Technical Assumptions](#4-technical-assumptions)
5. [Epic List](#5-epic-list)
6. [Epic Details](#6-epic-details)
7. [Checklist Results Report](#7-checklist-results-report)
8. [Next Steps](#8-next-steps)

---

## 1. Goals and Background Context

### Goals

#### Primary Product Goals

- **Deliver full feature parity** with the existing NutriPro desktop application
  - All 14+ modules from legacy system must be replicated (client management, meal builder, workout builder, blood tests, body composition, medical questionnaire, dictionary management, etc.)
  - Zero functionality regression—partner must confirm system meets daily workflow needs before launch
  - *Why it matters:* Migration blocker; partner won't switch without complete feature coverage

- **Enable cloud-based practice management** accessible from any device
  - Web application works on desktop, laptop, and tablet browsers
  - Support Chrome, Safari, Firefox, Edge (latest 2 versions)
  - Page load <3 seconds, API responses <500ms
  - *Why it matters:* Partner currently locked to one Windows machine; remote access is the #1 pain point

- **Provide real-time client visibility** between appointments
  - Nutritionist dashboard shows client adherence scores, recent activity, alerts
  - Changes sync between web and mobile within 5 seconds
  - *Why it matters:* Currently zero insight into client behavior between visits (often weeks apart)

- **Achieve seamless data migration** from legacy NutriPro desktop
  - 100% of partner's existing data imported: clients, foods, exercises, medications, supplements, history
  - Validation tools to verify migration accuracy
  - *Why it matters:* Years of curated data (5,000+ foods, 500+ exercises) cannot be recreated manually

#### User-Centric Goals

**For Nutritionists:**
- Reduce time spent on meal plan creation by 40%+ via improved UX and templates
- Access client data remotely at least 3x/week
- Generate professional PDF reports in <2 minutes
- View client adherence data between appointments for 80%+ of active clients

**For Clients:**
- Complete daily check-in in <30 seconds (one-tap interactions)
- 80%+ daily app engagement (check in at least once per day)
- Log 90%+ of prescribed workouts with weights/reps
- See weekly adherence score and progress trends anytime

#### Strategic Goals

- **Support Hebrew-first bilingual UI** (Hebrew/English) with proper RTL layout
  - Native RTL support throughout web and mobile
  - Hebrew as default language; English as secondary option
  - *Why it matters:* Underserved market; no major competitor offers Hebrew/RTL

- **Establish market foundation** for commercial expansion
  - Onboard development partner as first production user within 4 months (beta)
  - Launch MVP within 6 months with partner sign-off
  - Achieve 5-10 paying practitioners within 12 months of launch
  - *Why it matters:* Partner-funded development requires path to revenue diversification

---

### Background Context

#### The Problem

NutriPro is a modernization initiative replacing a **10+ year-old Windows desktop application** used by nutritionists in Israel. The existing system—while clinically comprehensive—suffers from critical limitations that constrain the partner's practice:

| Limitation | Impact |
|------------|--------|
| **Desktop-bound** | Can only access client data from one physical computer; no remote work, no tablet use during consultations |
| **Zero client visibility** | Once a client leaves the office, no insight into adherence until the next appointment (often 2-4 weeks later) |
| **No client self-service** | Clients receive printed PDF meal plans; must manually track adherence (most don't) |
| **Dated UX** | Dense Microsoft Access-style forms; slow workflows; steep learning curve |
| **Single-user architecture** | No collaboration; can't share clients between practitioners |

The partner estimates **30+ minutes/day lost** to workarounds, with client churn attributed to poor engagement between visits.

#### The Solution

Two purpose-built applications connected by a shared backend:

1. **NutriPro Web (Nutritionist Application)** — A browser-based practice management system with the full clinical toolset: client management, meal menu builder with real-time nutritional calculations, workout plan creator, blood test tracking, body composition analysis (skinfold/Jackson-Pollock), medical questionnaires, and comprehensive dictionary management.

2. **NutriPro Mobile (Client Application)** — A native iOS/Android app designed for daily use with minimal friction. One-tap meal check-offs, one-tap workout completion, exercise logging (weight/reps/sets), progress dashboard with adherence scores and streaks.

3. **Unified Backend** — Single source of truth with real-time bi-directional sync. Changes on web appear on mobile within seconds and vice versa.

#### Competitive Landscape

| Competitor | Gap NutriPro Fills |
|------------|-------------------|
| **Practice Better / Nutrium** | No Hebrew/RTL support; less clinical depth (blood tests, body composition); no existing data migration path |
| **MyFitnessPal / Cronometer** | Consumer-only; no professional tools; too complex for simple adherence (barcode scanning, portion estimation) |
| **Spreadsheets / Paper** | No automation; no client visibility; error-prone; doesn't scale |

NutriPro is purpose-built for **Hebrew-speaking practitioners** with **clinical depth** that consumer apps lack, plus a **migration path** from the existing desktop system.

#### Development Context

- **Primary stakeholder:** Israeli nutritionist (development partner) who will be the first production user
- **Funding model:** Partner-funded development with milestone-based payments
- **Team size:** Small team (1-2 developers + partner as domain expert)
- **IP arrangement:** Developer retains right to commercialize/license to other practitioners

---

### Change Log

| Date | Version | Description | Author |
|------|---------|-------------|--------|
| Dec 30, 2025 | 1.0 | Initial PRD from Project Brief | PM (John) |

---

## 2. Requirements

### Functional Requirements

#### Authentication & Security
- **FR1:** The system shall provide secure role-based authentication for two user types: Nutritionist and Client
- **FR2:** The system shall support JWT-based authentication with refresh tokens for session management
- **FR3:** The system shall enforce row-level security ensuring clients can only access their own data and nutritionists can only access their own clients' data

#### Master Data System (Dictionary)
- **FR4:** The system shall provide full CRUD operations for Foods with nutritional values (calories, protein, carbs, fat, fiber, 20+ micronutrients), categories, serving sizes, and tags
- **FR5:** The system shall provide full CRUD operations for Exercises with muscle groups, equipment, type, difficulty, and instructions
- **FR6:** The system shall provide full CRUD operations for Medications with name, category, dietary interactions, and notes
- **FR7:** The system shall provide full CRUD operations for Supplements with name, type, dosage guidelines, and interactions
- **FR8:** The system shall provide full CRUD operations for Diseases/Conditions with dietary considerations and contraindications
- **FR9:** The system shall support bulk CSV/Excel import for all dictionary entities to enable legacy data migration
- **FR10:** The system shall provide searchable, filterable interfaces for all dictionary entities

#### Client Management
- **FR11:** Nutritionists shall be able to create, view, update, and archive client profiles including personal info, contact details, status, and type
- **FR12:** The system shall store client medical information including food preferences, allergies, medications, supplements, and medical conditions
- **FR13:** The system shall provide a structured Medical Questionnaire with configurable Yes/No/Notes/Treated columns for health intake

#### Meal Planning
- **FR14:** Nutritionists shall be able to create daily and weekly meal menus by selecting foods from the dictionary
- **FR15:** The system shall calculate and display real-time macro and micronutrient totals as foods are added to meal plans
- **FR16:** The system shall support "Is Primary" food flagging to indicate main components of each meal
- **FR17:** Nutritionists shall be able to assign meal plans to clients with effective date ranges
- **FR18:** The system shall generate PDF exports of meal plans for client distribution

#### Workout Planning
- **FR19:** Nutritionists shall be able to create workout programs by selecting exercises from the dictionary
- **FR20:** The system shall support specifying sets, reps, and target weight for each exercise in a workout plan
- **FR21:** Nutritionists shall be able to assign workout plans to clients with effective date ranges

#### Clinical Features
- **FR22:** The system shall record blood test results with multiple parameters (HDL, LDL, Triglycerides, HbA1c, vitamins, thyroid panels, etc.) with dates and reference ranges
- **FR23:** The system shall display blood test trends over time with graphical visualization
- **FR24:** The system shall calculate body composition using skinfold measurements (7 sites) and Jackson-Pollock formulas
- **FR25:** The system shall track and calculate Fat %, Fat-Free Mass Index (FFMI), and Total Body Water (TBW)
- **FR26:** The system shall record client tracking data: weight, body measurements (belly, waist, arm, forearm), blood pressure, and hand grip strength
- **FR27:** The system shall display historical tracking data with trend graphs

#### Metabolic & Configuration
- **FR28:** The system shall support RMR (Resting Metabolic Rate) calculations using configurable coefficients
- **FR29:** The system shall support activity level coefficients and training type (strength/aerobic) for calorie target calculations
- **FR30:** The system shall provide admin interfaces to manage all configuration tables (blood test parameters, fat % ranges, meal types, client types, cities, etc.)

#### Client Mobile App
- **FR31:** Clients shall see their daily prescribed meals and mark each as completed with a single tap
- **FR32:** Clients shall see their daily prescribed exercises and mark each as completed with a single tap
- **FR33:** Clients shall be able to log actual weight, reps, and sets performed for each exercise
- **FR34:** Clients shall be able to log weight and body measurements on weigh-in days
- **FR35:** Clients shall see a progress dashboard showing adherence percentage, weight trend chart, and streak counter
- **FR36:** Clients shall be able to view their upcoming appointments with their nutritionist
- **FR37:** The mobile app shall support configurable push notifications for meal reminders, workout reminders, and weigh-in reminders

#### Sync & Real-Time
- **FR38:** Changes made on the nutritionist web app shall be visible on the client mobile app within 5 seconds
- **FR39:** Changes made on the client mobile app shall be visible on the nutritionist web app within 5 seconds
- **FR40:** The nutritionist dashboard shall display real-time client adherence scores and recent activity

#### Reports & Export
- **FR41:** The system shall generate PDF reports for meal plans, workout plans, and client progress summaries
- **FR42:** Nutritionists shall be able to view and manage scheduled client appointments

#### Data Migration
- **FR43:** The system shall provide data migration tools to import clients, foods, exercises, medications, supplements, and historical data from the legacy NutriPro desktop system
- **FR44:** The system shall provide validation reports to verify migration accuracy and completeness

---

### Non-Functional Requirements

#### Performance
- **NFR1:** Web application pages shall load within 3 seconds on standard broadband connections
- **NFR2:** API responses shall complete within 500ms for standard operations
- **NFR3:** Real-time sync latency shall not exceed 5 seconds under normal operating conditions
- **NFR4:** The system shall support 10 concurrent nutritionists with 100 clients each (1,000 total users) without performance degradation

#### Availability & Reliability
- **NFR5:** The system shall maintain 99.5% uptime availability
- **NFR6:** Client data shall be retained indefinitely with configurable archival policies

#### Security & Privacy
- **NFR7:** All data shall be encrypted in transit using TLS 1.3
- **NFR8:** All sensitive data shall be encrypted at rest using AES-256
- **NFR9:** The system shall maintain audit logs tracking all data access and modifications
- **NFR10:** The system shall comply with Israeli Privacy Protection Law (5741-1981)
- **NFR11:** The system shall support GDPR-aware operations including data export and deletion requests

#### Internationalization
- **NFR12:** The system shall support Hebrew language with proper RTL (right-to-left) layout throughout all interfaces
- **NFR13:** The system shall support English language as a secondary option
- **NFR14:** All UI components shall properly handle bidirectional text rendering

#### Compatibility
- **NFR15:** The web application shall support Chrome, Safari, Firefox, and Edge (latest 2 versions)
- **NFR16:** The mobile application shall support iOS 14+ and Android 10+

#### Usability
- **NFR17:** Client mobile app daily check-in flow shall be completable in under 30 seconds
- **NFR18:** PDF report generation shall complete within 2 minutes for standard reports

---

## 3. User Interface Design Goals

### Overall UX Vision

**NutriPro embraces a "dual simplicity" philosophy:** sophisticated power for professionals, radical simplicity for clients.

**Nutritionist Web App:** A clean, modern practice management interface that surfaces the right information at the right time. Dense data (nutritional values, blood tests, body composition) should be accessible but not overwhelming. The experience should feel like a well-organized digital workspace—professional, efficient, and confidence-inspiring. Hebrew RTL is native, not an afterthought.

**Client Mobile App:** One-tap everything. The app should feel almost "too simple" at first glance—a checklist, not a food diary. No cognitive load, no decisions beyond "did I do this?" The interface celebrates progress with subtle positive feedback (streaks, checkmarks, trends going the right direction). Opening the app should take less mental energy than checking a text message.

**Unifying Aesthetic:** Both apps share a cohesive visual language—clean typography, generous whitespace, a calming but professional color palette. The nutritionist and client should feel they're using two sides of the same system.

---

### Key Interaction Paradigms

| Paradigm | Application |
|----------|-------------|
| **One-Tap Actions** | Client meal/workout check-offs, quick-add for common actions |
| **Progressive Disclosure** | Complex nutritionist features (blood tests, body comp) revealed on demand, not cluttering primary views |
| **Real-Time Feedback** | Nutritional calculations update instantly as foods are added; adherence scores reflect latest client activity |
| **Card-Based Layouts** | Client cards on nutritionist dashboard; meal cards on client app—scannable, tappable, information-dense but not cluttered |
| **Contextual Toolbars** | Actions relevant to current context (editing a meal plan shows meal-specific tools) |
| **Search-First for Dictionary** | Foods, exercises, medications accessed primarily through search rather than hierarchical navigation |
| **Inline Editing** | Edit values in place where possible (click to edit weight, reps) rather than modal dialogs |

---

### Core Screens and Views

#### Nutritionist Web App

| Screen | Purpose |
|--------|---------|
| **Dashboard** | At-a-glance view of practice: recent client activity, adherence alerts, upcoming appointments, quick-access to active clients |
| **Client List** | Searchable/filterable list of all clients with status indicators, last activity, adherence scores |
| **Client Profile** | Comprehensive client view with tabs/sections: Personal Info, Medical History, Current Plans, Tracking Data, Blood Tests, Body Composition, Appointments |
| **Meal Menu Builder** | Create/edit meal plans with food search, drag-and-drop organization, real-time nutritional calculations sidebar |
| **Workout Plan Builder** | Create/edit workout programs with exercise search, sets/reps/weight configuration |
| **Blood Test Entry** | Record lab results with parameter selection, value entry, reference range display |
| **Body Composition Calculator** | Skinfold measurement entry with automatic Jackson-Pollock calculations |
| **Dictionary Management** | CRUD interfaces for Foods, Exercises, Medications, Supplements, Diseases with bulk import |
| **Reports Generator** | Select client, report type, date range; preview and export PDF |
| **Settings/Admin** | Configuration tables, profile settings, practice information |

#### Client Mobile App

| Screen | Purpose |
|--------|---------|
| **Today View (Home)** | Daily checklist: meals to complete, workout to complete, daily summary stats |
| **Meal Detail** | Tap a meal to see foods included, mark as completed |
| **Workout Detail** | Tap workout to see exercises, log weight/reps/sets for each, mark as completed |
| **Progress Dashboard** | Adherence % (this week), weight trend chart, streak counter, weekly summary |
| **Log Weight/Measurements** | Quick entry form for weigh-in data |
| **Appointments** | List of upcoming meetings with nutritionist |
| **Settings** | Notification preferences, language toggle, profile basics |

---

### Accessibility

**Target: WCAG AA Compliance**

| Requirement | Implementation |
|-------------|----------------|
| **Color Contrast** | Minimum 4.5:1 for normal text, 3:1 for large text |
| **Keyboard Navigation** | Full keyboard accessibility for web app |
| **Screen Reader Support** | Proper ARIA labels, semantic HTML, logical heading hierarchy |
| **Touch Targets** | Minimum 44x44pt touch targets on mobile |
| **Text Scaling** | Support system font size preferences up to 200% |
| **Motion** | Respect reduced-motion preferences; no essential information conveyed only through animation |

---

### Branding

**Visual Direction:** Modern, clean, health-oriented but not clinical. Approachable professionalism.

| Element | Guidance |
|---------|----------|
| **Color Palette** | Primary: Calming green or teal (health/wellness association). Secondary: Warm neutral. Accent: Energetic but not aggressive (coral, amber). Avoid: Clinical white/blue healthcare aesthetic |
| **Typography** | Clean sans-serif that renders well in both Hebrew and English. Excellent RTL support required. Consider: Heebo (Hebrew-optimized), Assistant, or similar |
| **Iconography** | Simple, recognizable line icons. Consistent stroke weight. Food/fitness imagery should feel fresh, not clip-art |
| **Imagery** | Minimal use of stock photos. Prefer abstract shapes, gradients, or illustration if decoration needed |
| **Tone** | Encouraging, supportive, professional. Celebrate wins ("🔥 12-day streak!") without being patronizing |

---

### Target Devices and Platforms

| Platform | Specification | Priority |
|----------|---------------|----------|
| **Web (Nutritionist)** | Desktop-first responsive design; must work well on tablets | Primary |
| **iOS (Client)** | Native app, iOS 14+ | Primary |
| **Android (Client)** | Native app, Android 10+ | Primary |
| **Web (Client)** | Not required for MVP | Out of Scope |
| **Tablet (Client)** | Mobile app should scale acceptably on tablets but not optimized | Secondary |

---

## 4. Technical Assumptions

### Repository Structure: Monorepo

| Decision | Rationale |
|----------|-----------|
| **Monorepo (Turborepo or Nx)** | Enables code sharing between web and mobile (shared types, validation, utilities). Small team benefits from unified tooling, single PR workflow, and atomic changes across packages. |

**Package Structure:**
```
/apps
  /web          # Nutritionist web application
  /mobile       # Client mobile application (React Native)
  /api          # Backend API server
/packages
  /shared       # Shared types, validation schemas, utilities
  /ui           # Shared UI components (if applicable)
```

---

### Service Architecture: Monolith-First

| Decision | Rationale |
|----------|-----------|
| **Monolith for MVP** | Simpler deployment, debugging, and iteration for a small team. Avoids distributed system complexity (network calls, service discovery, distributed transactions) when not yet needed. |
| **Modular Internal Structure** | Clear domain boundaries (Clients, Plans, Tracking, Dictionary, Auth) enable future service extraction if scale requires. |

**Domain Modules:**
- **Auth** — Authentication, authorization, session management
- **Users** — Nutritionist and client profiles
- **Clients** — Client management, medical info, preferences
- **Dictionary** — Foods, exercises, medications, supplements, diseases, config tables
- **Plans** — Meal plans, workout plans, assignments
- **Tracking** — Check-ins, measurements, blood tests, body composition
- **Reports** — PDF generation, data exports
- **Sync** — Real-time event distribution

---

### Testing Requirements: Unit + Integration

| Layer | Testing Approach |
|-------|------------------|
| **Unit Tests** | All business logic, calculations (nutritional totals, Jackson-Pollock formulas, RMR), and utilities |
| **Integration Tests** | API endpoints, database operations, authentication flows |
| **E2E Tests** | Critical user journeys (login, create meal plan, client check-in, sync verification) — limited scope for MVP |
| **Manual Testing** | UI/UX validation, RTL rendering, PDF output review, real-device mobile testing |

**Coverage Targets (MVP):**
- Unit: 80%+ for business logic
- Integration: All API endpoints covered
- E2E: Core happy paths only

---

### Technology Stack Preferences

#### Frontend (Web)

| Technology | Preference | Rationale |
|------------|------------|-----------|
| **Framework** | Next.js (React) | Modern, component-based, excellent RTL support, strong ecosystem, good DX |
| **Styling** | Tailwind CSS | Utility-first enables rapid iteration, RTL support via `dir="rtl"`, small bundle size |
| **State Management** | React Query + Zustand | React Query for server state, Zustand for minimal client state |
| **Forms** | React Hook Form + Zod | Type-safe validation, shared schemas with backend |

#### Frontend (Mobile)

| Technology | Preference | Rationale |
|------------|------------|-----------|
| **Framework** | React Native | Code sharing with web team, single codebase for iOS/Android, sufficient performance for simple UI |
| **Navigation** | React Navigation | Standard for React Native, well-documented |
| **State/Data** | React Query | Consistent with web, handles caching and sync |

#### Backend

| Technology | Preference | Rationale |
|------------|------------|-----------|
| **Runtime** | Node.js **OR Python** | Both are strong choices; decision should align with team expertise |
| **Framework** | Fastify/Express (Node) **OR FastAPI (Python)** | Both offer excellent async support and modern DX |
| **Language** | TypeScript **OR Python 3.11+** | See trade-off analysis below |
| **ORM** | Prisma (Node) **OR SQLAlchemy/SQLModel (Python)** | Both provide type-safe database access |

**Language Trade-off Analysis:**

| Factor | TypeScript/Node | Python/FastAPI |
|--------|-----------------|----------------|
| **Full-stack type sharing** | ✅ Excellent | ⚠️ Limited (requires OpenAPI codegen) |
| **Data processing & calculations** | ⚠️ Adequate | ✅ Excellent (NumPy/Pandas) |
| **Data migration (legacy import)** | ⚠️ Workable | ✅ Excellent (Pandas ideal) |
| **Real-time (WebSocket)** | ✅ Native strength | ✅ Good |
| **Future AI/ML features** | ⚠️ Would require Python | ✅ Natural fit |
| **Team context-switching** | ✅ Single language | ⚠️ Two languages |

**Recommendation:** Both stacks are production-ready. Choose based on team expertise.

#### Database

| Technology | Preference | Rationale |
|------------|------------|-----------|
| **Primary Database** | PostgreSQL | Relational model fits domain well, strong JSON support for flexible fields, proven at scale |
| **Hosting** | Supabase or Railway | Managed Postgres, cost-effective for MVP, easy scaling |

#### Real-Time

| Technology | Preference | Rationale |
|------------|------------|-----------|
| **Approach** | WebSockets (Socket.io) or Supabase Realtime | Required for bi-directional sync |
| **Fallback** | Polling | If WebSocket complexity is prohibitive, start with polling and upgrade |

#### Infrastructure & Hosting

| Component | Preference | Rationale |
|-----------|------------|-----------|
| **Web Frontend** | Vercel | Excellent Next.js support, easy deployment |
| **API Backend** | Railway, Render, or Fly.io | Cost-effective, easy deployment |
| **Database** | Supabase or Railway Postgres | Managed, backups included |
| **File Storage** | Supabase Storage or S3 | PDF exports, future photo storage |
| **Push Notifications** | Firebase Cloud Messaging (FCM) | Works for both iOS and Android |
| **Email** | Resend or SendGrid | Transactional emails |

---

### Additional Technical Assumptions

- **All timestamps stored in UTC** — Converted to local timezone (Israel Standard Time) in UI
- **Hebrew/RTL from day one** — All components, libraries, and layouts must support RTL
- **Shared validation schemas** — Zod schemas shared between frontend and backend for consistency
- **PDF generation server-side** — Must render Hebrew correctly
- **No offline mobile mode for MVP** — Deferred to Phase 2
- **Single-tenant for MVP** — Multi-tenancy considered but not implemented
- **Client belongs to one nutritionist** — No client sharing for MVP
- **Dictionary is shared** — Not per-nutritionist customization for MVP

---

## 5. Epic List

### Proposed Epic Structure

| # | Epic | Goal Statement |
|---|------|----------------|
| **1** | **Foundation & Dictionary** | Establish project infrastructure, authentication, and the complete master data system with bulk import capability |
| **2** | **Client Management** | Enable nutritionists to create and manage client profiles with medical history, questionnaires, and preferences |
| **3** | **Meal Planning & Nutrition** | Deliver the complete meal menu builder with real-time nutritional calculations, client assignment, and PDF export |
| **4** | **Workout Planning & Clinical Tracking** | Provide workout plan creation plus clinical features: blood test tracking, body composition calculator, and measurements |
| **5** | **Client Mobile App** | Launch the client-facing mobile app with meal/workout checklists, exercise logging, progress dashboard, and push notifications |
| **6** | **Real-Time Sync & Dashboard** | Implement bi-directional sync between web and mobile, plus the nutritionist dashboard with live adherence scores and alerts |
| **7** | **Data Migration & Launch** | Migrate partner's legacy data, validate completeness, and prepare for production launch |

### Epic Dependencies

```
Epic 1: Foundation & Dictionary
    ↓
Epic 2: Client Management
    ↓
Epic 3: Meal Planning ←──────────┐
    ↓                            │
Epic 4: Workout & Clinical  ─────┤ (can parallelize 3 & 4 after Epic 2)
    ↓                            │
Epic 5: Client Mobile App ───────┘
    ↓
Epic 6: Real-Time Sync & Dashboard
    ↓
Epic 7: Data Migration & Launch
```

### Risk Mitigations Built Into Epic Structure

1. **Epic 1:** WebSocket proof-of-concept spike to validate sync infrastructure early
2. **Epic 2:** Client search/dashboard as "quick win" for immediate value
3. **Epic 3-4:** Parallel mobile design track for head start
4. **Epic 4:** Pre-authorized split into 4a/4b if velocity shows >30% overrun
5. **Epic 6:** Degraded mode requirement—apps work with polling if sync fails
6. **Throughout:** Migration milestones at Epics 1, 2, 4, 7

---

## 6. Epic Details

### Epic 1: Foundation & Dictionary

**Goal:** Establish the project infrastructure, authentication system, and complete master data management with bulk import capability.

**Stories:**

#### Story 1.1: Project Setup & Infrastructure
**As a** developer, **I want** the project repository, development environment, and CI/CD pipeline configured, **so that** the team can begin development with consistent tooling.

**Acceptance Criteria:**
1. Monorepo structure created with `/apps/web`, `/apps/mobile`, `/apps/api`, `/packages/shared`
2. TypeScript configured with strict mode
3. ESLint and Prettier configured
4. Git hooks (Husky) for pre-commit linting
5. CI pipeline runs linting, type checking, tests on every PR
6. README documents local development setup
7. Environment variable structure defined

#### Story 1.2: Database Schema & ORM Setup
**As a** developer, **I want** PostgreSQL provisioned with core schema and ORM configured, **so that** the application can persist data with type safety.

**Acceptance Criteria:**
1. PostgreSQL database provisioned
2. ORM configured with database connection
3. Initial schema migrations for Users, Nutritionists, Clients, Dictionary entities
4. Seed script creates test data
5. Migration workflow documented
6. Connection pooling configured
7. Tables support Hebrew content (UTF-8)

#### Story 1.3: Authentication System
**As a** user, **I want** to securely log in with email and password, **so that** my data is protected.

**Acceptance Criteria:**
1. Registration endpoint with hashed password
2. Login returns JWT access token (15min) and refresh token (7 day)
3. Refresh token endpoint issues new access token
4. Password reset flow with email
5. Role field distinguishes nutritionist/client
6. Protected routes reject invalid JWT
7. Rate limiting on auth endpoints

#### Story 1.4: Web App Shell with RTL Support
**As a** nutritionist, **I want** a web application with proper Hebrew/RTL layout, **so that** I can use the system in my native language.

**Acceptance Criteria:**
1. Next.js application scaffolded
2. Tailwind CSS with RTL support
3. Language toggle (Hebrew/English) with persistence
4. Layout with navigation sidebar, header, main content
5. Login/logout flow integrated
6. Protected routes redirect to login
7. Works in Chrome, Safari, Firefox, Edge
8. Hebrew text displays correctly

#### Story 1.5: Foods Dictionary CRUD
**As a** nutritionist, **I want** to create, view, edit, and delete foods, **so that** I can manage the food database.

**Acceptance Criteria:**
1. Foods list with search and filter by category
2. Food detail shows all fields (name, category, serving, calories, protein, carbs, fat, fiber, 20+ micronutrients)
3. Create/edit/delete functionality with validation
4. Pagination handles 5,000+ foods
5. Search works on Hebrew and English names
6. All UI text available in Hebrew and English

#### Story 1.6: Foods Bulk Import
**As a** nutritionist, **I want** to import foods from CSV/Excel, **so that** I can migrate my existing database.

**Acceptance Criteria:**
1. Import accepts CSV or Excel upload
2. Preview of first 10 rows
3. Column mapping UI
4. Validation report before import
5. Background processing for large files
6. Progress indicator
7. Summary report with success/failure counts
8. Failed rows exportable for correction
9. Imports 5,000+ foods within 5 minutes

#### Story 1.7: Exercises Dictionary CRUD & Import
**As a** nutritionist, **I want** to manage exercises with CRUD and bulk import, **so that** I can build workout plans.

**Acceptance Criteria:**
1. Exercises list with search and filter
2. Fields: name, muscle group, equipment, type, difficulty, instructions
3. CRUD functionality with validation
4. Bulk import from CSV/Excel
5. Imports 500+ exercises

#### Story 1.8: Medications, Supplements & Diseases CRUD
**As a** nutritionist, **I want** to manage medications, supplements, and diseases, **so that** I can track client medical information.

**Acceptance Criteria:**
1. Medications: name, category, interactions, notes; CRUD + search
2. Supplements: name, type, dosage, interactions; CRUD + search
3. Diseases: name, dietary considerations, contraindications; CRUD + search
4. Each supports bulk CSV import

#### Story 1.9: Configuration Tables Management
**As an** admin, **I want** to manage configuration tables, **so that** the system uses correct reference values.

**Acceptance Criteria:**
1. Admin section lists all config tables
2. Blood Test Parameters with reference ranges by age/gender
3. Meal Types, Client Types, Activity Coefficients, RMR Coefficients, Fat % Ranges
4. Add/edit/delete operations
5. Changes take effect immediately

#### Story 1.10: WebSocket Proof-of-Concept Spike
**As a** developer, **I want** to validate WebSocket infrastructure, **so that** we surface issues early.

**Acceptance Criteria:**
1. WebSocket server endpoint established
2. Client can connect, send, receive messages
3. Works through production infrastructure
4. Basic authentication required
5. Document findings
6. Timeboxed to 1-2 days

---

### Epic 2: Client Management

**Goal:** Enable nutritionists to create and manage comprehensive client profiles including personal information, medical history, medical questionnaires, and food preferences.

**Stories:**

#### Story 2.1: Client List & Search Dashboard
**As a** nutritionist, **I want** to see all my clients in a searchable list with status indicators, **so that** I can quickly find clients and see my practice at a glance.

**Acceptance Criteria:**
1. Client list shows all clients for logged-in nutritionist
2. Each row: name, status, client type, last activity, phone
3. Search by name, phone, email
4. Filter by status, client type
5. Sort by name, last activity, date added
6. Dashboard summary: total clients, active, seen this week
7. Click navigates to profile
8. "Add Client" button
9. Handles 100+ clients
10. Empty state message

#### Story 2.2: Client Profile - Personal Information
**As a** nutritionist, **I want** to create and edit client personal information, **so that** I have complete contact details.

**Acceptance Criteria:**
1. Form: first name, last name, email, phone, DOB, gender, address, city, ID
2. Client type dropdown
3. Status: active, inactive, archived
4. Notes field
5. Profile photo upload (optional)
6. Hebrew text support
7. Validation for required fields
8. Save creates client linked to nutritionist
9. Edit mode for updates
10. Profile page shows personal info section

#### Story 2.3: Client Profile - Medical Information
**As a** nutritionist, **I want** to record client medical information, **so that** I can make informed recommendations.

**Acceptance Criteria:**
1. Medical info section with subsections
2. Conditions: multi-select from dictionary + free-text
3. Medications: multi-select with dosage + free-text
4. Supplements: multi-select with dosage + free-text
5. Allergies: free-text field
6. Medical Notes: rich text area
7. Each subsection independently editable
8. Interaction warnings displayed
9. Organized, scannable format

#### Story 2.4: Client Profile - Food Preferences
**As a** nutritionist, **I want** to record client food preferences, **so that** I can create appropriate meal plans.

**Acceptance Criteria:**
1. Food preferences section
2. Dietary restrictions checkboxes + custom
3. Disliked foods: multi-select + free-text
4. Preferred foods: multi-select + free-text
5. Eating habits notes
6. Goal dropdown
7. All saveable and displayed

#### Story 2.5: Medical Questionnaire Template
**As a** nutritionist, **I want** to define a structured questionnaire template, **so that** I can gather health intake systematically.

**Acceptance Criteria:**
1. Template editor in admin section
2. Default template pre-populated
3. Questions: text, response type
4. Reorder via drag-and-drop
5. Add/edit/deactivate questions
6. "Treated" checkbox option
7. Single template for MVP
8. Changes don't affect completed questionnaires

#### Story 2.6: Client Medical Questionnaire Entry
**As a** nutritionist, **I want** to fill out the questionnaire for a client, **so that** I have structured intake data.

**Acceptance Criteria:**
1. Questionnaire section on profile
2. All questions from active template
3. Yes/No toggle, Notes, Treated checkbox
4. Auto-saves
5. Completion indicator
6. Read-only summary mode
7. Date recorded
8. Reset option for annual review
9. Data persists if template changes

#### Story 2.7: Client Profile - Unified View
**As a** nutritionist, **I want** to see all client information in organized sections, **so that** I can quickly access any detail.

**Acceptance Criteria:**
1. Tabbed/accordion sections
2. Header: name, photo, status, quick stats
3. Quick actions: Edit, Archive, Print
4. Loads within 2 seconds
5. RTL layout
6. Responsive on tablet

#### Story 2.8: Client Bulk Import (Migration Dry-Run)
**As a** nutritionist, **I want** to import clients from CSV/Excel, **so that** I can migrate my database.

**Acceptance Criteria:**
1. Import accepts CSV/Excel
2. Column mapping for client fields
3. Duplicate detection
4. Preview before import
5. Creates clients linked to nutritionist
6. Summary report
7. Partner validates with sample data
8. Document unmapped fields

#### Story 2.9: Client Archive & Data Management
**As a** nutritionist, **I want** to archive inactive clients and manage data lifecycle, **so that** my list stays manageable.

**Acceptance Criteria:**
1. Archive moves to archived status
2. Archived hidden from default list
3. Data retained (not deleted)
4. Restore action available
5. Permanent delete with confirmation
6. Export client data as JSON/CSV
7. Audit log for actions

---

### Epic 3: Meal Planning & Nutrition

**Goal:** Deliver the complete meal menu builder with real-time nutritional calculations, client assignment, and PDF export.

**Stories:**

#### Story 3.1: Meal Plan Data Model & API
**As a** developer, **I want** the meal plan data model and API established, **so that** the meal builder can manage plans.

**Acceptance Criteria:**
1. Schema: MealPlan, MealPlanDay, Meal, MealFood
2. MealPlan: client_id, name, dates, status, notes
3. API: CRUD with nested creation
4. Returns calculated nutrition (computed)
5. Row-level security enforced
6. Soft delete

#### Story 3.2: Meal Plan List & Management
**As a** nutritionist, **I want** to see all meal plans for a client, **so that** I can track current and historical plans.

**Acceptance Criteria:**
1. Meal Plans tab on profile
2. List: name, dates, status, daily calories
3. Status badges
4. Filter and sort
5. Create/edit/duplicate/archive actions
6. One active plan per client

#### Story 3.3: Meal Builder - Plan Structure
**As a** nutritionist, **I want** to create a meal plan with daily structure, **so that** I can organize meals across days.

**Acceptance Criteria:**
1. Builder with metadata header
2. Daily/Weekly view toggle
3. Meal slots from config
4. Droppable zones for foods
5. Generic or specific dates
6. Auto-save

#### Story 3.4: Meal Builder - Food Search & Selection
**As a** nutritionist, **I want** to search and add foods to meals, **so that** I can build meals quickly.

**Acceptance Criteria:**
1. Food search panel
2. Search by Hebrew/English name
3. Filter by category
4. Click/drag to add
5. Quantity and unit prompt
6. "Is Primary" checkbox
7. Recently used foods
8. Favorites section
9. <500ms search response

#### Story 3.5: Meal Builder - Real-Time Nutrition Calculations
**As a** nutritionist, **I want** real-time nutritional totals, **so that** I can ensure plans meet goals.

**Acceptance Criteria:**
1. Nutrition summary panel
2. Per-meal totals: calories, protein, carbs, fat, fiber
3. Per-day totals with percentage breakdown
4. Plan averages
5. Updates <200ms
6. Micronutrient detail view
7. Target comparison with color coding
8. Matches legacy formulas

#### Story 3.6: Meal Builder - Edit Foods & Quantities
**As a** nutritionist, **I want** to edit quantities and remove foods, **so that** I can refine plans precisely.

**Acceptance Criteria:**
1. Each food shows: name, quantity, macros
2. Edit: quantity, unit, Is Primary
3. Decimal quantities supported
4. Remove with undo
5. Reorder via drag-and-drop
6. Move between meals
7. Duplicate to another meal

#### Story 3.7: Meal Plan Assignment & Activation
**As a** nutritionist, **I want** to activate a meal plan, **so that** clients see their plan in the app.

**Acceptance Criteria:**
1. Activate button
2. Archives previous active plan
3. Date range determines mobile display
4. One active plan per client
5. Confirmation dialog
6. Deactivate option
7. Active indicator in list

#### Story 3.8: Meal Plan PDF Export
**As a** nutritionist, **I want** to export meal plans as PDF, **so that** clients can print or receive by email.

**Acceptance Criteria:**
1. Export PDF button
2. Includes client/nutritionist names, plan info
3. Daily meals in table format
4. Shows foods with macros
5. Daily totals row
6. Hebrew RTL correct
7. Fits A4/Letter
8. <10 seconds generation
9. Download or email option
10. Notes section included

#### Story 3.9: Meal Plan Templates (Copy From Existing)
**As a** nutritionist, **I want** to create plans by copying existing ones, **so that** I can reuse structures.

**Acceptance Criteria:**
1. Duplicate action available
2. Creates copy with "(Copy)" suffix
3. Same or different client
4. All content copied
5. New plan in Draft status
6. Original unchanged

#### Story 3.10: Mobile App Scaffolding (Parallel Track)
**As a** developer, **I want** the React Native app scaffolded, **so that** Epic 5 can start immediately.

**Acceptance Criteria:**
1. React Native project in `/apps/mobile`
2. Tab navigator with placeholder screens
3. RTL configured and tested
4. Auth flow integrated
5. API client configured
6. Basic UI components started
7. Builds for iOS and Android
8. Design tokens aligned with web

---

### Epic 4: Workout Planning & Clinical Tracking

**Goal:** Provide workout plan creation plus clinical features: blood test tracking, body composition calculator, and measurements.

**Split Authorization:** Pre-authorized to split into 4a/4b if velocity shows >30% overrun.

**Stories:**

#### Story 4.1: Workout Plan Data Model & API
Schema and API for WorkoutPlan, WorkoutDay, WorkoutExercise with CRUD operations.

#### Story 4.2: Workout Plan List & Management
Workout Plans tab on profile with list, status, and management actions.

#### Story 4.3: Workout Builder - Program Structure
Create workout programs with named training days, program type, and day organization.

#### Story 4.4: Workout Builder - Exercise Selection & Configuration
Add exercises with sets, reps, weight targets, rest periods, and notes.

#### Story 4.5: Workout Plan Activation & PDF Export
Activate plans for mobile visibility and export as printable PDF.

#### Story 4.6: Weight & Body Measurements Tracking
Record weight, height, circumferences with history table and BMI calculation.

#### Story 4.7: Weight & Measurements Trend Graphs
Line charts for weight and measurements over time with date range selection.

#### Story 4.8: Blood Test Recording
Record blood test results with 50+ parameters, reference ranges, and color-coded values.

#### Story 4.9: Blood Test Trends & Comparison
Trend charts per parameter, comparison view, and improvement indicators.

#### Story 4.10: Body Composition Calculator (Skinfold)
7-site skinfold entry with Jackson-Pollock formulas calculating body fat %, FFMI, etc.

#### Story 4.11: Body Composition History & Trends
History table and trend charts for body composition metrics over time.

#### Story 4.12: Vitals Tracking (Blood Pressure, Grip Strength)
Record and track blood pressure and hand grip strength with norms display.

#### Story 4.13: Clinical Data Import Dry-Run (Migration)
Import historical tracking data from legacy system with validation.

---

### Epic 5: Client Mobile App

**Goal:** Launch the complete client-facing mobile application with one-tap tracking, exercise logging, progress dashboard, and push notifications.

**Stories:**

#### Story 5.1: Client Authentication & Onboarding
Login flow with JWT, brief onboarding screens, language selection.

#### Story 5.2: Today View - Daily Overview
Home screen showing daily meals, workout, streak, and summary stats.

#### Story 5.3: Meal Check-Off
One-tap meal completion with optimistic UI and sync.

#### Story 5.4: Workout Check-Off & Exercise Logging
Mark workouts complete with actual weight/reps/sets logging per exercise.

#### Story 5.5: Exercise Progress & Personal Records
Exercise history, PR badges, celebration animations for new records.

#### Story 5.6: Weight & Measurement Logging
Quick weight entry with optional measurements, synced to nutritionist.

#### Story 5.7: Progress Dashboard
Adherence %, weight trend chart, streak counter, weekly summary.

#### Story 5.8: Appointments View
List of upcoming appointments with add-to-calendar option.

#### Story 5.9: Push Notifications
FCM integration with configurable meal, workout, weigh-in, and appointment reminders.

#### Story 5.10: Client Settings & Profile
Profile view, language toggle, notification settings, logout.

#### Story 5.11: Offline Resilience (Basic)
Cache today's data, queue check-offs offline, sync when connected.

---

### Epic 6: Real-Time Sync & Dashboard

**Goal:** Implement bi-directional sync and the nutritionist dashboard with live adherence and alerts.

**Stories:**

#### Story 6.1: WebSocket Infrastructure Setup
WebSocket server with JWT auth, heartbeat, reconnection, graceful degradation.

#### Story 6.2: Event Publishing System
Define and publish events for plan updates, check-ins, tracking entries.

#### Story 6.3: Web App Real-Time Updates
Receive events on web, update adherence scores and activity feed live.

#### Story 6.4: Mobile App Real-Time Updates
Receive plan updates on mobile, refresh views automatically.

#### Story 6.5: Nutritionist Dashboard - Overview
Summary cards, real-time activity feed, practice health at a glance.

#### Story 6.6: Nutritionist Dashboard - Adherence Scores
Client list with adherence %, color coding, at-risk filtering.

#### Story 6.7: Client Alerts & Notifications
Configurable alerts for inactive clients, dropped adherence, missed activities.

#### Story 6.8: Sync Conflict Resolution
Last-write-wins with appropriate source-of-truth rules, no data loss.

#### Story 6.9: Sync Performance & Reliability
Meet 5-second latency target, load testing, monitoring.

#### Story 6.10: Degraded Mode & Fallbacks
Polling fallback, manual refresh, all features work without WebSocket.

---

### Epic 7: Data Migration & Launch

**Goal:** Complete legacy data migration, validate accuracy, and launch to production.

**Stories:**

#### Story 7.1: Legacy Data Export & Analysis
Extract and analyze complete legacy dataset, create field mapping document.

#### Story 7.2: Master Data Migration (Final)
Import all 5,000+ foods, 500+ exercises, medications, supplements, diseases.

#### Story 7.3: Client Data Migration (Final)
Import all client profiles, medical info, preferences.

#### Story 7.4: Meal Plan History Migration
Import historical meal plans with structure and nutritional data.

#### Story 7.5: Workout Plan History Migration
Import historical workout plans with exercises and configurations.

#### Story 7.6: Clinical Data Migration
Import weight history, blood tests, body composition, vitals.

#### Story 7.7: Migration Validation Suite
Automated validation: counts, integrity, required fields, business rules.

#### Story 7.8: Performance Optimization
Index optimization, query performance, load testing with production data.

#### Story 7.9: Security Audit & Hardening
Auth review, authorization, encryption, audit logging, privacy compliance.

#### Story 7.10: App Store Preparation (Mobile)
TestFlight/Play Store submission, listings, privacy policy, approval.

#### Story 7.11: Launch Preparation & Documentation
User guides, FAQ, support channel, monitoring, rollback plan.

#### Story 7.12: Partner Sign-Off & Go-Live
End-to-end testing, data verification, formal sign-off, production switch.

---

## 7. Checklist Results Report

```
PRD VALIDATION COMPLETE
=======================
Date: December 30, 2025
Validator: PM Agent (John)

Overall Score: 95%
Status: READY FOR ARCHITECT

Categories Passed: 9/9
- Problem Definition: PASS (98%)
- MVP Scope: PASS (95%)
- User Experience: PASS (92%)
- Functional Requirements: PASS (96%)
- Non-Functional Requirements: PASS (94%)
- Epic & Story Structure: PASS (98%)
- Technical Guidance: PASS (90%)
- Cross-Functional: PASS (92%)
- Clarity & Communication: PASS (94%)

Blockers: 0
High Issues: 2
  - Legacy data format unknown (partner action required)
  - Hebrew PDF rendering validation needed

Medium Issues: 3
  - Client invitation flow not specified
  - Password reset templates not detailed
  - Hebrew font selection not finalized

Recommendation: PROCEED TO ARCHITECTURE
```

---

## 8. Next Steps

### UX Expert Prompt

> **To: UX Expert (Sally)**
>
> The NutriPro PRD is complete and validated. Please create a comprehensive Front-End Specification using the `front-end-spec-tmpl` template.
>
> **Key inputs to review:**
> - `docs/prd.md` — Full PRD with UI Design Goals section
> - `docs/brief.md` — Project Brief with user personas
>
> **Critical UX considerations:**
> - Hebrew-first with proper RTL layout
> - "Dual simplicity" philosophy
> - One-tap interactions for client mobile
> - WCAG AA accessibility
>
> **Deliverable:** `docs/front-end-spec.md`

---

### Architect Prompt

> **To: Architect (Winston)**
>
> The NutriPro PRD is complete and validated (95% score). Please create a comprehensive Full-Stack Architecture document using the `fullstack-architecture-tmpl` template.
>
> **Key inputs to review:**
> - `docs/prd.md` — Full PRD with Technical Assumptions
> - `docs/brief.md` — Project Brief
> - `docs/front-end-spec.md` — UX specification (when available)
>
> **Critical decisions needed:**
> 1. Backend: TypeScript vs Python
> 2. Real-time: WebSocket vs Supabase Realtime
> 3. Mobile: Expo vs bare workflow
> 4. Database: Supabase vs Railway
> 5. PDF: Library for Hebrew RTL
>
> **High-risk areas:**
> - Real-time sync (Epic 6)
> - Data migration (Epic 7)
> - Hebrew/RTL consistency
> - Jackson-Pollock formula accuracy
>
> **Deliverable:** `docs/architecture.md`

---

## Appendix A: Document References

- `docs/brief.md` — Project Brief (input document)
- `docs/brainstorming-session-results.md` — Feature brainstorming
- `NutriPro_System_Documentation.pdf` — Legacy system analysis

---

## Appendix B: Glossary

| Term | Definition |
|------|------------|
| **RTL** | Right-to-left text direction (Hebrew) |
| **FFMI** | Fat-Free Mass Index |
| **Jackson-Pollock** | Body composition formula using skinfold measurements |
| **RMR** | Resting Metabolic Rate |
| **WCAG AA** | Web Content Accessibility Guidelines Level AA |

---

*Document created using the BMAD-METHOD™ framework*

