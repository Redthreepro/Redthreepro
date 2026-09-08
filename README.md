<img src="assets/headshot.jpg" alt="Ryan Faber" width="140" align="right" style="border-radius:50%">

# Ryan Faber

**AI Application Developer · Technical Product Builder**

I take operational problems out of real businesses and turn them into production software. I design the system, direct AI coding agents to build it, test it with the people who have to use it, deploy it, and keep it running.

Since mid-2024 that has meant a production AI platform used daily by an entire field-inspection crew, a commercial SaaS drawing tool, data pipelines over a decade of company records, and desktop apps a non-technical owner runs himself.

## Case studies

Documentation-only repositories. Production source stays private; company work is anonymized.

| Project | What it is | Status |
|---|---|---|
| [Field-inspection AI platform](https://github.com/Redthreepro/inspection-ai-platform-case-study) | PWA with a retrieval-grounded AI assistant, LLM photo analysis, and an in-house report writer, used daily by 100% of a company's inspectors | Production since 2025 |
| [Site Sketch Pro](https://github.com/Redthreepro/site-sketch-pro-case-study) | Browser site-plan tool for well and septic inspections, on satellite imagery with OSM footprint auto-trace | Live SaaS, pre-revenue |
| [Inspection records and photo data engineering](https://github.com/Redthreepro/inspection-data-engineering-case-study) | Pipelines over 8,000 reports and ~2M photos, plus the rebuild after a drive failure | Run to completion |
| [Local-first AI video studio](https://github.com/Redthreepro/local-first-ai-video-studio-case-study) | Electron app that turns a form into a branded promo video with local TTS and voice cloning | Shipped v1 |
| [Red Three Discovery](https://github.com/Redthreepro/red-three-discovery-case-study) | Consultant's workbench: discovery notes to process maps, scored opportunities, and client deliverables | In development |
| [Compliance-guarded outreach automation](https://github.com/Redthreepro/outreach-automation-case-study) | Listing-triggered agent outreach with a kill switch, daily cap, per-agent cooldown, and suppression list. The v1 pipeline was held back until the compliance posture was right; the production rebuild on n8n has sent 1,000+ automated emails | Production (n8n rebuild); v1 case study |
| [Jarvis operations protocol](https://github.com/Redthreepro/jarvis-ops-protocol-case-study) | File-based protocol that keeps eight scheduled AI agents, background jobs, and a human's priorities coherent across sessions, at zero API cost | Running daily |

---

## What I build

- **AI applications for operations.** Assistants grounded in a company's own documents, photo analysis, report generation, and the cost controls that keep them affordable for a small business.
- **Business systems.** The scheduling, reporting, training, and admin tooling around the AI, built for people working from a phone in someone's basement.
- **Data and automation pipelines.** Batch systems over large archives of records and photos, and automations with the guardrails to be trusted unattended.
- **Packaged products.** Web apps, PWAs, and Electron desktop installers that ship to people who will never open a terminal.

## Selected work

### Field-inspection AI platform
*Private. In production since 2025 for a multi-inspector Michigan home-inspection company.*

The crew's single working surface: a streaming AI assistant grounded in the company's own procedures through Firestore native vector search, an equipment data-plate reader that learns from inspector corrections, and an in-house report writer that replaced commercial software. Scheduling integration, a training module with AI grading, and an admin console for roles, usage, and cost.

- **100% of field inspectors** adopted; 13 active users, ~79 logins a week when last measured
- **1,078 commits** over 15 months, **26 cloud functions**, CI gate of **1,836 automated tests**
- Per-user daily AI caps, a monthly spend ceiling, and instance limits designed in before launch

[Case study](https://github.com/Redthreepro/inspection-ai-platform-case-study)

### Site Sketch Pro
*[sitesketchpro.com](https://sitesketchpro.com). Personally owned, live.*

Enter an address, get a satellite background, auto-trace the building footprint from OpenStreetMap, place well and septic symbols with setback rules, export a branded PDF. Admin dashboard, rate-limited serverless API, Sentry, CI with tests, and the legal pages a real product needs. Free trial and pricing tiers are live; payment processing is not yet wired.

- ~**70,000 lines**, including a ~10,000-line Konva canvas engine
- React 19 with the React Compiler, Firebase, Vercel, Upstash Redis, Vitest, GitHub Actions

[Case study](https://github.com/Redthreepro/site-sketch-pro-case-study)

### Inspection records and photo data engineering
*Private. Batch pipelines over a decade of company archives.*

Deterministic parsers across three generations of report HTML, a defect dataset feeding a continuing-education class, an append-only report index, and a tiered photo classifier that runs a local CLIP model first and cloud vision only on low-confidence images. When the drive holding the sorted photo database died, the sort was rebuilt from the reports themselves.

- **8,193 reports** indexed with zero failures in one 30-minute run
- **88,286 defect findings** from 5,225 reports at 100% parse success
- **1.6 million photo jobs** processed; **95%** of a 2M-photo index re-bound after the drive failure

[Case study](https://github.com/Redthreepro/inspection-data-engineering-case-study)

### Local-first AI video studio
*Shipped as Windows installers; the multi-brand edition is personally owned.*

A non-technical owner fills in a form and gets a branded promo video. An AI agent authors the composition from a brand kit; narration and voice cloning run locally; FFmpeg renders. Only the authoring step touches a cloud service, on a subscription rather than a metered key. Delivered with a Mac build runbook a non-developer can follow.

- Two editions, **33 built installers**, 25 rendered campaign videos

[Case study](https://github.com/Redthreepro/local-first-ai-video-studio-case-study)

### Red Three Discovery
*Personal. In development, deployed privately.*

Discovery notes become editable process maps, a transparent 0 to 100 opportunity score, a phased roadmap, and printable reports and proposals. The AI layer routes every call through one runner with a typed task registry, versioned prompts, and provenance on every output. A fully fictional showcase company demonstrates the whole method without client data.

- Next.js 15, TypeScript, Prisma, Supabase Postgres; 2 of 11 AI tasks implemented, the rest labeled as planned

[Case study](https://github.com/Redthreepro/red-three-discovery-case-study)

**Also built:** a [compliance-guarded outreach automation](https://github.com/Redthreepro/outreach-automation-case-study) whose v1 was deliberately held back until the compliance posture was right, then rebuilt on self-hosted n8n where it now runs in production with over 1,000 automated emails sent; a [file-based operations protocol](https://github.com/Redthreepro/jarvis-ops-protocol-case-study) that keeps scheduled AI agents, background jobs, and my own priorities in sync across projects; a batch video converter; a workstation provisioning installer.

## How I work

AI coding agents write most of the implementation in my projects. I do the parts that decide whether the software is any good:

- Find the workflow that is actually broken and define what "fixed" means
- Set the constraints: cost ceilings, offline behavior, mobile-first, who can see what
- Make the architecture and product calls, and write them down
- Direct the agents, review their output, and debug with them when it breaks
- Deploy, field-test with real users, handle the incidents, and iterate

The commit history on my repositories reflects this honestly. That is the method, not a shortcut. Each case study has a "How it was built" section that separates my work from the agents' work.

## Technology

Used in systems I have designed, directed, deployed, and operated:

**Frontend:** React, Vite, Next.js App Router, Tailwind, PWA/service workers, Konva, Leaflet, Electron
**Backend and data:** Firebase (Auth, Firestore, Cloud Functions, Storage, Hosting), Node/Express, Next.js route handlers, Postgres with Prisma and Supabase, SQLite, Upstash Redis
**AI:** OpenAI, Anthropic, and Gemini APIs; embeddings and retrieval; LLM vision; streaming; local models (CLIP, Kokoro TTS, voice cloning); Claude Code as a build tool
**Ops:** Vercel, Firebase Hosting, GitHub Actions, Sentry, Vitest and Playwright, Electron packaging

I am not a traditional senior engineer in these stacks. I know them well enough to make sound design decisions, read and reason about what the agents produce, and own the result in production.

## Writing

Short pieces on decisions from the case studies:

- [Cost-first AI for a small business](writing/cost-first-ai-for-a-small-business.md)
- [RAG on Firestore without a vector database](writing/rag-on-firestore-without-a-vector-database.md)
- [The automation I didn't launch](writing/the-automation-i-did-not-launch.md)

## Background

I came to software from operational work: construction, real estate, photography and media, home inspection, and running the day-to-day of a small business. I have spent years inside the workflows I now build for, which is why the software tends to fit how people actually work rather than how a spec says they should.

## What I'm looking for

Roles where someone has to take an operational problem and turn it into working, maintained software, with AI as a tool rather than a slogan. Titles that fit: AI application developer, applied AI or AI implementation engineer, AI automation engineer, technical product builder, solutions engineer, forward-deployed engineer at a startup, or full-stack developer on a team that builds with AI agents.

- **Where:** Grand Rapids, Michigan (in office or hybrid), or fully remote. Not relocating.
- **How:** full-time, or contract-to-hire; open to a fractional or consulting engagement for the right problem
- **What I'm best at:** small teams and real operations, where the person building the software has also stood in the workflow
- **What I'm not:** a traditional senior engineer for a large-scale systems role. If the job is deep algorithms or a whiteboard interview, that's not me

Email works best. I reply within a day.

## Contact

- Email: redthreepro@gmail.com
- LinkedIn: https://www.linkedin.com/in/ryan-faber-864b77426
- Site Sketch Pro: https://sitesketchpro.com
- Resume: [PDF](resume/Ryan-Faber-Resume.pdf) · [Markdown](resume/Ryan-Faber-Resume.md)
