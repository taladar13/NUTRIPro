# Project Brief: NutriPro

**Version:** 1.0  
**Date:** December 29, 2025  
**Author:** Business Analyst (Mary)  
**Status:** Ready for PRD

---

## Executive Summary

**NutriPro** is a bilingual (Hebrew/English) web and mobile platform designed to modernize nutritional counseling practices. The system replaces an existing 10+ year desktop application with two purpose-built interfaces:

1. **Nutritionist Web App** — A comprehensive practice management tool featuring client records, meal menu builder with real-time macro/micronutrient calculations, workout plan creator, blood test tracking, body composition analysis (including skinfold calculations), medical questionnaire management, and a rich dictionary of foods, exercises, medications, supplements, and conditions.

2. **Client Mobile App** — A radically simple daily tracker where clients check off meals and workouts with one tap, log exercise progress (weight/reps/sets), view their adherence and trends, and stay synced with their nutritionist in real-time.

**Primary Problem:** The current NutriPro desktop system—while clinically comprehensive—is trapped on Windows machines with no remote access, no client self-service, and no way to maintain engagement between appointments. Nutritionists lose visibility into client behavior; clients forget their plans or lack motivation without feedback loops. Competing apps (MyFitnessPal, Cronometer) are consumer-focused and lack the clinical depth professionals require.

**Target Market:**
- **Primary:** Independent nutritionists and dietitians in Israel (500+ practitioners), initially onboarding 1 power user (development partner) with expansion to 10-50 practitioners in Year 1
- **Secondary:** Their clients (estimated 20-100 active clients per practitioner)

**Key Value Proposition:**
- For nutritionists: "Your entire practice in the cloud—every feature you rely on, accessible anywhere, with real-time client visibility."
- For clients: "One tap. That's it. Check your meal, check your workout, see your progress."

**Unique Differentiators:**
- Full clinical toolset (blood tests, body composition, medical history) vs. consumer apps
- Bi-directional real-time sync between professional and client apps
- Hebrew-first with RTL support (underserved market)
- Migration path from existing NutriPro desktop data

While platforms like Practice Better and Nutrium serve English-speaking markets, NutriPro is purpose-built for Hebrew-speaking practitioners with clinical depth that consumer apps lack.

---

## Problem Statement

### Current State & Pain Points

**For Nutritionists:**
The existing NutriPro system is a comprehensive desktop application built over 10+ years, running on Windows machines with a Microsoft Access-style interface. While feature-rich, it suffers from critical limitations:

- **Desktop-bound:** Practitioners can only access client data from one physical computer. No remote access, no tablet use during consultations, no working from home.
- **Zero client visibility between visits:** Once a client leaves the office, the nutritionist has no insight into adherence until the next appointment—often weeks later.
- **Dated UX:** Dense forms, inconsistent design, and a cluttered interface slow down daily workflows and create a learning curve for new staff.
- **Single-user architecture:** No collaboration, no ability to share clients between practitioners in a group practice.
- **No client self-service:** Clients receive printed PDF meal plans and must manually track (or not track) their adherence.

**For Clients:**
- **Complexity kills adherence:** Existing nutrition apps (MyFitnessPal, Cronometer) require logging every ingredient, scanning barcodes, and estimating portions—too much friction for most users.
- **No connection to their nutritionist:** Clients have questions, slip up, or need encouragement between visits but have no channel to their professional.
- **Progress is invisible:** Without simple tracking, clients don't see their adherence patterns or celebrate small wins, reducing motivation.

### Impact of the Problem

| Stakeholder | Impact |
|-------------|--------|
| Nutritionists | Lost productivity (estimated 30+ min/day on workarounds), inability to scale practice, client churn due to poor engagement |
| Clients | Lower adherence rates, slower progress toward health goals, higher dropout from nutrition programs |
| Practice Revenue | Reduced client retention, limited capacity for growth, competitive disadvantage vs. modernized practices |

### Why Existing Solutions Fall Short

| Solution | Gap |
|----------|-----|
| Current NutriPro Desktop | No mobile, no client app, no remote access, dated UX |
| Practice Better / Nutrium | No Hebrew/RTL, less clinical depth (blood tests, body comp), no existing data migration |
| MyFitnessPal / Cronometer | Consumer-only, no professional tools, too complex for simple adherence |
| Spreadsheets / Paper | No automation, no client visibility, error-prone, doesn't scale |

### Urgency

- The development partner (nutritionist) is actively constrained by the current system daily
- Competitors are modernizing; delay risks losing market position
- Post-COVID, remote/hybrid work expectations have accelerated demand for cloud-based tools
- Client expectations for mobile apps have become standard; practices without them appear outdated

---

## Proposed Solution

### Core Concept

Build a **cloud-native platform** consisting of two purpose-built applications connected by a shared backend:

---

#### 1. NutriPro Web (Nutritionist Application)

A browser-based practice management system accessible from any device (desktop, laptop, tablet). Key modules:

| Module | Capabilities |
|--------|--------------|
| **Client Management** | Full profiles (personal info, medical history, food preferences, medications, supplements, notes), client status tracking, client type categorization |
| **Medical Questionnaire** | Structured health intake forms with Yes/No/Notes/Treated columns, configurable questions, pre-consultation review |
| **Meal Menu Builder** | Create daily/weekly menus by selecting foods from dictionary, real-time macro/micronutrient calculations, "Is Primary" food flagging, PDF export |
| **Workout Plan Builder** | Create programs from exercise dictionary, specify sets/reps/weight targets, assign to clients |
| **Blood Test Tracking** | Record lab results over time (HDL, LDL, Triglycerides, HbA1c, vitamins, thyroid, etc.), reference range display, trend graphing |
| **Body Composition** | Skinfold measurements (7 sites), Jackson-Pollock formula calculations, fat %, FMMI, track over time |
| **Data Tracking** | Weight, fat %, body measurements (belly, waist, arm, forearm), blood pressure, hand grip strength, historical graphs |
| **Metabolic Settings** | RMR coefficients, activity coefficients, training type (strength/aerobic), calorie target calculations |
| **Dictionary Management** | CRUD for foods, exercises, medications, supplements, diseases—searchable, filterable, bulk import |
| **Progress Dashboard** | Client adherence scores, recent activity, alerts for off-track clients, quick-glance cards |
| **Reports & Export** | PDF generation for meal plans, workout plans, progress reports |
| **Admin Configuration** | Manage all reference tables (meal types, client types, blood test parameters, fat % ranges, cities, etc.) |

---

#### 2. NutriPro Mobile (Client Application)

A native mobile app (iOS + Android) designed for daily use with minimal friction:

| Feature | User Experience |
|---------|-----------------|
| **Daily Meal Checklist** | See today's meals → tap to mark eaten ✓ → done in seconds |
| **Daily Workout Checklist** | See today's exercises → tap to mark completed ✓ |
| **Exercise Logging** | For each exercise: log actual weight, reps, sets performed |
| **Weight & Measurements** | Quick entry for weight, body measurements on weigh-in days |
| **Progress Dashboard** | Adherence % (this week), weight trend chart, streak counter |
| **Personal Records** | See PRs per exercise, celebrate new maxes |
| **Meeting Schedule** | View upcoming appointments with nutritionist |
| **Push Notifications** | Reminders for meals, workouts, weigh-ins (configurable) |
| **Daily Summary** | "Today: 4/5 meals ✓, Leg Day ✓, 🔥 12-day streak" |

**Design Philosophy:** One-tap interactions wherever possible. No barcode scanning, no portion estimation, no calorie counting—just check what you ate from your prescribed plan.

---

#### 3. Unified Backend & Sync Architecture

| Component | Description |
|-----------|-------------|
| **Central Database** | Single source of truth for all client data, plans, tracking, and master data |
| **Real-Time Sync** | Changes on web immediately visible on mobile and vice versa (WebSocket or similar) |
| **Offline Support** | Mobile app queues actions when offline, syncs when reconnected (future phase) |
| **API Layer** | RESTful API serving both web and mobile clients |
| **Authentication** | Secure login for both nutritionists and clients, role-based access control |
| **Data Encryption** | All client health data encrypted at rest and in transit |

---

#### 4. Master Data System (Dictionary)

The backbone powering all features:

| Entity | Key Fields | Records (Est.) |
|--------|------------|----------------|
| **Foods** | Name, category, serving, calories, protein, carbs, fat, fiber, 20+ micronutrients, tags | 5,000+ |
| **Exercises** | Name, muscle group, equipment, type, difficulty, instructions | 500+ |
| **Medications** | Name, category, dietary interactions, notes | 200+ |
| **Supplements** | Name, type, dosage guidelines, interactions | 100+ |
| **Diseases/Conditions** | Name, dietary considerations, contraindicated items | 100+ |
| **Blood Test Parameters** | Name, unit, reference ranges by age/gender | 50+ |
| **Configuration Tables** | RMR coefficients, activity levels, fat % ranges, meal types, client types, etc. | Various |

**Import Path:** Bulk CSV/Excel import from partner's existing NutriPro desktop database.

---

### Key Differentiators

| Differentiator | How We're Different |
|----------------|---------------------|
| **Clinical Depth** | Full blood test tracking, body composition calculator (skinfold/Jackson-Pollock), medical questionnaires, RMR/metabolic calculations—features consumer apps don't offer |
| **Dual-Interface Architecture** | Complex tools for professionals + dead-simple app for clients, rather than one-size-fits-all |
| **Hebrew-First, Bilingual** | Native RTL support with Hebrew UI, serving an underserved market |
| **Real-Time Sync** | Nutritionist and client see the same data instantly—no manual syncing, no stale information |
| **Migration-Ready** | Built to import data from the existing NutriPro desktop system, ensuring zero data loss |
| **Master Data System** | Comprehensive dictionary (foods, exercises, medications, supplements, diseases) that the partner has curated over years |

### Why This Solution Will Succeed

| Factor | Rationale |
|--------|-----------|
| **Built with a power user** | The development partner (nutritionist) provides real-world requirements, immediate feedback, and domain expertise |
| **No feature regression** | By preserving all existing functionality, we eliminate the #1 migration blocker |
| **Solves the engagement gap** | The mobile app creates a daily touchpoint that doesn't exist today |
| **Right-sized for the market** | Hebrew/RTL focus means less competition; clinical depth means higher switching costs |
| **Proven problem** | Partner is already working around limitations daily—this isn't speculative |

### Data Flow Example

```
NUTRITIONIST creates meal plan for Client A
        ↓
Plan saved to central database
        ↓
Real-time sync pushes to Client A's mobile app
        ↓
CLIENT A sees today's meals, taps "Breakfast ✓"
        ↓
Check-in saved to database
        ↓
NUTRITIONIST dashboard updates: "Client A: 1/5 meals today"
```

---

## Target Users

### Primary User Segment: Nutritionists & Dietitians

**Profile:**
- Licensed nutritionists, dietitians, and clinical nutrition professionals
- Primarily based in Israel (Hebrew-speaking)
- Solo practitioners or small practices (1-5 professionals)
- Age range: 28-55, tech-comfortable but not developers
- Managing 20-100+ active clients at any time

**Current Behaviors & Workflows:**
- Use existing NutriPro desktop software (or spreadsheets/paper for some)
- Create meal plans manually, print as PDFs for clients
- Track client metrics in the system but have no visibility between visits
- Schedule appointments via phone, WhatsApp, or external calendar
- Spend significant time on data entry and administrative tasks

**Specific Needs & Pain Points:**
- Access client data from anywhere (home, second office, during consultations)
- See if clients are following plans without waiting for next appointment
- Reduce time spent on repetitive meal plan creation (templates)
- Professional-grade tools (blood tests, body composition) not found in consumer apps
- Maintain comprehensive medical/dietary history per client
- Hebrew interface with proper RTL support

**Goals:**
- Improve client outcomes through better engagement and accountability
- Scale practice without proportionally scaling administrative burden
- Appear modern and professional to clients
- Reduce client dropout rates

---

### Secondary User Segment: Clients (End Users)

**Profile:**
- Adults seeking nutritional guidance for weight management, health conditions, or performance
- Range from highly motivated to reluctant/skeptical
- Tech literacy varies widely (must support lowest common denominator)
- Age range: 18-70
- Hebrew-speaking (primarily), some English

**Current Behaviors & Workflows:**
- Receive printed meal plan from nutritionist
- May or may not track adherence (usually don't)
- Use WhatsApp to message nutritionist with questions (informal)
- Weigh themselves periodically (data often lost or unshared)
- Go to gym with workout plan on paper or in notes app

**Specific Needs & Pain Points:**
- Need simple way to remember what to eat today
- Want to track gym progress without complex apps
- Forget their plan details when shopping or cooking
- Lack motivation when they don't see progress
- Want to feel connected to their nutritionist between visits

**Goals:**
- Follow the plan their nutritionist created (adherence)
- See visible progress toward their health goals
- Feel supported and accountable
- Minimum friction in daily tracking

---

## Goals & Success Metrics

### Business Objectives

- **Launch MVP within 6 months** with full feature parity to existing NutriPro desktop (no regression)
- **Onboard development partner** (nutritionist) as first production user within 4 months (beta)
- **Migrate 100% of partner's existing data** (clients, foods, exercises, medications, history) without data loss
- **Achieve 5-10 paying practitioners** within 12 months of launch
- **Establish Hebrew-first nutrition platform** as market leader in Israel

---

### User Success Metrics

**Nutritionist Success:**
- Reduce time spent on meal plan creation by 40%+ (via templates and improved UX)
- Access client data remotely at least 3x/week
- View client adherence data between appointments for 80%+ of active clients
- Generate professional PDF reports in <2 minutes

**Client Success:**
- Daily app engagement: 80%+ of clients check in at least once per day
- Adherence visibility: Clients can see their weekly adherence score anytime
- Workout logging: Clients log 90%+ of prescribed workouts with weights/reps
- Reduced friction: Complete daily check-in in <30 seconds

---

### Key Performance Indicators (KPIs)

| KPI | Definition | Target (Year 1) |
|-----|------------|-----------------|
| **Practitioner Adoption** | # of paying nutritionists using the platform | 5-10 |
| **Client Activation** | % of invited clients who install and use mobile app | >70% |
| **Daily Active Clients** | % of active clients who check in daily | >60% |
| **Adherence Rate** | Avg % of prescribed meals/workouts checked off per client | >75% |
| **Data Migration Success** | % of legacy data successfully imported | 100% |
| **Feature Parity** | % of legacy features replicated in new system | 100% |
| **System Uptime** | Platform availability | >99.5% |
| **NPS (Nutritionists)** | Net Promoter Score from practitioners | >50 |
| **Client Retention** | % of clients still active after 3 months | >70% |
| **Time to Plan** | Avg time to create a weekly meal plan | <15 min |

---

## MVP Scope

### Core Features (Must Have)

**Foundation & Security:**
- **Secure Authentication:** Role-based access (nutritionist vs. client), encrypted credentials
- **Data Protection:** All health data encrypted at rest and in transit, audit logging
- **Bilingual UI:** Hebrew (RTL) + English interface support throughout

**Master Data System (Dictionary):**
- **Foods Database:** Full CRUD, search/filter, nutritional values (macros + micros), bulk CSV import
- **Exercises Database:** Full CRUD, muscle groups, equipment, types, instructions
- **Medications Database:** Name, interactions, dietary notes
- **Supplements Database:** Name, type, dosage, interactions
- **Diseases/Conditions:** Dietary considerations, contraindications
- **Configuration Tables:** Blood test parameters, RMR coefficients, activity coefficients, fat % ranges, meal types, client types, etc.

**Nutritionist Web App:**
- **Client Management:** Profiles, contact info, status, type, medical info, food preferences, notes
- **Medical Questionnaire:** Structured health intake with configurable questions
- **Meal Menu Builder:** Create daily/weekly plans, select from food DB, auto-calculate nutrition, "Is Primary" flag
- **Workout Plan Builder:** Create programs from exercise DB, sets/reps/weight targets
- **Blood Test Tracking:** Record lab results, multiple parameters, reference ranges, trend graphs
- **Body Composition Calculator:** Skinfold measurements (7 sites), Jackson-Pollock formulas
- **Data Tracking:** Weight, fat %, FMMI, TBW, body measurements, blood pressure, grip strength, historical graphs
- **RMR & Metabolic Settings:** Coefficients, activity levels, training type, calorie calculations
- **Supplements Tracking:** Per-client supplement assignments
- **Progress Dashboard:** Adherence scores, recent client activity, basic alerts
- **PDF Generation:** Export meal plans, workout plans, progress reports
- **Meeting Management:** View/manage scheduled appointments

**Client Mobile App:**
- **Daily Meal Checklist:** One-tap check-off for prescribed meals
- **Daily Workout Checklist:** One-tap check-off for prescribed exercises
- **Exercise Progress Logging:** Log weight, reps, sets per exercise
- **Weight/Measurement Logging:** Quick entry on weigh-in days
- **Progress Dashboard:** Adherence %, weight trend, streak counter
- **Meeting Schedule:** View upcoming appointments
- **Push Notifications:** Meal/workout reminders (configurable)

**Sync & Infrastructure:**
- **Bi-directional Real-Time Sync:** Web ↔ Mobile, changes visible within seconds
- **Data Migration Tools:** Import from existing NutriPro desktop (clients, foods, exercises, history)

---

### Out of Scope for MVP

| Feature | Reason | Phase |
|---------|--------|-------|
| Chat/Messaging | Nice-to-have; adds complexity | Future |
| Calendar Integration (Google/Outlook) | Nice-to-have | Phase 2 |
| Offline Mobile Mode | Complex sync logic; requires stable online-first | Phase 2 |
| Before/After Photo Timeline | Secondary feature | Phase 2 |
| Adherence Heatmaps | Advanced visualization | Phase 2 |
| In-App Meeting Booking | Nice-to-have | Phase 2 |
| Drag-and-Drop Plan Builder | UX enhancement, not core | Future |
| Version History for Plans | Nice-to-have | Future |
| Non-Adherence Auto-Alerts | Requires tuning thresholds | Phase 2 |
| AI Meal Suggestions | Moonshot | Future |
| Wearable Integration | Moonshot | Future |
| White-Label Platform | Business model expansion | Future |
| Research Platform | Moonshot | Future |
| Client Cohort Views | User removed | Won't do |
| Bulk Operations | User removed | Won't do |
| Photo Meal Logging | User removed | Won't do |

---

### MVP Success Criteria

The MVP is successful when:

1. **Feature Parity:** 100% of existing NutriPro desktop functionality is available in the new web app
2. **Data Migration:** Partner's complete dataset (clients, foods, exercises, medications, history) is imported without loss
3. **Client App Adoption:** Partner's clients can download, log in, and check off meals/workouts
4. **Real-Time Sync:** Changes made on web appear on mobile within 5 seconds and vice versa
5. **Partner Sign-Off:** Development partner (nutritionist) confirms the system meets their daily workflow needs
6. **Stability:** System handles 1 nutritionist + 50 concurrent clients without performance degradation

---

## Post-MVP Vision

### Phase 2 Features (Months 7-12)

Immediately following MVP launch, prioritize features that enhance engagement and polish:

| Feature | Value | Effort |
|---------|-------|--------|
| **Template Library** | Reusable meal plans and workout programs; major time-saver for nutritionists | Medium |
| **Session Notes** | Per-client visit notes; improves continuity of care | Low |
| **Client Summary Bar** | Quick-view of blood tests, meds, preferences on menu screen | Low |
| **Push Notification Enhancements** | Smart reminders based on client schedule | Medium |
| **Streak Tracking & Milestones** | Gamification for clients; improves engagement | Low |
| **Personal Records (PRs)** | Celebrate workout achievements; motivates clients | Low |
| **Daily Summary Card** | "Today: 4/5 meals ✓" at-a-glance view | Low |
| **Graph Enhancements** | Height/weight/BMI development pages, body composition pages | Medium |
| **Calendar Integration** | Sync meetings with Google Calendar / Outlook | Medium |
| **Offline Mobile Mode** | App works without internet, syncs when reconnected | High |
| **SMS Templates** | Saved messages for client communication | Low |

---

### Long-Term Vision (Year 2+)

**Platform Maturity:**
- Support for **group practices** (multiple nutritionists, shared clients, role permissions)
- **Advanced visualizations**: Adherence heatmaps, workout volume progression, period comparisons
- **Before/after photo timeline** with secure storage and nutritionist review
- **In-app meeting booking** with availability management
- **Non-adherence alerts** with configurable thresholds and escalation

**Market Expansion:**
- **English-first version** for international markets (US, UK, Europe)
- **Localization** for additional languages (Arabic, Russian—significant in Israel)
- **Marketing site** and self-service onboarding for new practitioners
- **Pricing tiers** based on client count or feature access

**Technology Evolution:**
- **AI-powered meal suggestions** based on preferences, restrictions, and goals
- **Wearable integration** (Apple Watch, Fitbit, Garmin) for automatic activity logging
- **Lab integration** (direct import from Israeli health funds: Clalit, Maccabi, Meuhedet, Leumit)
- **Telehealth features** (video consultations within the platform)

---

### Expansion Opportunities

| Opportunity | Description | Prerequisites |
|-------------|-------------|---------------|
| **White-Label Platform** | License the platform to nutrition clinics under their brand | Multi-tenancy architecture, customization framework |
| **B2B2C Model** | Partner with gyms, health clubs, corporate wellness programs | API integrations, bulk client management |
| **Research Platform** | Aggregate anonymized data for nutritional research | Privacy compliance, data anonymization, research partnerships |
| **Certification/Education** | Partner with nutrition certification bodies for continuing education | Content partnerships |
| **Supplement/Food Partnerships** | Affiliate links or integrations with health food brands | E-commerce integrations |
| **Insurance Integration** | Support for insurance-covered nutrition counseling documentation | Compliance features, reporting |

---

## Technical Considerations

### Platform Requirements

| Requirement | Specification |
|-------------|---------------|
| **Target Platforms** | Web app (responsive, desktop-first), iOS app, Android app |
| **Browser Support** | Chrome, Safari, Firefox, Edge (latest 2 versions) |
| **Mobile OS Support** | iOS 14+, Android 10+ |
| **Performance** | Page load <3s, API responses <500ms, real-time sync <5s latency |
| **Availability** | 99.5% uptime target |
| **Concurrent Users** | Support 10 nutritionists × 100 clients = 1,000 users initially |
| **Data Retention** | Client records retained indefinitely; configurable archival |

---

### Technology Preferences

*Note: These are initial preferences, not final decisions. Architecture phase will validate.*

| Layer | Preference | Rationale |
|-------|------------|-----------|
| **Frontend (Web)** | React or Next.js | Modern, component-based, large ecosystem, good RTL support |
| **Frontend (Mobile)** | React Native | Code sharing with web, single codebase for iOS/Android, fast development |
| **Backend** | Node.js (Express/Fastify) or Python (FastAPI) | Strong async support, good for real-time features |
| **Database** | PostgreSQL | Relational data model fits well, strong JSON support, proven scale |
| **Real-Time** | WebSockets (Socket.io) or Supabase Realtime | Required for bi-directional sync |
| **Authentication** | JWT + refresh tokens, or Auth0/Supabase Auth | Industry standard, secure |
| **File Storage** | Cloud storage (S3/GCS/Supabase Storage) | PDF exports, future photo storage |
| **Hosting** | Vercel (frontend) + Railway/Render/Fly.io (backend) or Supabase | Cost-effective for MVP, easy scaling |

---

### Architecture Considerations

**Repository Structure:**
- **Monorepo recommended** (Turborepo or Nx)
- Packages: `web`, `mobile`, `api`, `shared` (types, utils, validation)
- Enables code sharing between web and mobile

**Service Architecture:**
- **Monolith-first** for MVP (simpler deployment, debugging, and iteration)
- Modular internal structure allowing future service extraction
- Clear domain boundaries: Clients, Plans, Tracking, Dictionary, Auth

**Integration Requirements:**
- **PDF Generation:** Server-side PDF library (Puppeteer, PDFKit, or similar)
- **Push Notifications:** Firebase Cloud Messaging (FCM) for both iOS and Android
- **Email:** Transactional email service (SendGrid, Resend, or similar) for invites and notifications
- **Calendar (Phase 2):** Google Calendar API, Microsoft Graph API

**Security & Compliance:**
- **Data Encryption:** TLS 1.3 in transit, AES-256 at rest
- **Access Control:** Role-based (nutritionist, client, admin), row-level security on client data
- **Audit Logging:** Track all data access and modifications
- **Privacy:** GDPR-aware design (data export, deletion requests)
- **Israeli Privacy Law:** Compliance with Protection of Privacy Law, 5741-1981
- **No HIPAA required** (Israel-focused; revisit for US expansion)

---

### Data Model Highlights

**Core Entities:**
```
User (id, email, role, language_preference)
  └── Nutritionist (practice_info, settings)
  └── Client (nutritionist_id, profile, preferences, medical_info)
        └── MealPlan (dates, meals)
        └── WorkoutPlan (dates, exercises)
        └── TrackingRecord (date, metrics)
        └── BloodTest (date, parameters)
        └── BodyComposition (date, measurements)
        └── MealCheckIn (date, meal_id, completed)
        └── WorkoutCheckIn (date, exercise_id, sets, reps, weight)

Dictionary (shared across all nutritionists initially)
  └── Food (nutrition_values)
  └── Exercise (details)
  └── Medication (interactions)
  └── Supplement (details)
  └── Disease (considerations)
  └── BloodTestParameter (ranges)
  └── ConfigTables (coefficients, types, etc.)
```

**Key Design Decisions:**
- Dictionary is shared (not per-nutritionist) for MVP; consider per-practice customization later
- Client belongs to one nutritionist (no sharing) for MVP
- All timestamps in UTC, converted to local timezone in UI

---

## Constraints & Assumptions

### Constraints

| Constraint | Details | Impact |
|------------|---------|--------|
| **Budget** | Partner-funded development; no external investment assumed | Must prioritize cost-effective tech choices; limit paid services; leverage open-source |
| **Timeline** | Target MVP in 6 months, with beta at 4 months | Aggressive but achievable with focused scope; no room for scope creep |
| **Resources** | Small team (likely 1-2 developers + partner as domain expert) | Must choose technologies that maximize productivity; avoid complex architectures |
| **Technical** | Must support Hebrew/RTL from day one; must import legacy data | Influences framework/library choices; requires data migration tooling |
| **Legacy Dependency** | Existing NutriPro desktop database format must be reverse-engineered for import | May require partner access to export data; could reveal unknown data structures |
| **Single Tenant (MVP)** | Initially built for one practitioner; multi-tenancy deferred | Simplifies auth/data model but limits scalability story |

---

### Key Assumptions

**Business Assumptions:**
- Partner (nutritionist) will pay for development work on agreed milestone schedule
- Partner will actively participate in requirements, testing, and feedback throughout development
- Partner's existing client base will adopt the mobile app when recommended
- Hebrew-speaking nutritionist market in Israel is underserved by modern tools
- Feature parity with legacy system is mandatory for partner to migrate
- Developer retains right to commercialize/license platform to other practitioners
- No significant regulatory changes will affect nutrition software in Israel during development

**Technical Assumptions:**
- Legacy NutriPro data can be exported to CSV/Excel or accessed via database file
- Partner has rights to the data in the existing system
- All master data (foods, exercises, medications) from legacy system is usable and accurate
- Real-time sync can be achieved with standard WebSocket infrastructure
- React Native provides sufficient performance for the mobile app's simple UI needs

**User Assumptions:**
- Nutritionists are willing to use a web browser instead of desktop application
- Clients have smartphones (iOS or Android) and basic app literacy
- Clients will install an app if their nutritionist recommends it
- Daily check-in habit can be formed with simple UX and optional reminders
- Hebrew speakers are comfortable with some English medical/technical terminology

**Market Assumptions:**
- Competitors (Practice Better, Nutrium) won't launch Hebrew versions in the next 12 months
- Word-of-mouth from satisfied practitioners will drive initial growth
- Pricing can be introduced after proving value with initial users

---

## Risks & Open Questions

### Key Risks

| Risk | Description & Impact | Likelihood | Mitigation |
|------|---------------------|------------|------------|
| **Payment/Cash Flow** | Partner may delay payments or dispute scope; development stalls without funding | Medium | Milestone-based payments; clear contract; deposit before work begins |
| **Scope vs. Budget Mismatch** | Feature parity requirement exceeds what partner is willing/able to pay | Medium-High | Detailed estimate upfront; fixed-price phases; explicit change request process |
| **Ownership/IP Disputes** | Unclear who owns the code, data, or right to commercialize | Medium | Contract specifies IP ownership clearly |
| **Partner as Only Client** | Revenue depends on one customer; risky if relationship sours | High initially | Plan for productization; retain right to sell to other nutritionists |
| **Data Migration Failure** | Legacy NutriPro data format is undocumented or incompatible; migration takes longer than expected or loses data | Medium | Early spike on data export; involve partner in testing; build validation tools |
| **Scope Creep** | Feature parity requirement keeps expanding as partner remembers "one more thing" | High | Lock MVP scope document; defer new requests to Phase 2; weekly scope reviews |
| **Partner Availability** | Partner (nutritionist) is too busy with practice to provide timely feedback | Medium | Schedule fixed weekly sessions; async communication for small questions; "delay by client" clauses |
| **Real-Time Sync Complexity** | Bi-directional sync introduces bugs, race conditions, or performance issues | Medium | Start with simple polling; upgrade to WebSocket; extensive testing; conflict resolution strategy |
| **Mobile App Rejection** | Apple/Google app store rejects app for policy violations | Low | Follow platform guidelines; no health claims; proper privacy policy |
| **Client Adoption** | Clients don't install or use the mobile app despite nutritionist recommendation | Medium | Make onboarding frictionless; clear value prop; optional (not required) for nutritionist workflow |
| **Hebrew/RTL Bugs** | RTL layout issues across web and mobile cause usability problems | Medium | Choose RTL-friendly frameworks; test with Hebrew content from day one |
| **Solo Developer Risk** | Single developer creates knowledge silo; illness/departure halts progress | Medium-High | Document architecture decisions; use standard patterns; consider contractor backup |
| **Security Breach** | Health data exposed due to vulnerability | Low | Security-first architecture; encryption; audit logs; penetration testing before launch |

---

### Open Questions

**Business & Commercial Questions:**
- What is the payment structure? Milestone-based? Monthly retainer? Fixed price for MVP?
- Who owns the IP? Developer retains and licenses? Partner owns? Joint ownership?
- Can developer sell/license the platform to other nutritionists? (Exclusivity?)
- Who pays for ongoing hosting, domains, app store fees?
- What's the maintenance/support arrangement post-launch?
- How are Phase 2 features priced?

**Technical Questions:**
- What database format does the existing NutriPro desktop use? (MS Access? SQL Server? Proprietary?)
- Can we get a sample data export to assess migration complexity?
- Does the partner have any existing hosting/domain preferences?
- What email/SMS providers are common in Israel for transactional messages?

**Product Questions:**
- Should clients be able to see their historical meal plans, or only current?
- How should the system handle clients who switch nutritionists?
- What happens to client data if a nutritionist stops using the platform?
- Should nutritionists be able to customize the food database, or is it shared?

**User Experience Questions:**
- How do clients get invited? Email? SMS? QR code?
- What's the minimum viable onboarding flow for clients?
- Do clients need to see their nutritionist's name/photo in the app?
- How should push notification preferences work?

---

### Areas Needing Further Research

| Research Area | Why It Matters | Next Step |
|---------------|----------------|-----------|
| **Legacy Data Format** | Migration is critical path; unknown format is highest risk | Partner to provide sample export or database file access |
| **Israeli Privacy Regulations** | Ensure compliance with Protection of Privacy Law | Consult legal resource or research ILITA guidelines |
| **Nutrition App Competitors** | Understand local market (Israeli apps we may have missed) | Partner interview + app store research |
| **Client Onboarding Best Practices** | Maximize app installation rate | Review how Nutrium/Practice Better onboard clients |
| **React Native RTL Performance** | Confirm RTL works well in RN before committing | Build small proof-of-concept |
| **PDF Generation in Hebrew** | Ensure proper RTL rendering in generated PDFs | Test PDF libraries with Hebrew content |

---

## Appendices

### A. Research Summary

**Inputs Used for This Brief:**

| Source | Key Findings |
|--------|--------------|
| **Existing NutriPro System Documentation** | 14-page analysis of current desktop platform; 10+ modules documented; full data model inferred; Hebrew/RTL interface; comprehensive clinical features (blood tests, body composition, medical questionnaires) |
| **Brainstorming Session** | 70+ features identified; MoSCoW prioritization completed; 19 must-have MVP features; gap analysis against legacy system |
| **Competitive Analysis** | Practice Better, Nutrium, Healthie validated B2B nutrition software market; none offer Hebrew/RTL; pricing benchmarks $25-95/month |
| **Partner Requirements** | Dictionary preservation critical; all existing functionality must migrate; client simplicity is paramount |

**Key Research Findings:**

1. **B2B nutrition software is a proven market** — Multiple successful SaaS platforms exist internationally
2. **Hebrew/RTL is an unserved niche** — No major competitor offers native Hebrew support
3. **Clinical depth differentiates** — Blood tests, body composition, medical questionnaires are rare in consumer apps
4. **Client apps are table stakes** — All successful B2B nutrition platforms include client-facing apps
5. **Migration path is essential** — Practitioners won't switch without data portability

---

### B. Stakeholder Input

**Primary Stakeholder: Development Partner (Nutritionist)**

| Input | Details |
|-------|---------|
| **Current Pain** | Desktop-bound system limits mobility; no client visibility between visits; dated UX |
| **Must-Haves** | All existing functionality preserved; Dictionary (foods, exercises, meds, supplements, diseases) intact; Hebrew interface |
| **Nice-to-Haves** | Research platform (deferred); Chat (deferred) |
| **Removed from Scope** | Client cohort views; bulk operations; photo meal logging; pre-meeting questionnaire; weekly automated check-in; nutritionist quick-notes |
| **Success Criteria** | "System meets my daily workflow needs" — personal sign-off required |

**Secondary Stakeholder: Clients (End Users)**

| Input | Details |
|-------|---------|
| **Primary Need** | Simple way to track what they ate and whether they completed workouts |
| **Key Frustration** | Existing apps are too complex; too much data entry required |
| **Desired Outcome** | Feel supported; see progress; stay accountable |

---

### C. References

**Project Documents:**
- `docs/brainstorming-session-results.md` — Full brainstorming session output
- `NutriPro_System_Documentation.pdf` — Existing platform analysis (14 pages)

**Competitive References:**
- [Practice Better](https://www.practicebetter.io) — B2B nutrition practice management
- [Nutrium](https://nutrium.com) — B2B nutrition software with client app
- [Healthie](https://www.gethealthie.com) — Telehealth + nutrition platform
- [Trainerize](https://www.trainerize.com) — Fitness coaching platform

**Technical References:**
- React Native RTL documentation
- Israeli Privacy Protection Law (5741-1981)
- Jackson-Pollock body composition formulas

---

## Next Steps

### Immediate Actions

1. **Finalize Contract with Partner**
   - Define payment structure (milestones recommended)
   - Clarify IP ownership and commercialization rights
   - Set project timeline and communication cadence
   - Include change request process for scope additions

2. **Obtain Legacy Data Sample**
   - Partner to export sample data from existing NutriPro desktop
   - Assess data format, structure, and migration complexity
   - Identify any data quality issues early

3. **Technical Spike: RTL + React Native**
   - Build small proof-of-concept with Hebrew/RTL support
   - Validate framework choice before full development
   - Test PDF generation with Hebrew content

4. **Create PRD**
   - Hand off this Project Brief to PM workflow
   - Generate detailed Product Requirements Document with epics and stories
   - Define acceptance criteria for each feature

5. **Architecture Design**
   - Design database schema based on data model
   - Define API contracts between web, mobile, and backend
   - Select and validate technology stack
   - Plan sync architecture (WebSocket vs. polling)

6. **Set Up Development Environment**
   - Initialize monorepo structure
   - Configure CI/CD pipeline
   - Set up staging and production environments
   - Establish coding standards and conventions

---

### Recommended Contract Terms

| Term | Recommendation |
|------|----------------|
| **Deposit** | 20-30% upfront before development begins |
| **Milestones** | 3-4 payment milestones tied to deliverables (e.g., Dictionary, Web MVP, Mobile MVP, Launch) |
| **Change Requests** | Any scope additions require written approval + cost estimate |
| **IP Ownership** | Developer retains code ownership; partner gets perpetual license. OR: Partner owns but developer retains right to create derivative works for other clients |
| **Commercialization** | Developer retains right to sell platform to other nutritionists (non-exclusive) |
| **Source Code** | Held in escrow or delivered upon final payment |
| **Hosting Costs** | Partner pays directly or reimburses monthly |
| **Maintenance** | Separate agreement post-launch (monthly retainer or hourly) |
| **Termination** | Clear terms for what happens if project is cancelled mid-way |

---

### PM Handoff

This Project Brief provides the full context for **NutriPro** — a bilingual web and mobile platform for nutritionists and their clients.

**Key artifacts to reference:**
- This Project Brief (`docs/brief.md`)
- Brainstorming Session Results (`docs/brainstorming-session-results.md`)
- Existing System Documentation (`NutriPro_System_Documentation.pdf`)

**Recommended next step:**
Start in **PRD Generation Mode** to create a detailed Product Requirements Document. Review the brief thoroughly, then work through each epic and feature systematically, ensuring:

- All 19 must-have MVP features are captured as stories
- Acceptance criteria are specific and testable
- Dependencies between features are identified
- Data migration is treated as a distinct epic
- Dictionary/Master Data is built first (foundation for everything else)

**Suggested Epic Structure:**
1. Epic 1: Foundation (Auth, Database, Dictionary)
2. Epic 2: Client Management & Medical Intake
3. Epic 3: Meal Planning & Nutritional Calculations
4. Epic 4: Workout Planning
5. Epic 5: Clinical Features (Blood Tests, Body Composition, Tracking)
6. Epic 6: Client Mobile App
7. Epic 7: Sync & Real-Time Infrastructure
8. Epic 8: Reports & PDF Generation
9. Epic 9: Data Migration
10. Epic 10: Polish & Launch Prep

---

*Document created using the BMAD-METHOD™ framework*

