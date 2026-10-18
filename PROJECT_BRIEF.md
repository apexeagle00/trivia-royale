# Trivia Royale — Project Brief

## Concept
Competitive 1v1 online multiplayer trivia. Players compete in real-time — the first person
to type the correct answer wins the point. Inspired by BradyYourTutor's quiz format,
but with original branding, questions, and game mechanics.

## Vision
Level the playing field. A polished, competitive trivia platform that's actually fun to play —
like chess.com but for trivia knowledge.

## Stack
| Layer | Technology | Why |
|---|---|---|
| Frontend | Next.js 14 + TypeScript | Industry standard, fast, SEO-friendly |
| Styling | Tailwind CSS | Rapid, consistent design |
| Auth + DB | Supabase (PostgreSQL) | Free tier, built-in auth, real-time |
| Real-time | Supabase Realtime | WebSocket layer without a dedicated server |
| Hosting | Vercel | Free tier, auto-deploys from GitHub |
| Version control | GitHub (apexeagle00) | Free, industry standard |

## Accounts
- GitHub: apexeagle00
- Vercel: apexeagle00 (apex.agencies@hotmail.com)
- Supabase: apex.agencies@hotmail.com

## MVP Scope
- User registration and login (Supabase Auth)
- Public matchmaking (1v1)
- 10-question timed matches
- First correct typed answer wins the point (server-authoritative)
- Live scoreboard visible to both players during the match
- Win/loss record saved per player
- Basic leaderboard (top players by wins)
- Desktop browser support

## Full Feature Set (Post-MVP)
- Private rooms with room codes
- Elo/chess-style rating system
- Ranked, casual, and impossible difficulty modes
- Customizable win scores in private/casual matches
- Category selection (history, geography, science, sports, entertainment, general knowledge)
- Match history with accuracy and category breakdowns
- Win streaks, leaderboards, progression system
- Customizable player profiles

## Budget
**$100 total.** All infrastructure stays on free tiers through MVP.
Nothing gets purchased without Tony's explicit approval.

## Hard Rules
1. No sub-agents spawned without permission
2. No packages installed without explanation + approval
3. No paid services activated without approval
4. One milestone at a time — verify before moving on
5. Always commit to Git after meaningful changes
6. Update PROJECT_STATUS.md after every session
