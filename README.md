# LifeOS | Personal Life Management Platform

**One place to manage your health, productivity, projects and learning.**

LifeOS is a personal life-management application designed to bring everyday activities into one unified dashboard. It combines nutrition tracking, fitness monitoring, task management, project organization and learning management, with AI-assisted meal analysis using food photographs or text descriptions.

**Live Application:** [LifeOS](https://life-os-orcin-pi.vercel.app/)

---

## Project Overview

Managing personal health, daily responsibilities and long-term goals across multiple applications can become fragmented.

LifeOS addresses this by bringing these activities together in a single application, with a shared dashboard and a consistent data-management experience.

The application also incorporates AI-assisted nutrition logging, allowing users to analyze meals using a photograph or a text description, review estimated nutritional values and save the results.

## Key Features

### 1. Dashboard
- Daily overview of nutrition and health information.
- Priority tasks and upcoming activities.
- Project and learning progress overview.
- Work-session analytics.
- Quick access to frequently used actions.

### 2. Nutrition Management
- Track meals across breakfast, lunch, dinner and snacks.
- Monitor calories, protein, carbohydrates, fat, fibre and sodium.
- Configure personal nutrition targets.
- Review nutrition history through a calendar.
- Store and browse meal photographs in a private Food Gallery.

### 3. AI-Powered Meal Analysis
- Analyze food using photographs or text descriptions.
- Generate estimated calories and nutritional information.
- Identify individual food items and quantities.
- Ask clarification questions when meal descriptions are ambiguous.
- Review and edit AI-generated estimates before saving.

### 4. Fitness Tracking
- Record workouts, exercise duration and notes.
- Track body-weight history.
- Visualize weight changes.
- Monitor progress toward a goal weight.

### 5. Task Management
- Centralized task management across categories.
- Priorities, due dates and estimated durations.
- Import tasks from pasted ChatGPT-generated lists.
- Move overdue tasks to the current day.

### 6. Project Management
- Create and manage personal project boards.
- Organize tasks within individual projects.
- Track focused work sessions.
- Review time spent through work-session history and analytics.

### 7. Learning Management
- Create and manage learning boards.
- Organize learning activities.
- Track focused study sessions.
- Review learning time and work-session history.

### 8. Personalization
- User profile and profile photograph.
- Light, dark and system themes.
- Configurable nutrition targets.
- Responsive desktop and mobile layouts.

---

## Technology Stack

| Area | Technologies |
|---|---|
| Frontend | React 19, JavaScript |
| Build Tool | Vite 8 |
| Styling | CSS |
| Icons | Lucide React |
| Backend | Supabase |
| Database | PostgreSQL |
| Authentication | Supabase Auth, Google OAuth |
| File Storage | Supabase Storage |
| Serverless Functions | Supabase Edge Functions, TypeScript, Deno |
| AI Integration | OpenAI Responses API |
| Deployment | Vercel |
| Testing | Node.js Test Runner, PGlite |

---

## System Architecture

LifeOS uses a modular frontend and a shared data-access layer to support both local browser storage and Supabase-backed operation.

```text
                  LifeOS
                     |
              React + Vite
                     |
             Application Context
                     |
                 Data Client
                  /       \
                 /         \
          Local Storage   Supabase
                              |
                +-------------+-------------+
                |             |             |
              Auth        PostgreSQL      Storage
                                           
                              |
                       Edge Function
                       analyze-meal
                              |
                       OpenAI API
```

### AI Meal Analysis Workflow

1. The user uploads a food photograph or enters a meal description.
2. The frontend sends the input to a Supabase Edge Function.
3. The function authenticates the user and validates the request.
4. The function calls the OpenAI Responses API using structured output.
5. Nutritional estimates are validated and returned to the application.
6. The user reviews and edits the results before saving the meal.

AI-generated nutritional values are estimates and should not be treated as medical measurements.

---

## Security and Data Protection

Security considerations incorporated into the application include:

- Supabase Row Level Security policies for user-specific database access.
- Private storage buckets for meal and profile photographs.
- Short-lived signed URLs for accessing private photographs.
- API credentials and service-role credentials kept in server-side environment secrets.
- Server-side validation and usage limits for AI meal analysis.
- OpenAI requests configured with `store: false`.

---

## Testing and Quality Assurance

The application includes automated testing across frontend logic, serverless functionality and database operations.

| Test Suite | Tests | Result |
|---|---:|---|
| Application Unit Tests | 148 | Passing |
| Edge Function Tests | 91 | Passing |
| Database Tests | 16 | Passing |
| **Total** | **255** | **All passing** |

Additional quality checks include ESLint and production builds for both Supabase-configured and local-only configurations.

---

## Deployment

The application is deployed using Vercel, with Supabase providing authentication, database services, private storage and serverless functionality.

**Live Application:** https://life-os-orcin-pi.vercel.app/

---

## Project Scope and Transparency

This repository is a public portfolio showcase of LifeOS. It contains project documentation and selected visual materials, not the complete application source code.

The original application source code is maintained separately in a private repository.

Some current implementation boundaries:

- The core database schema is maintained outside this showcase repository.
- Data is re-fetched when the application regains focus, reconnects or is refreshed; live real-time synchronization is not implemented.
- Local-only mode uses browser storage and does not support AI meal analysis.
- Multi-device usage has not been formally validated.
- Health-platform and wearable integrations are not currently implemented.

---

## Project

**LifeOS**

A personal software project focused on integrating everyday health tracking and productivity management into one application, while exploring practical AI integration, backend architecture and data protection.

**Live Demo:** [Open LifeOS](https://life-os-orcin-pi.vercel.app/)
