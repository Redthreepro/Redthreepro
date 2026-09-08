# Ryan Faber

Grand Rapids, MI · redthreepro@gmail.com · [linkedin.com/in/ryan-faber-864b77426](https://www.linkedin.com/in/ryan-faber-864b77426) · [github.com/Redthreepro](https://github.com/Redthreepro)

**AI Application Developer · Technical Product Builder**

Production AI systems, business software, and automation for real-world operations, built by directing AI coding agents and owning the result.

## Summary

I take operational problems out of real businesses and turn them into production software. Fifteen years inside construction and residential real estate from three seats (photographing and marketing homes, representing buyers and sellers as a licensed agent, inspecting properties), then rebuilding my employer's operating stack around AI. The platform I built is used daily by 100% of the inspectors at a 12-to-15-inspector operation on pace for about 5,000 inspections in 2026. Full lifecycle, solo: problem selection, architecture, AI-directed implementation, deployment, cost governance, incident response, and adoption. Eight years in the U.S. Army before any of it.

## Experience

### Technology Lead & Residential Inspector — residential and commercial inspection company, Grand Rapids, MI
**June 2024 – Present** · engaged through Red Three Productions (my own business) · employer name on request

- **Designed, built, and operate a production AI platform adopted by 100% of the field crew**: 13 active inspectors, ~79 logins/week. Streaming AI assistant grounded in company procedures via retrieval, LLM photo analysis, in-house report writer that replaced commercial software, scheduling integration, training with AI grading, admin console. React PWA on Firebase; 1,078 commits over 15 months; 26 cloud functions; CI gate of 1,836 automated tests.
- **Built production RAG with no added infrastructure**: company documents embedded and stored as native Firestore vector fields with cosine retrieval and a keyword fallback. Chose vectors-in-Firestore over a dedicated vector database and documented the revisit trigger.
- **Moved the highest-risk AI task into deterministic code**: equipment manufacture dates decode across 25 manufacturer serial schemes with 57 cited samples and 63 passing tests, plus a prompt-level learning loop from inspector corrections in production.
- **Made AI affordable at small-business scale**: per-user daily caps, a monthly spend ceiling, per-function instance limits, and tiered model selection, all designed in before launch.
- **Ran production solo through five incidents** (stale service-worker builds, iOS auth loop, storage misconfiguration, IAM over-restriction, a runtime upgrade that silently dropped every function's public invoker), turning each into a systemic fix and a written rule, including a post-deploy probe script.
- **Turned a decade of company records into data**: 8,193 legacy reports indexed in one 30-minute run with zero failures; 5,225 reports mined into 88,286 structured defect findings for a continuing-education class delivered to referral partners; 1.6 million photos classified with a local-model-first, cloud-fallback pipeline; 95% of a two-million-photo index rebuilt from report HTML after a drive failure.
- **Built and run a production outreach automation on self-hosted n8n**: property-listing ingest with service-area and well/septic rules, inspector drive-time qualification, lead routing, and a guardrail layer (send window, per-run and daily caps, per-domain limit, 7-day cooldown, ramp-up mode, kill switch, test and dry-run modes) with persistent state and failure logging, all controlled from a spreadsheet the office can edit. 4,019 emails sent January to August 2026 at 95% delivery, 2% hard bounce, and zero spam complaints. The v1 pipeline was built with the guardrails first and deliberately held back until the compliance posture was right.
- **Shipped a local-first AI video studio** as Electron desktop installers (33 builds) so a non-technical owner produces branded promo videos from a form, with local TTS and voice cloning and no metered cloud cost.

### Founder — Site Sketch Pro (sitesketchpro.com)
**February 2026 – Present** · personal product, live

- Browser-based site-plan tool for well, septic, and contractor inspections: address to satellite background, OpenStreetMap footprint auto-trace, domain symbol kits with setback rules, branded PDF export. React 19 with the React Compiler, Konva canvas engine (~10,500 lines), Firebase, Vercel serverless with Upstash Redis rate limiting, Sentry, Vitest, GitHub Actions. ~70,000 lines; 206 commits. Free trial and pricing live; payments not yet integrated.

### Licensed Real Estate Agent — Five Star Real Estate, Grand Rapids, MI
**2020 – 2023**

- Represented residential buyers and sellers through the full transaction lifecycle. The customer whose workflow, referral relationships, and reporting expectations I now build software for.

### Owner / Operator — Red Three Productions / Red Three Pro, Grand Rapids, MI
**August 2010 – Present** · independent

- Built and operate a real-estate media, design, and technology business: a decade of real estate photography for a consistent book of about ten agents, client websites (WordPress, Squarespace), graphic design, and video production, then software and automation. Owned client acquisition, pricing, production, and delivery throughout.

### United States Army — Armor Crewman, M1 Abrams · 4th Infantry Division, Fort Hood, TX
**July 2002 – July 2010** · active duty 2002–2005, Reserve/IRR through 2010 · combat deployment, Iraq 2003–2004

- Accountable for roughly $17M in equipment (4 M1 Abrams tanks, 2 Humvees, weapon systems for a 6-soldier team) and led a team of six, at age 20.
- Selected out of basic training for six additional weeks of advanced technology and weapons-systems training (about 5% of the class). Qualified Expert in personal weaponry; youngest tanker in 1-66 Armor to qualify Expert on the Tank Table 12 gunnery course.

## How I work

AI coding agents write most of the implementation in my projects. I define the problem and the constraints, make the architecture and product decisions, direct the agents, review and test their output, deploy, field-test with real users, handle incidents, and iterate. Every project on my GitHub profile documents which parts were mine and which were the agents'.

## Technology

- **Frontend:** React, Vite, Next.js App Router, Tailwind, PWA/service workers, Konva, Leaflet, Electron
- **Backend and data:** Firebase (Auth, Firestore, Cloud Functions, Storage, Hosting, Secret Manager), Node/Express, Postgres with Prisma and Supabase, SQLite, Upstash Redis
- **AI and automation:** OpenAI, Anthropic, and Gemini APIs; embeddings and retrieval; LLM vision; streaming; n8n workflow orchestration; local models (Ollama, CLIP, Kokoro TTS, voice cloning); Claude Code as a build tool
- **Integration and ops:** REST APIs, webhooks, Google Workspace integrations, Apify; Vercel, Firebase Hosting, GitHub Actions, Sentry, Vitest and Playwright, Electron packaging, IAM and secrets management, incident response

## Selected public work

Seven documentation-only case studies at [github.com/Redthreepro](https://github.com/Redthreepro): field-inspection AI platform, Site Sketch Pro, inspection records and photo data engineering, local-first AI video studio, Red Three Discovery, compliance-guarded outreach automation, Jarvis operations protocol.

## Education

Coopersville High School, 2002 · Michigan real estate pre-licensure coursework
