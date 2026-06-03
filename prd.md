Project Title
Trackify

One Sentence Pitch
My project is a program that lets athletes log, upload, and analyze their workouts across 34 different sports — turning raw training data into clear stats, charts, and personal bests.

Target User
This project is for recreational and competitive athletes who want one place to track all their sports — runners who use a Garmin watch, gym-goers logging sets and reps, soccer players counting goals — without paying for a subscription app like Strava or MyFitnessPal.

Purpose
This is useful because most tracking apps only focus on one sport (running or cycling), and the ones that cover multiple sports charge monthly fees. Trackify is free, works with files exported from any fitness device, and shows stats specific to each sport — pace for running, goals for soccer, sets/reps for weightlifting — instead of forcing everything into the same generic form.

MVP
The smallest working version will let a user log one running session manually (distance, time, date), save it to a database, and display the total distance on a dashboard.

Must Have Features
Manual activity logging with sport-specific fields (distance, duration, calories, heart rate)
GPX file upload so GPS data from Garmin/Apple Watch imports automatically
A dashboard showing total distance, calories, time active, and a weekly trend chart
Nice To Have Features
Personal bests — automatically tracks your fastest pace, longest run, etc. per sport
Per-sport breakdown cards showing stats only for sports you've actually done
Stretch Feature
Apple Health and Samsung Health ZIP export parsing — so users can bulk-import months of data from their phone with one file
Python Skills I Might Use
Functions
Reusable helpers for parsing GPX files (extracting distance, pace, elevation from GPS coordinates), calculating pace from distance + time, and detecting which sport a file belongs to based on its contents.

Lists
Storing the 34 sport categories, weekly trend data (a list of 12 weekly summaries), and split-by-kilometre pace breakdowns for each GPS activity.

Dictionaries
Sport configuration map — a dictionary keyed by sport name where each value holds which fields to show in the log form (e.g. soccer gets "goals scored", weightlifting gets "sets" and "reps"). Also used for building the JSON response objects sent to the frontend.

APIs
FastAPI to build the REST API backend. The frontend calls endpoints like GET /api/activities and POST /api/activities to read and write data.

File I/O
Reading uploaded .gpx, .tcx, and .zip files (Apple Health / Samsung Health exports), parsing their XML or JSON contents, and extracting workout data from them.

OOP
The database connection is managed as a singleton. GPX/TCX file parsers are structured as functions with clear input/output so they can be tested independently.

Error Handling
Try/except blocks around file parsing (malformed GPX files), database queries (connection failures), and API inputs (missing required fields) — with meaningful error messages returned to the user instead of server crashes.

Data Plan
What data does my project need?
Each activity needs: sport type, date, duration, distance, calories, average heart rate, pace, and sport-specific extras (goals, sets, elevation, etc.).

Where will the data come from?
Two sources: users type it in manually through a form, or they upload a file exported from their fitness device (Garmin, Apple Watch, Samsung Health).

How will I store or organize the data?
PostgreSQL database with an activities table. Sport-specific extras (goals, sets, reps) go in a metadata JSON column so the same table works for all 34 sports without needing 34 different tables.

First Tiny Step
The first thing I need to build is a Python function that accepts a sport name, distance (km), and duration (minutes) and saves one row to a PostgreSQL database — then reads it back and prints it.

Possible Risk
The hardest part might be parsing GPX files correctly — GPS tracks from different devices (Garmin, Apple Watch, Wahoo) format their XML slightly differently, so the parser needs to handle multiple variations without breaking on edge cases like missing heart rate data or tracks with only a single point.
