# Sam-Shi-final-project
https://991c3288-f870-4ae7-8277-515f645e8fba-00-1a2vagbxo5dg4.kirk.replit.dev/activities
[README.md](https://github.com/user-attachments/files/28688757/README.md)
# Trackify

> Your personal training hub — log every rep, every km, every personal best.

Trackify is a full-stack sports tracking web app for athletes who want detailed stats across multiple sports in one place — without a subscription.

---

## What It Does

- **Log any sport** — 34 categories including running, cycling, swimming, weightlifting, soccer, basketball, yoga, and more
- **Upload GPS files** — import workouts directly from Garmin, Apple Watch, Wahoo, or Strava via GPX/TCX files
- **Import bulk data** — drag in an Apple Health or Samsung Health ZIP export to load months of history at once
- **See your stats** — weekly trend charts, per-sport breakdowns, total distance/calories/time, and auto-detected personal bests
- **Sport-specific fields** — running tracks pace and splits, soccer tracks goals scored, weightlifting tracks sets and reps
- **Google login** — sign in with your Google account, data is private to you

---

## Screenshots

> Dashboard with switchable trend chart (Distance / Calories / Heart Rate / Goals)

![Dashboard](attached_assets/image_1780523359294.png)

---

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend | React, TypeScript, Vite, Tailwind CSS |
| Backend | Python, FastAPI |
| Database | PostgreSQL |
| Auth | Clerk (Google login) |
| Charts | Recharts |
| API contract | OpenAPI + Orval codegen |
| File parsing | GPX, TCX, Apple Health ZIP, Samsung Health ZIP |

---

## Features

### Activity Logging
- Manual entry with sport-specific dynamic fields
- GPX/TCX file upload with automatic distance, pace, elevation, and heart rate extraction
- Apple Health and Samsung Health bulk import

### Dashboard
- Total distance, time, calories, and weekly session count
- 12-week bar chart — switch between Distance, Calories, Heart Rate, or Goals
- Per-sport stat cards (only shows sports you've actually done)
- Personal bests per sport (fastest pace, longest distance, etc.)

### Activities Feed
- Filter by sport and time period (This Week / This Month / Last 3 Months / All Time)
- Sessions grouped by month for easy scanning
- Click any activity for a detailed view with km-by-km splits

---

## Running Locally

### Requirements
- Python 3.11+
- Node.js 24+
- PostgreSQL database
- pnpm

### Setup

```bash
# Install dependencies
pnpm install

# Set environment variables
DATABASE_URL=your_postgres_connection_string
SESSION_SECRET=any_random_string

# Push database schema
pnpm --filter @workspace/db run push

# Start the API server
python artifacts/api-server/server.py

# Start the frontend
pnpm --filter @workspace/sports-tracker run dev
```

---

## Project Structure

```
trackify/
├── artifacts/
│   ├── api-server/         # Python FastAPI backend
│   │   └── server.py       # All API endpoints + file parsing
│   └── sports-tracker/     # React frontend
│       └── src/
│           ├── pages/      # Dashboard, Activities, Log, Detail
│           └── components/ # Shared UI components
├── lib/
│   ├── api-spec/           # OpenAPI contract (source of truth)
│   ├── api-client-react/   # Auto-generated React Query hooks
│   └── db/                 # Drizzle ORM schema
```

---

## Built With

This project was built as a personal sports tracker to replace paid apps like Strava and MyFitnessPal for athletes who train across multiple sports.
