# Brainstorming Session Results

**Session Date:** December 27, 2025  
**Facilitator:** Business Analyst Mary  
**Participant:** Product Owner / Founder  

---

## Executive Summary

**Topic:** NutriPro — A web app for nutritionists/dietitians to manage their work + mobile app for clients to track food, workouts, and progress.

**Session Goals:** Focused ideation with exploration to define MVP scope for replacing an existing desktop-based platform (NutriPro) with a modern web + mobile solution.

**Techniques Used:**
1. Fast Problem Framing (roles: nutritionist, client)
2. Feature Storm by Role
3. Gap Analysis against existing NutriPro platform documentation
4. MoSCoW Prioritization

**Total Ideas Generated:** 70+ features across all categories

### Key Themes Identified:
- **Simplicity for clients** — One-tap check-off interface for meals and workouts
- **Professional depth for nutritionists** — Full clinical toolset (blood tests, body composition, medical questionnaires)
- **Dictionary as backbone** — Comprehensive master data system (foods, exercises, medications, supplements, diseases, parameters)
- **Bi-directional sync** — Real-time data flow between web (nutritionist) and mobile (client)
- **Modern UX upgrade** — Replace dated desktop app with beautiful, responsive web + mobile
- **Preserve all functionality** — No feature regression from existing system
- **Bilingual support** — Hebrew (RTL) + English interface

---

## Technique Sessions

### Technique 1: Fast Problem Framing — 15 min

**Description:** Identified primary users, their pain points, and success criteria.

**Ideas Generated:**

1. **Primary Users:**
   - Nutritionists building and managing client plans
   - Clients following meal plans and workout programs

2. **Nutritionist Pain Points:**
   - No existing system is good enough for comprehensive workflow
   - UI/UX matters significantly for daily productivity
   - Zero interaction with clients between in-person meetings

3. **Client Pain Points:**
   - No app is simple enough (just check what you ate, check gym goals)
   - Limited interaction with nutritionist outside appointments
   - Progress tracking in apps doesn't provide meaningful insights

4. **Success Criteria:**
   - Improved nutritionist workflow efficiency
   - Better client outcomes and adherence
   - Seamless data flow between professionals and clients

**Insights Discovered:**
- The interaction gap between meetings is a major opportunity
- Simplicity is the #1 client requirement — complexity kills adherence
- Nutritionists need clinical-grade tools, not consumer-grade apps

**Notable Connections:**
- Client simplicity + nutritionist depth = two very different UX approaches needed
- Async sync solves the "between meetings" interaction gap

---

### Technique 2: Feature Storm by Role — 30 min

**Description:** Generated features organized by user role and system area.

#### Nutritionist Workspace Features:

1. Manage all client data (profiles, contact, goals, medical info)
2. Create meal menus from food database
3. Create workout plans from exercise database
4. Manage master data (food/workouts/medication/supplements/dictionary)
5. Scheduled meetings management
6. Progress review dashboards
7. Template library (reusable meal plans, workout programs)
8. Drag-and-drop plan builder (visual construction)
9. Version history for plans (track changes, rollback)
10. Session notes per client (observations, adjustments)
11. Alert dashboard (clients off-track 3+ days)
12. Auto-calc nutritional values from food database
13. Quick-glance client cards (adherence %, last activity, next meeting)
14. Client Summary Bar (blood tests, meds, preferences, supplements at a glance)
15. "Is Primary" food flag for meal emphasis

#### Client Mobile App Features:

1. Daily checklists for meals (one-tap check-off)
2. Daily checklists for workouts (one-tap check-off)
3. Workout progress per exercise (weight, reps, sets)
4. Simple logging interface
5. Progress checks and dashboards
6. Meetings schedule view
7. Weight/body measurement logging
8. Streak tracking + milestones (gamification)
9. Daily summary card ("Today: 4/5 meals ✓, leg day ✓")
10. Push notification reminders (meal times, workout time)
11. Offline mode (sync when back online)
12. Personal records celebration (new PR! 🎉)

#### Interaction Model Features:

1. Async bi-directional data sync (web ↔ mobile)
2. Real-time sync between platforms
3. In-app meeting booking (client requests, nutritionist confirms)
4. Post-meeting summary pushed to client
5. Non-adherence alerts (nutritionist notified if client off-track)

#### Progress & Insights Features:

1. Dashboards with key metrics
2. Trend analysis over time
3. Adherence scores (calculated from check-ins)
4. Detailed workout progress per exercise
5. Weight/measurement trend charts (line graphs)
6. Before/after photo timeline
7. Adherence heatmap (calendar view—green/yellow/red)
8. Personal records board (PRs per exercise)
9. Workout volume progression (total lifted over weeks)
10. Exportable progress reports (PDF)
11. Goal achievement celebrations
12. Period comparison ("This month vs. last month")

**Insights Discovered:**
- Two distinct app experiences needed: complex web for professionals, simple mobile for clients
- Gamification elements (streaks, PRs, celebrations) drive client engagement
- PDF export is critical for professional documentation

**Notable Connections:**
- Adherence scores can trigger non-adherence alerts automatically
- Template library + drag-and-drop = efficient plan creation workflow

---

### Technique 3: Gap Analysis vs. Existing Platform — 20 min

**Description:** Compared brainstorm results against existing NutriPro System Documentation to identify missing functionality.

#### Critical Gaps Identified:

1. **Blood Tests Module**
   - Track lab results over time: HDL, LDL, Triglycerides, Cholesterol, Blood Sugar, HbA1c, Albumin, Iron, Vitamin D, B12, Folate, TSH, T3, T4, Creatinine, Uric Acid
   - Graphing capabilities for trends
   - Reference range display

2. **Medical Questionnaire**
   - Structured health history intake form
   - Yes/No responses with notes column
   - "Treated" column for conditions under treatment
   - Configurable questions through admin

3. **Supplements Module**
   - Separate from medications
   - Track client supplement intake
   - Name, type, dosage, notes, interactions

4. **Body Composition Calculator**
   - Skinfold measurements (7 sites): Triceps, Midaxillary, Chest, Subscapular, Suprailium, Abdominal, Thigh
   - Jackson-Pollock formulas (3-site methods)
   - Calculated fat % output

5. **Detailed Body Metrics (beyond weight/fat%)**
   - Fat Mass (kg)
   - FMMI (Fat-Free Mass Index)
   - %BIA (Bioelectrical Impedance Analysis)
   - TBW (Total Body Water)
   - Body Measurements: Belly, Waist, Arm, Forearm
   - Blood Pressure (Systolic/Diastolic)
   - Hand Grip Strength (H.GRIP)

6. **RMR & Metabolic Settings**
   - RMR Coefficient (based on O2 consumption)
   - Activity Coefficient (adjustable multiplier)
   - Training Type checkboxes (Strength, Aerobic)

7. **Admin/Configuration Modules**
   - RMR Coefficients management
   - Activity Coefficients management
   - Fat Percentage Ranges (by age/gender)
   - Blood Test Parameters (configurable)
   - Food Property Units (g, mg, mcg, IU, etc.)
   - Food Properties (nutritional attributes)
   - Meal Types configuration
   - Client Types management
   - Plan Types
   - Exercise Types
   - Cities list

8. **SMS Templates**
   - Saved SMS messages for client communication

9. **Hebrew/RTL + English Bilingual Support**
   - Existing system is Hebrew-first with RTL layout
   - New system must support bilingual UI

**Insights Discovered:**
- Existing system is far more feature-rich than initially discussed
- Clinical features (blood tests, body composition, medical questionnaire) are essential
- Configuration/admin layer is substantial — many reference tables needed

**Notable Connections:**
- Blood tests + body composition + data tracking = comprehensive health monitoring
- All configuration modules feed into the main workflow modules

---

## Idea Categorization

### Immediate Opportunities
*Ideas ready to implement in MVP*

1. **Client Management System**
   - Description: Complete client profiles with personal info, medical info, food preferences, medications, supplements, notes
   - Why immediate: Foundation of the entire platform
   - Resources needed: Database schema, CRUD APIs, secure storage

2. **Dictionary / Master Data System**
   - Description: Foods, exercises, medications, supplements, diseases, all configuration tables
   - Why immediate: Powers all other features; partner has existing data to import
   - Resources needed: Data import tools, comprehensive schema, search/filter UI

3. **Meal Menu Builder**
   - Description: Create daily/weekly menus from food database with real-time nutritional calculations
   - Why immediate: Core value proposition for nutritionists
   - Resources needed: Food database, calculation engine, intuitive builder UI

4. **Workout Plan Builder**
   - Description: Create programs from exercise database with sets/reps/weight specifications
   - Why immediate: Core value proposition for nutritionists
   - Resources needed: Exercise database, plan template system

5. **Client Mobile App — Checklists**
   - Description: One-tap check-off for meals and workouts, daily summary view
   - Why immediate: Core value proposition for clients; major differentiator from existing system
   - Resources needed: Mobile development (React Native or similar), sync infrastructure

6. **Data Tracking (Expanded)**
   - Description: Weight, fat%, all body metrics, measurements, blood pressure, notes with graphing
   - Why immediate: Core clinical feature
   - Resources needed: Time-series data handling, charting library

7. **Blood Tests Module**
   - Description: Track lab results over time with reference ranges and trend graphs
   - Why immediate: Essential clinical feature from existing system
   - Resources needed: Parameter configuration, date-based tracking, graphing

8. **PDF Generation**
   - Description: Export meal plans, workout plans, and progress reports as PDFs
   - Why immediate: Required for professional documentation
   - Resources needed: PDF generation library, template system

9. **Bi-directional Sync**
   - Description: Real-time or near-real-time sync between web and mobile
   - Why immediate: Enables the core web + mobile architecture
   - Resources needed: Sync infrastructure, conflict resolution strategy

### Future Innovations
*Ideas requiring development/research*

1. **Advanced Visualization Dashboard**
   - Description: Adherence heatmaps, workout volume progression, period comparisons, body composition pages
   - Development needed: Advanced charting, data aggregation pipelines
   - Timeline estimate: Post-MVP, 2-3 months

2. **Template Library with Sharing**
   - Description: Reusable meal plans and workout programs, potentially shareable between nutritionists
   - Development needed: Template versioning, sharing/permissions system
   - Timeline estimate: Post-MVP, 1-2 months

3. **Before/After Photo Timeline**
   - Description: Client uploads photos, nutritionist reviews visual progress
   - Development needed: Secure image storage, timeline UI, privacy controls
   - Timeline estimate: Post-MVP, 1-2 months

4. **Calendar Integration**
   - Description: Sync meetings with Google Calendar / Outlook
   - Development needed: OAuth integrations, two-way sync
   - Timeline estimate: Post-MVP, 1 month

5. **Offline Mobile Mode**
   - Description: Mobile app works without internet, syncs when reconnected
   - Development needed: Local storage, sync queue, conflict resolution
   - Timeline estimate: Post-MVP, 2-3 months

### Moonshots
*Ambitious, transformative concepts*

1. **AI-Powered Meal Suggestions**
   - Description: Based on client preferences, restrictions, and goals, AI suggests meal plans
   - Transformative potential: Dramatically reduces nutritionist planning time
   - Challenges to overcome: Accuracy, dietary safety, professional liability

2. **Wearable/Fitness Tracker Integration**
   - Description: Import data from Apple Watch, Fitbit, Garmin, gym equipment
   - Transformative potential: Automatic activity logging, richer data
   - Challenges to overcome: Multiple API integrations, data normalization

3. **Research Platform**
   - Description: Aggregate anonymized data for nutritional research insights
   - Transformative potential: Industry-wide impact, potential revenue stream
   - Challenges to overcome: Privacy compliance, data anonymization, research partnerships

4. **White-Label Platform**
   - Description: Allow other nutrition practices to use the platform under their brand
   - Transformative potential: SaaS business model, scalable revenue
   - Challenges to overcome: Multi-tenancy architecture, customization framework

### Insights & Learnings
*Key realizations from the session*

- **Desktop → Web+Mobile is the core transformation**: The existing NutriPro is feature-rich but trapped on desktop. The new platform's value is making this accessible everywhere.

- **Two UX philosophies required**: Nutritionists need power-user interfaces with depth; clients need dead-simple, one-tap interactions. These are fundamentally different design challenges.

- **Dictionary is the foundation**: All features depend on comprehensive, well-structured master data. This must be built right from day one.

- **No feature regression**: The existing system has 10+ years of evolved functionality. Users will expect ALL of it, plus the new benefits.

- **Bilingual is non-negotiable**: Hebrew (RTL) + English support is required from the start, not an afterthought.

- **Sync architecture is critical**: The web ↔ mobile real-time sync is the technical linchpin. Get this wrong and the whole value proposition fails.

---

## Action Planning

### Top 3 Priority Ideas

#### #1 Priority: Dictionary / Master Data System
- **Rationale:** Everything else depends on this. Foods, exercises, medications, supplements, diseases, and all configuration tables must exist before menus and plans can be created.
- **Next steps:**
  1. Design complete database schema for all entity types
  2. Build data import tools for partner's existing tables
  3. Create admin CRUD interfaces for all reference data
  4. Implement search, filter, and categorization
- **Resources needed:** Database architect, backend developer, partner's existing data exports
- **Timeline:** Weeks 1-4

#### #2 Priority: Nutritionist Web App Core (Client + Menu + Workout + Tracking)
- **Rationale:** The nutritionist workspace is the primary interface. Client management, meal builder, workout builder, and data tracking form the minimum viable product.
- **Next steps:**
  1. Design UI/UX for nutritionist dashboard
  2. Build client management module
  3. Build meal menu builder with nutritional calculations
  4. Build workout plan builder
  5. Build data tracking with graphing
- **Resources needed:** UX designer, frontend developer(s), backend developer(s)
- **Timeline:** Weeks 3-12

#### #3 Priority: Client Mobile App (Checklists + Progress)
- **Rationale:** This is the major differentiator from the existing desktop system. Clients need a simple way to track adherence daily.
- **Next steps:**
  1. Design mobile UX (one-tap philosophy)
  2. Build checklist interfaces for meals and workouts
  3. Build workout logging (weight/reps/sets)
  4. Build progress dashboard
  5. Implement bi-directional sync
- **Resources needed:** Mobile developer (React Native recommended), sync infrastructure
- **Timeline:** Weeks 6-14

---

## Reflection & Follow-up

### What Worked Well
- Fast Problem Framing quickly aligned on user roles and pain points
- Feature Storm by role created comprehensive coverage
- Gap Analysis against existing documentation caught critical missing features
- Partner's existing system documentation was invaluable

### Areas for Further Exploration
- **Sync architecture:** Need deep technical design for real-time bi-directional sync
- **Blood test workflows:** How do nutritionists typically enter and review lab data?
- **Body composition UX:** What's the ideal flow for entering skinfold measurements?
- **Mobile offline mode:** How critical is this for MVP vs. post-MVP?

### Recommended Follow-up Techniques
- **User Journey Mapping:** Map the end-to-end flow for both nutritionist and client personas
- **Competitive Analysis:** Review existing nutrition apps (MyFitnessPal, Cronometer, etc.) for UX inspiration
- **Technical Spike:** Prototype the sync architecture early to de-risk

### Questions That Emerged
- What's the expected client load per nutritionist? (Affects scale requirements)
- Will multiple nutritionists share clients? (Affects permissions model)
- Are there regulatory/compliance requirements in Israel for health data?
- What's the partner's tolerance for feature differences during migration?

### Next Session Planning
- **Suggested topics:** Technical architecture decisions, detailed UX flows, data migration strategy
- **Recommended timeframe:** Within 1 week
- **Preparation needed:** Partner to export sample data from existing system; review competitive apps

---

## Appendix: Complete Feature List by Priority

### 🔴 MUST HAVE (MVP)

| # | Feature | Module |
|---|---------|--------|
| 1 | Dictionary / Master Data System (all entities) | Core |
| 2 | Secure authentication & data protection | Core |
| 3 | Client management (profiles, status, types, medical info) | Nutritionist |
| 4 | Medical Questionnaire (structured intake) | Nutritionist |
| 5 | Meal menu builder (with nutritional calculations) | Nutritionist |
| 6 | Workout plan builder | Nutritionist |
| 7 | Blood Tests Module (lab tracking + graphing) | Nutritionist |
| 8 | Body Composition Calculator (skinfold + formulas) | Nutritionist |
| 9 | Data Tracking (expanded metrics: weight, fat%, FMMI, TBW, measurements, BP, grip) | Nutritionist |
| 10 | Supplements Module | Nutritionist |
| 11 | RMR & Metabolic Settings | Nutritionist |
| 12 | Progress dashboard (with basic graphs) | Nutritionist |
| 13 | PDF generation (plans + reports) | Nutritionist |
| 14 | Client mobile app — daily checklists (meals + workouts) | Client |
| 15 | Workout progress logging (weight, reps, sets) | Client |
| 16 | Basic progress view (adherence, weight trend) | Client |
| 17 | Async bi-directional sync (web ↔ mobile) | Core |
| 18 | Hebrew/RTL + English bilingual support | Core |
| 19 | Admin configuration modules (all reference tables) | Admin |

### 🟠 SHOULD HAVE (MVP+)

| # | Feature | Module |
|---|---------|--------|
| 20 | Template library (meal plans, workout programs) | Nutritionist |
| 21 | Session notes per client | Nutritionist |
| 22 | Client Summary Bar (quick view on menu screen) | Nutritionist |
| 23 | "Is Primary" food flag | Nutritionist |
| 24 | Graph generation options (height/weight/BMI/body comp) | Nutritionist |
| 25 | Meeting scheduling | Both |
| 26 | Push notifications (reminders) | Client |
| 27 | Streak tracking + milestones | Client |
| 28 | Personal records (PRs) | Client |
| 29 | Daily summary card | Client |
| 30 | SMS templates | Nutritionist |

### 🟡 COULD HAVE (Future)

| # | Feature | Module |
|---|---------|--------|
| 31 | Drag-and-drop plan builder | Nutritionist |
| 32 | Version history for plans | Nutritionist |
| 33 | Alert dashboard (off-track clients) | Nutritionist |
| 34 | Quick-glance client cards | Nutritionist |
| 35 | Auto-calc nutritional values | Nutritionist |
| 36 | Before/after photo timeline | Both |
| 37 | Adherence heatmap | Both |
| 38 | Workout volume progression | Client |
| 39 | Period comparison | Both |
| 40 | In-app meeting booking | Client |
| 41 | Post-meeting summary | Both |
| 42 | Non-adherence alerts | Nutritionist |
| 43 | Calendar integration | Nutritionist |
| 44 | Offline mobile mode | Client |
| 45 | Goal achievement celebrations | Client |

### ⚪ WON'T HAVE (Deferred)

| Feature | Reason |
|---------|--------|
| Client cohort views | User removed |
| Bulk operations | User removed |
| Photo logging (meals) | User removed |
| Nutritionist quick-notes | User removed |
| Pre-meeting questionnaire | User removed |
| Weekly automated check-in | User removed |
| Chat | Nice-to-have, deferred |
| Research platform | Nice-to-have, deferred |
| AI meal suggestions | Moonshot |
| Wearable integration | Moonshot |
| White-label platform | Moonshot |

---

## Appendix: Dictionary Entity Schema (Reference)

| Entity | Key Fields |
|--------|------------|
| **Foods** | Name, category, serving size, calories, protein, carbs, fat, fiber, all micronutrients, custom tags, customer description |
| **Exercises** | Name, muscle group, equipment, type (strength/aerobic/flexibility), difficulty, instructions, video/image link |
| **Medications** | Name, category, interactions, dietary notes |
| **Supplements** | Name, type, dosage, notes, interactions |
| **Diseases/Conditions** | Name, dietary considerations, contraindicated foods/exercises, treatment notes |
| **Blood Test Parameters** | Parameter name, unit, reference ranges (by age/gender), notes |
| **RMR Coefficients** | Name, value, description |
| **Activity Coefficients** | Activity level, multiplier |
| **Fat % Ranges** | Age range, gender, healthy/unhealthy thresholds |
| **Meal Types** | Name, typical time, display order |
| **Client Types** | Name, description |
| **Client Status** | Name (active/inactive/etc.) |
| **Plan Types** | Name, description |
| **Exercise Types** | Name, description |
| **Food Properties** | Property name, unit, description |
| **Food Property Units** | Unit symbol, full name |
| **Cities** | Name |

---

## Appendix: Existing System Limitations → New System Solutions

| Current Limitation | New System Solution |
|--------------------|---------------------|
| Desktop-only, no mobile/web | Modern web app + native mobile app |
| Single-user architecture | Multi-user with role-based access |
| No client portal or self-service | Dedicated client mobile app |
| Manual data entry for reference data | Bulk import + modern CRUD interfaces |
| Limited visualization (basic graphs) | Rich dashboards, heatmaps, trend analysis |
| Dated visual design | Modern, responsive UI with bilingual support |
| Dense information display | Progressive disclosure, clean UX |
| No external integrations | Calendar integration (future), PDF export |
| No between-meeting interaction | Real-time sync, notifications, in-app communication |

---

*Session facilitated using the BMAD-METHOD™ brainstorming framework*

