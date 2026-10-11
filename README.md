# AI Learning SaaS Platform

A full-stack learning platform that combines AI-powered voice tutoring with user authentication, personalized learning sessions, tutor creation, bookmarks, session history, search, and subscription-ready access control.

## Overview

This application provides an interactive learning experience where users can discover AI tutors, create their own tutors, start voice-based learning sessions, and keep track of their learning activity.

The application is built as a modern Next.js SaaS platform with a PostgreSQL database, authentication, voice AI integration, monitoring, and a responsive component-based interface.

## Features

* AI-powered voice learning sessions
* Create custom AI tutors/companions
* Tutor discovery and search
* Subject and topic filtering
* User authentication and account management
* Bookmarked tutors
* Recent session history
* Personal tutor management
* Subscription and feature-limit support
* Responsive design for desktop and mobile
* Reusable UI components
* Form validation with Zod
* Error tracking and performance monitoring with Sentry
* PostgreSQL database integration through Supabase

## Tech Stack

### Frontend

* Next.js 15
* React
* TypeScript
* Tailwind CSS
* shadcn/ui
* Radix UI

### Backend & Data

* Next.js Server Actions
* Supabase
* PostgreSQL

### Authentication & Access Control

* Clerk
* Subscription and feature-based access control

### AI & Monitoring

* Vapi Voice AI
* Sentry

### Validation & Tooling

* Zod
* ESLint
* npm

## Application Architecture

```text
app/
├── authentication and route pages
├── companions/
├── my-journey/
└── other application routes

components/
├── reusable UI components
├── companion components
├── navigation
└── forms

lib/
├── actions/
│   └── server-side application actions
├── Supabase client
└── utility functions

constants/
└── application constants

types/
└── TypeScript type definitions

public/
└── static assets
```

## Database

The application uses Supabase PostgreSQL with three core tables.

### `companions`

Stores AI tutor/companion information.

| Column       | Type        | Description         |
| ------------ | ----------- | ------------------- |
| `id`         | UUID        | Primary key         |
| `name`       | text        | Companion name      |
| `subject`    | text        | Learning subject    |
| `topic`      | text        | Learning topic      |
| `voice`      | text        | Voice configuration |
| `style`      | text        | Conversation style  |
| `duration`   | integer     | Session duration    |
| `author`     | text        | User ID of creator  |
| `created_at` | timestamptz | Creation timestamp  |

### `session_history`

Tracks users' learning sessions and recently accessed companions.

### `bookmarks`

Stores companions bookmarked by users.

Both `session_history` and `bookmarks` reference `companions.id` through foreign keys.

## Environment Variables

Create a `.env` file in the project root.

```env
# Sentry
SENTRY_AUTH_TOKEN=

# Vapi
NEXT_PUBLIC_VAPI_WEB_TOKEN=

# Clerk
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=
CLERK_SECRET_KEY=
NEXT_PUBLIC_CLERK_SIGN_IN_URL=/sign-in
NEXT_PUBLIC_CLERK_SIGN_IN_FALLBACK_REDIRECT_URL=/
NEXT_PUBLIC_CLERK_SIGN_UP_FALLBACK_REDIRECT_URL=/

# Supabase
NEXT_PUBLIC_SUPABASE_URL=
NEXT_PUBLIC_SUPABASE_ANON_KEY=
```

Never commit `.env` or expose secret credentials in source control.

## Local Setup

### Prerequisites

* Node.js
* npm
* Git
* Supabase project
* Clerk application
* Vapi account/API key
* Sentry project/auth token

### Installation

```bash
git clone <your-repository-url>
cd saas-app
npm install
```

Create and configure `.env` with the required credentials.

Start the development server:

```bash
npm run dev
```

Open:

```text
http://localhost:3000
```

## Database Setup

Create a Supabase project and execute the required PostgreSQL schema in the Supabase SQL Editor.

The core schema contains:

* `companions`
* `session_history`
* `bookmarks`

The `session_history` and `bookmarks` tables use foreign keys referencing `companions`.

## Available Scripts

```bash
npm run dev       # Start the development server
npm run build     # Create a production build
npm run start     # Start the production server
npm run lint      # Run ESLint
```

## Security

* Authentication is handled through Clerk.
* Server-side operations use protected server actions.
* Supabase credentials are supplied through environment variables.
* Secret keys must never be committed to Git.
* Sentry is used for application monitoring and error tracking.

## Production Deployment

The application can be deployed to a platform that supports Next.js applications.

Before deploying, configure all required environment variables in the deployment platform and verify that the production Supabase, Clerk, Vapi, and Sentry configuration is available.

## Project Goals

This project demonstrates a modern full-stack SaaS architecture combining:

* Next.js application architecture
* Type-safe React development
* Server-side application logic
* PostgreSQL data management
* Authentication and access control
* Conversational AI
* Responsive UI development
* Production monitoring

## Status

**Development-ready / actively configured**

The application is configured for local development with Next.js, Supabase, Clerk, Vapi, and Sentry.
