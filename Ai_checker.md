Entry 2
Date
June 3, 2026

AI Tool Used
Replit AI Agent

What I Asked AI
I asked the AI to add a time period filter to the Activities page — chips/buttons for "This Week", "This Month", "Last 3 Months", and "All Time" — so I can narrow down which sessions I'm looking at without scrolling through everything.

Why I Asked
The activities list was getting long and there was no way to filter by date. I had a sport filter already but wanted to also filter by when the activity happened. I knew the UI should have pill-shaped buttons but didn't know where to put the filtering logic — in the backend or the frontend.

What AI Gave Me
The AI added the four period buttons above the list. The filtering happens entirely on the frontend — it fetches up to 200 activities at once and then uses JavaScript's useMemo and Date comparison to filter which ones show. It also added a groupByMonth function so when you're viewing "All time" or "Last 3 months", activities automatically group under headers like "June 2026 — 4 sessions". The activity count badge updates live as you switch periods.

What I Used
All of it. The groupByMonth idea was something I hadn't thought of and makes the feed much easier to read.

What I Changed or Rejected
I asked about whether filtering should happen on the backend (sending the date range to the API) or the frontend (fetching all and filtering in JavaScript). The AI chose client-side filtering for simplicity. I understand the tradeoff — if someone had 10,000 activities this would be slow, but for a personal tracker with a few hundred sessions it's fine. I'm keeping it as-is for now.

What I Still Do Not Fully Understand
The useMemo hook — I see it wraps the filter logic and has a dependency array [allActivities, period], but I don't fully understand when React decides to re-run it vs. use the cached result. Is it every render? Only when the dependencies change?

My Next Step
Look up how useMemo works in the React docs and try writing a second useMemo in the same file for something else — maybe calculating the total distance across only the filtered activities — to practice using it.
