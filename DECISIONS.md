# Trivia Royale — Technical Decisions

This file logs every major architectural or design decision, why it was made,
and what alternatives were considered. Never delete entries — append only.

---

## 2026-10-18 — Stack Selection

**Decision:** Next.js + Supabase + Vercel + TypeScript + Tailwind CSS

**Why:**
- Entire stack runs on free tiers through MVP
- Next.js API routes handle server-authoritative logic without a separate backend
- Supabase provides auth, PostgreSQL, and WebSocket real-time in one service
- Vercel auto-deploys from GitHub on every commit — zero DevOps overhead
- TypeScript catches bugs before they reach production
- Tailwind makes consistent UI fast to build

**Alternatives considered:**
- Socket.io on Railway/Fly.io — $5-7/month, unnecessary for MVP
- Ably for WebSockets — free tier exists but adds a third-party dependency
- Firebase instead of Supabase — less SQL control, worse free tier for DB size
- Plain Express server — requires VPS, ongoing cost, more maintenance

**Tradeoffs accepted:**
- Supabase Realtime limited to 200 concurrent connections on free tier (fine for MVP)
- Vercel serverless functions have cold starts (not a problem for trivia timing)

---

## 2026-10-18 — Server-Authoritative Answer Checking

**Decision:** All answer submissions go to a Next.js API route. The server records
`Date.now()` on arrival, validates the answer, and updates the database. The database
stores who answered first per question. Supabase Realtime broadcasts the result.

**Why:**
- Client clocks cannot be trusted — can drift, be manipulated, or vary by network lag
- Server timestamp is the only fair judge of "who answered first"
- Prevents cheating (can't fake an earlier timestamp from the browser)

**Alternative considered:** Client-side first-answer detection — rejected immediately.
Any client-side timing is gameable and unfair across different network conditions.

---

## 2026-10-18 — Answer Normalization Strategy

**Decision:** Normalize answers by: lowercase, trim whitespace, collapse multiple spaces.
Each question stores an array of accepted answers (handles common variations).

**Example:** Question: "What is the capital of France?"
Accepted: ["paris", "paris, france"]
Player types "Paris " → normalized to "paris" → match found → correct.

**Why:** Typed answers under time pressure will have capitalization variance. Strict
matching would create frustrating false negatives.

**Not doing:** Fuzzy matching (Levenshtein distance) for MVP — too complex, risk of
false positives on short answers.

---

## 2026-10-18 — Matchmaking Approach (MVP)

**Decision:** Simple queue table in PostgreSQL. Player joins queue → row inserted with
timestamp + player ID. A lightweight check (triggered by the joining player's API call
or a short polling interval) looks for another waiting player → pairs them → creates
a game_rooms row → both players subscribe to that room via Supabase Realtime.

**Why:** No persistent server needed. Works entirely within Vercel serverless + Supabase.

**Alternative considered:** Dedicated matchmaking service — overkill for MVP with small
user base.

**Known limitation:** If traffic grows large, this needs a more sophisticated queue.
Not a concern until well past MVP.

---

## 2026-10-18 — MVP vs Full Feature Scope

**Decision:** Build MVP first. MVP = public 1v1 matchmaking, 10-question matches,
server-authoritative scoring, win/loss saved, basic leaderboard. Everything else is Phase 5+.

**Why:** Get something playable and fun working first. Validate the core mechanic
(real-time competitive trivia) before investing in rating systems and advanced modes.

**Tony's input:** "Do not begin coding yet" — deliberate, methodical approach confirmed.
