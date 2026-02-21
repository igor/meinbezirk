# MeinBezirk Toolkit Blueprint — Design Document

**Date:** 2026-02-21
**Author:** Igor Schwarzmann / Claude
**Status:** Approved

## What We're Building

Transform the MeinBezirk GitHub repo from a single prototype into an open-source civic transparency toolkit. Not a product to install — a blueprint for how to approach civic transparency in any city.

## Core Decisions

**Audience:** Civic catalysts — people who see MeinBezirk and want to bring it to their city government. Also useful for municipal decision-makers who want to adopt it directly.

**Code's role:** Reference implementation. The `index.html` prototype stays at root (live at igorschwarzmann.com/meinbezirk) as one example of what the output looks like. The methodology is the product, not the code.

**AI framing:** AI-native methodology, but not locked to any vendor. Explicitly note that open-source, non-commercial, local solutions (Ollama, LM Studio, etc.) can do everything described.

**Data guidance:** Berlin case study as a worked example, then abstracted into a reusable pattern library. Include both official sources (ALLRIS, PADOK) and AI-powered research tools (Perplexity, etc.) as complementary approaches.

**Relevance filters:** Framed as a starting point, not a complete taxonomy. The Berlin prototype's three axes (Lebenslage, Ort, Anlässe) are one possible model. The toolkit teaches the method of finding relevant dimensions, not a fixed set.

**Tone:** GDS-style — plain, practical, direct. Short sentences. Active voice. Accessible to non-native speakers.

**Language:** German. International adaptation invited in English via CONTRIBUTING.md.

**Sources:** Referenced throughout for transparency and credibility. Collected in a dedicated `quellen/` directory.

## Repo Structure

```
meinbezirk/
├── index.html                   → Live prototype (root, keeps URL working)
├── README.md                    → Entry point: what, why, how to use this repo
├── CONTRIBUTING.md              → International invitation (English)
├── 01-verstehen/README.md       → Was bedeutet kommunale Transparenz
├── 02-daten-finden/README.md    → Wo und wie findet man die Daten
├── 03-relevanz-gestalten/README.md → Wie macht man Entscheidungen relevant
├── 04-umsetzen/README.md        → Gestaltungsprinzipien und technische Umsetzung
├── 05-betreiben/README.md       → Betrieb, Pflege, Governance
├── quellen/README.md            → All sources, references, inspirations
└── docs/plans/                  → Design documents (internal)
```

## Content Design Per Phase

### README.md (root)

Purpose: Entry point. Three jobs — explain, show, direct.

Content:
- One-paragraph description of MeinBezirk
- Link to live prototype (igorschwarzmann.com/meinbezirk)
- Screenshot or visual of the prototype
- Framing: "Dieses Repo ist kein fertiges Produkt. Es ist eine Blaupause."
- Table of contents linking to the 5 phases
- Attribution (Igor Schwarzmann / Known Unknowns)

### 01-verstehen/ — Verstehen

Purpose: Why civic transparency matters. The problem statement.

Content:
- Citizens are affected by decisions they don't know about
- Information exists but is scattered across bureaucratic systems
- The gap isn't access — it's relevance and readability
- Government publishes data for compliance, not for citizens
- References: GDS "Start with user needs" principle
- Sources: BVV/council information systems, civic participation research

### 02-daten-finden/ — Daten finden

Purpose: Core methodological contribution. How to find and process civic decision data.

Content splits into three parts:

**Teil 1: Fallstudie Berlin**
- What ALLRIS and PADOK are, how they work
- How to navigate Abgeordnetenhaus and Bezirksamt sources
- Specific steps taken, including where AI helped
- What worked, what didn't

**Teil 2: Recherche-Tools**
- Official sources (Ratsinformationssysteme, open data portals, council protocols) are the foundation
- AI-powered research tools (Perplexity, similar) help find context, news coverage, related decisions, and verify findings
- Framing: "Offizielle Quellen sind die Grundlage. Recherche-Tools helfen, Kontext zu finden, Zusammenhänge zu erkennen, und Lücken in den offiziellen Daten zu schließen."
- Both commercial (Perplexity, Claude, ChatGPT) and open-source (Ollama, LM Studio) options referenced

**Teil 3: Muster für andere Städte**
- Common systems: Ratsinformationssysteme (ALLRIS is one of many), open data portals
- Checklist: "Go to your city's website and look for..."
- Common data formats and where they hide
- How to use AI tools to process what you find
- Sources: actual portal links, system vendors, open data directories

### 03-relevanz-gestalten/ — Relevanz gestalten

Purpose: How to design the filtering/relevance layer. Explicitly a starting point, not a finished taxonomy.

Content:
- Core principle: people care about decisions through the lens of their life, not the government's org chart
- Berlin prototype uses three axes (Lebenslage, Ort, Anlässe) — one possible model
- Other dimensions worth exploring: age groups, mobility needs, language/accessibility, economic situation, housing type, and many more
- How to research what matters to your community: interviews, existing complaint data, council meeting attendance patterns, local news analysis
- The toolkit teaches the method of finding relevant dimensions, not a fixed set to copy
- Sources: service design literature, GDS life events work

### 04-umsetzen/ — Umsetzen

Purpose: Design principles and technical guidance. Not a tutorial.

Content:
- Design principles from GDS: do the hard work to make it simple, this is for everyone, be consistent not uniform
- Plain language: translating Amtsdeutsch into human language
- Technical considerations: start simple (static HTML is fine), progressive enhancement, accessibility
- Reference implementation walkthrough — link to index.html, explain design choices
- Scaling considerations: CMS, data pipelines, automated updates (for later, not day one)
- Sources: GDS Design System, WCAG, plain language guides

### 05-betreiben/ — Betreiben

Purpose: Who runs this, how, for how long. The sustainability question.

Content:
- Why municipal ownership or support matters (sustainability, trust, authority)
- Governance models: city-run, civic org-run, hybrid
- Maintenance: who updates cards, how often, quality control
- How to pitch to local government: citizen engagement, transparency obligations, reduced inquiry load
- Cost/effort reality of ongoing operation
- Sources: municipal digital service examples, civic tech sustainability research

### quellen/README.md — Quellen

Purpose: All sources in one place. Transparency and credibility.

Content organized by category:
- Government data systems (ALLRIS, PADOK, specific URLs)
- Design references (GDS principles, service design literature)
- Civic technology examples and prior art
- AI tools (commercial and open-source)
- Legal/regulatory context (transparency laws, open data regulations)

### CONTRIBUTING.md

Purpose: International invitation. Written in English.

Content:
- "This toolkit was built for Berlin. But the problem is universal."
- How to adapt for another German city
- How to adapt for another country (different government structures, different data systems)
- Contribution guidelines: translations, new case studies, pattern additions

## Design Principles (for the toolkit itself)

Drawn from GDS, applied to this project:

1. **Start with user needs** — The user is a citizen, not a civil servant
2. **Do the hard work to make it simple** — Translate bureaucratic complexity into clarity
3. **Make things open** — Open source, open methodology, open invitation
4. **This is for everyone** — Accessible language, accessible design, accessible tools
5. **Iterate** — This toolkit is v1. It will evolve with contributions

## What This Is Not

- Not a finished product to deploy
- Not a complete taxonomy of civic relevance filters
- Not locked to any specific AI vendor or tool
- Not limited to Berlin or Germany
