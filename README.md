# AI-Assisted Import Sourcing Tool (v1)

A practical sourcing workspace for importers of manufacturing/agricultural consumable inputs.

## Features in v1

- Sourcing intake form (item, volume, sector, spec notes)
- AI-assisted top-10 manufacturer search panel (mocked for v1)
- Outreach email generator with required compliance/pricing requests
- Supplier response tracker + scoring/ranking table
- Negotiation pipeline tracker per supplier:
  - Contacted → Responded → Compared → Negotiating → Samples Requested → Site Visit → Agreement

## Run

Open `index.html` in a browser.

## Deploy (Vercel)

This repo is static and deploys as-is on Vercel.

---

## Deliverable 1 — Tool Design (Summary)

### Core Modules

1. **Sourcing Intake & Demand Definition**
   - Capture target material, technical specs, monthly/quarterly volume, required certifications, and sector context.
2. **AI Supplier Discovery**
   - Agent searches web sources and builds top-10 candidate list with contact emails and metadata.
3. **Outreach Orchestration**
   - Auto-draft and dispatch supplier inquiry emails requesting spec fit, FOB per container, nominated export port, HS code, and compliance docs.
4. **Response Normalization & Comparison**
   - Parse incoming replies into structured fields for like-for-like comparison.
5. **Supplier Scoring & Shortlisting**
   - Rank suppliers by direct factory preference, quality/export credibility, and FOB competitiveness.
6. **Negotiation & Qualification Pipeline**
   - Stage management from first contact through samples/site visit/agreement.

### AI Agent Role by Stage

- **Intake stage:** clarify missing fields, validate requirement completeness.
- **Discovery stage:** find candidates, deduplicate entities, enrich contacts, classify manufacturer/agent.
- **Outreach stage:** generate tailored request emails and follow-up reminders.
- **Evaluation stage:** extract structured response data, identify outliers, score and rank suppliers.
- **Negotiation stage:** suggest playbooks (counter-offers, sampling terms, visit checklist).

### Critical Data to Track

- Item profile: material class, use-case, target spec, volumes, target port preference (NOR).
- Supplier master: legal name, domain, country, role (factory/agent), confidence score.
- Commercial: FOB/container, currency, lead time, MOQ, Incoterms, nominated export port.
- Compliance: HS code, MSDS/TDS/COA, origin docs, export permits.
- Performance: response speed, completeness, quality score, track record signals.
- Workflow: current pipeline stage, owner, next action, due date.

### Manufacturer vs Agent Classification Logic

- **Signals for manufacturer:** own production site evidence, factory certificates, manufacturing photos/capabilities, direct export records.
- **Signals for agent/trader:** broad multi-category catalog, no plant evidence, third-party forwarding behavior.
- **Output:** class + confidence (high/med/low), with rationale trace.

### Supplier Scoring Framework (v1)

`Total Score = Type Score + Quality/Track Record Score + Price Competitiveness Score`

- Type Score: manufacturer favored strongly over agent.
- Quality score: normalized from certifications, export evidence, response completeness.
- Price score: relative to lowest viable FOB quote (with outlier controls).

---

## Deliverable 2 — Written Overview (System Flow)

1. **User inputs** sourcing target and volume requirements.
2. **AI autonomously researches** top supplier candidates and enriches contact + role metadata.
3. **AI drafts outreach emails** with mandatory request fields.
4. **Responses are parsed** into comparable fields (FOB, HS code, docs, lead time, role evidence).
5. **Comparison engine scores suppliers** and flags:
   - agent vs manufacturer risk,
   - suspiciously low/high FOB outliers,
   - missing compliance documents,
   - weak export evidence.
6. **User reviews shortlist** and moves suppliers through negotiation pipeline.
7. **AI supports next actions** (follow-ups, sample requests, visit prep, negotiation prompts).

### Responsibility split

- **User-controlled:** final supplier decisions, negotiation approvals, stage transitions.
- **AI-handled:** research, classification, draft generation, extraction, scoring, and flags.

---

## Deliverable 3 — V1 Interface

Implemented in `index.html` using React components + embedded CSS/JS with realistic mocked AI hooks.
