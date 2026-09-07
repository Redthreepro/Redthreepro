# Ryan Faber

**AI Application Developer · Technical Product Builder**

I take operational problems out of real businesses and turn them into production software. I design the system, direct AI coding agents to build it, test it with the people who have to use it, deploy it, and keep it running.

Since mid-2025 that has meant a production AI platform used daily by an entire field-inspection crew, a commercial SaaS drawing tool, data pipelines over a decade of company records, and desktop apps a non-technical owner runs himself.

---

## What I build

- **AI applications for operations.** Assistants grounded in a company's own documents, photo analysis, report generation, and the cost controls that keep them affordable for a small business.
- **Business systems.** The scheduling, reporting, training, and admin tooling around the AI, built for people working from a phone in someone's basement.
- **Data and automation pipelines.** Batch systems over large archives of records and photos, and automations with the guardrails to be trusted unattended.
- **Packaged products.** Web apps, PWAs, and Electron desktop installers that ship to people who will never open a terminal.

## Selected work

### Field-inspection AI platform
*Private, in production since 2025 for a multi-inspector Michigan home-inspection company.*

A progressive web app the whole crew uses every day. AI assistant with streaming answers grounded in the company's own procedures via retrieval (Firestore native vector search, no separate vector database to operate). LLM photo analysis, including an equipment data-plate reader that decodes manufacture dates from manufacturer serial schemes and learns from inspector corrections. An in-house report writer that replaced commercial report software, with phone camera capture, a photo bank, voice dictation, and a client-facing published report. Scheduling-system integration, training module with AI grading, and an admin console for roles, usage, and cost.

- Adopted by **100% of field inspectors**; 13 active users, roughly 79 logins a week when last measured
- **1,078 commits** over 15 months; **26 cloud functions**; CI gate of **1,836 automated tests**
- Per-user daily AI caps, a monthly spend ceiling, and instance limits designed in before launch

[Read the case study](https://github.com/Redthreepro/inspection-ai-platform-case-study) (documentation only; the production repository stays private)

### Site Sketch Pro
*sitesketchpro.com — personally owned product, live.*

Browser-based site-plan tool for well, septic, and contractor inspections. Type an address, get a satellite background, auto-trace the building footprint from OpenStreetMap, place well and septic symbols with setback rules, and export a branded PDF. Includes an admin dashboard, rate-limited serverless API, error monitoring, CI with automated tests, and the legal pages (Terms, Privacy, DPA, SLA) a real product needs. Free trial and pricing tiers are live; payment processing is not yet wired.

- ~**70,000 lines** across the app, including a ~10,000-line canvas engine on Konva
- React 19 with the React Compiler, Firebase, Vercel, Upstash Redis, Sentry, Vitest, GitHub Actions

[Read the case study](https://github.com/Redthreepro/site-sketch-pro-case-study)

### Inspection records and photo data engineering
*Private. Batch pipelines over a decade of company archives.*

Three pipelines that made 8,000+ legacy inspection reports and roughly two million photos queryable: format fingerprinting across three generations of report HTML, defect extraction into a structured dataset, and photo classification using a local CLIP model first with cloud vision only for low-confidence images. After a drive failure took the sorted photo database, the sort was rebuilt from the reports themselves.

- **8,193 reports indexed with zero failures** in a single 30-minute run
- **88,286 defect findings** extracted from 5,225 reports at 100% parse success, feeding a data-driven continuing-education deck
- **1.6 million photo jobs** processed over three weeks of continuous runs

[Read the case study](https://github.com/Redthreepro/inspection-data-engineering-case-study)

### Local-first AI video studio
*Shipped as Windows installers; multi-brand version personally owned.*

A desktop app that lets a non-technical business owner fill in a form and get a branded promo video. An AI agent authors the composition from a brand kit, narration is generated locally, voice cloning runs locally, and FFmpeg renders the result. Nothing but the authoring step touches a cloud API. Packaged as Electron installers with a Mac build runbook written for a non-developer to follow.

- Two apps, **33 built installers**, 25 rendered campaign videos

[Read the case study](https://github.com/Redthreepro/local-first-ai-video-studio-case-study)

### Red Three Discovery
*Personal, in development. Deployed privately.*

A consultant's workbench for understanding how a business runs before proposing changes: discovery sessions, process maps, opportunity scoring, and branded reports and proposals. Its AI layer is provider-agnostic with a typed task registry, versioned prompts, and provenance on every output. Ships with a fully fictional showcase company so the whole workflow can be demoed without client data.

- Next.js 15, TypeScript, Prisma, Supabase Postgres

[Read the case study](https://github.com/Redthreepro/red-three-discovery-case-study)

**Also built:** a compliance-guarded outreach automation (kill switch, daily cap, per-agent cooldown, suppression list) that was deliberately never launched until the trigger was right; a file-based operations protocol that keeps scheduled AI agents, background jobs, and my own priorities in sync across projects; a batch video converter; a workstation provisioning installer.

## How I work

AI coding agents write most of the implementation in my projects. I do the parts that decide whether the software is any good:

- Find the workflow that is actually broken and define what "fixed" means
- Set the constraints: cost ceilings, offline behavior, mobile-first, who can see what
- Make the architecture and product calls, and write them down
- Direct the agents, review their output, and debug with them when it breaks
- Deploy, field-test with real users, handle the incidents, and iterate

The commit history on my repositories reflects this honestly. That is the method, not a shortcut.

## Technology

Used in systems I have designed, directed, deployed, and operated:

**Frontend:** React, Vite, Next.js App Router, Tailwind, PWA/service workers, Konva, Leaflet, Electron
**Backend and data:** Firebase (Auth, Firestore, Cloud Functions, Storage, Hosting), Node/Express, Next.js route handlers, Postgres with Prisma and Supabase, SQLite, Upstash Redis
**AI:** OpenAI, Anthropic, and Gemini APIs; embeddings and retrieval; LLM vision; streaming; local models (CLIP, Kokoro TTS, voice cloning); Claude Code as a build tool
**Ops:** Vercel, Firebase Hosting, GitHub Actions, Sentry, Vitest and Playwright, Electron packaging

I am not a traditional senior engineer in these stacks. I know them well enough to make sound design decisions, read and reason about what the agents produce, and own the result in production.

## Background

I came to software from operational work: construction, real estate, photography and media, home inspection, and running the day-to-day of a small business. I have spent years inside the workflows I now build for, which is why the software tends to fit how people actually work rather than how a spec says they should.

## Contact

- Email: redthreepro@gmail.com
- LinkedIn: https://www.linkedin.com/in/ryan-faber-864b77426
- Site Sketch Pro: https://sitesketchpro.com
