# Trivia Royale — Project Status

**Last updated:** 2026-10-18
**Current phase:** 1 — Auth & Profiles
**Next action:** Install Supabase JS client, build register/login/logout pages

---

## Phase Checklist

### Phase 0 — Foundation ✅ COMPLETE
- [x] Create Next.js project with TypeScript + Tailwind
- [x] Initialize Git and push to GitHub (apexeagle00/trivia-royale)
- [x] Connect Vercel for auto-deploys (trivia-royale-three.vercel.app)
- [x] Create Supabase project and connect keys (wyfnnujophmekulaaryv)

### Phase 1 — Auth & Profiles ⬅️ CURRENT
- [ ] Register / login / logout (Supabase Auth)
- [ ] Username and display name setup
- [ ] Protected routes (can't access game without account)
- [ ] Basic profile page

### Phase 2 — Question Database
- [ ] Design questions table schema
- [ ] Seed 150+ questions across 4-6 categories
- [ ] Answer normalization logic (case-insensitive, trimmed)
- [ ] Test answer matching

### Phase 3 — Core Game Engine
- [ ] Matchmaking queue (write to DB, poll for match)
- [ ] Game room creation
- [ ] Supabase Realtime subscription (both players watch the same room)
- [ ] Server-authoritative question broadcasting
- [ ] Answer submission → API route → server timestamp → correct check → broadcast result
- [ ] Scoring (first correct answer = 1 point)
- [ ] End game logic (10 questions → winner declared)
- [ ] Save match result to DB

### Phase 4 — Stats & Leaderboard
- [ ] Win/loss/accuracy per player
- [ ] Match history page
- [ ] Public leaderboard (top players by wins)
- [ ] Category performance stats

### Phase 5 — Advanced Features
- [ ] Private rooms with room codes
- [ ] Elo rating system
- [ ] Ranked / casual / impossible game modes
- [ ] Customizable win scores
- [ ] Streaks, badges, progression UI

---

## Completed Work
*Nothing yet — planning stage complete, ready to build.*

---

## Active Blockers
*None.*

---

## Notes
- Two-browser local testing: Chrome (User A) + Chrome Incognito (User B) → both hit localhost:3000
- Supabase Realtime connects to cloud even in local dev — real-time works from day one
- Vercel free tier: unlimited personal projects, auto-deploy on every GitHub push
- Supabase free tier: 500MB DB, 50K monthly active users, 200 concurrent Realtime connections
