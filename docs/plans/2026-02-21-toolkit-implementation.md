# MeinBezirk Toolkit — Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Transform the MeinBezirk repo into an open-source civic transparency toolkit with 5 methodology phases, a sources directory, and international contribution guide.

**Architecture:** Markdown-only content project. Each phase is a directory with a single README.md. The existing index.html stays at root (live URL must keep working). All content in German except CONTRIBUTING.md (English).

**Writing style:** GDS-style — plain, practical, direct. Short sentences. Active voice. No fluff. Cite sources inline and collect them in quellen/.

**Design doc:** `docs/plans/2026-02-21-toolkit-blueprint-design.md`

**Key research findings for content:**
- PARDOK (not PADOK): pardok.parlament-berlin.de — Berlin parliamentary documentation, XML open data, daily updates
- Ratsinformationssysteme in Germany: SD.net (175 municipalities), Session (114), ALLRIS (21), more-rubin (27), Provox (22) — just in NRW alone
- OParl: standardized API spec for council data (oparl.org), v1.0 since 2016, many cities expose compliant APIs
- Politik bei uns: aggregator that pulls from OParl-compliant systems
- GDS life events approach: organizing services around citizen life moments, not government org charts

---

### Task 1: Create directory structure

**Files:**
- Create: `01-verstehen/README.md` (placeholder)
- Create: `02-daten-finden/README.md` (placeholder)
- Create: `03-relevanz-gestalten/README.md` (placeholder)
- Create: `04-umsetzen/README.md` (placeholder)
- Create: `05-betreiben/README.md` (placeholder)
- Create: `quellen/README.md` (placeholder)

**Step 1:** Create all directories and placeholder files

```bash
mkdir -p 01-verstehen 02-daten-finden 03-relevanz-gestalten 04-umsetzen 05-betreiben quellen
```

Write a one-line placeholder in each README.md:
```
# [Phase name]
```

**Step 2: Commit**

```bash
git add 01-verstehen 02-daten-finden 03-relevanz-gestalten 04-umsetzen 05-betreiben quellen
git commit -m "Add toolkit directory structure"
```

---

### Task 2: Write quellen/README.md

Write this first — other phases reference these sources. Organize by category.

**Files:**
- Create: `quellen/README.md`

**Step 1: Write content**

Sections:
- **Kommunale Informationssysteme** — ALLRIS, SD.net, Session, more-rubin, Provox. OParl standard (oparl.org). Politik bei uns as aggregator. PARDOK for Berlin state parliament (pardok.parlament-berlin.de, open data: parlament-berlin.de/dokumente/open-data).
- **Offene Daten** — Berlin Open Data (daten.berlin.de), GovData (govdata.de), European Data Portal
- **Gestaltungsprinzipien** — GDS Design Principles (gov.uk/guidance/government-design-principles), GDS Service Standard, GDS life events approach
- **Barrierefreiheit und Sprache** — WCAG 2.1 guidelines, Leichte Sprache / Einfache Sprache resources, plain language guidance
- **KI-Werkzeuge** — Commercial: Perplexity (perplexity.ai), Claude (claude.ai), ChatGPT (chat.openai.com). Open-source/lokal: Ollama (ollama.com), LM Studio (lmstudio.ai). Note: all methodology steps can be done with open-source tools.
- **Civic Technology** — Code for Germany (codefor.de), Code for America, Hack for LA civic-tech-structure, Open Knowledge Foundation (okfn.de)

Each entry: name, URL, one-sentence description of what it is and why it's relevant.

**Step 2: Commit**

```bash
git add quellen/README.md
git commit -m "Add sources and references"
```

---

### Task 3: Write root README.md

**Files:**
- Modify: `README.md`

**Step 1: Write content**

Structure:
1. **Title:** MeinBezirk
2. **One-paragraph description:** What this is — a toolkit for civic transparency at the municipal level
3. **Framing line:** "Dieses Repo ist kein fertiges Produkt. Es ist eine Blaupause."
4. **Link to live prototype:** [igorschwarzmann.com/meinbezirk](https://igorschwarzmann.com/meinbezirk/)
5. **Table of contents** linking to the 5 phases:
   - 01 — Verstehen
   - 02 — Daten finden
   - 03 — Relevanz gestalten
   - 04 — Umsetzen
   - 05 — Betreiben
   - Quellen
6. **Brief context:** Built in ~90 minutes with AI tools. Not because AI made it faster — because AI made it feasible for one person (Machbarkeitsunterschied, nicht Geschwindigkeitsunterschied).
7. **Attribution:** Igor Schwarzmann / Known Unknowns GmbH
8. **License note** and link to CONTRIBUTING.md

Keep it short. The README is a signpost, not the content.

**Step 2: Commit**

```bash
git add README.md
git commit -m "Rewrite README as toolkit entry point"
```

---

### Task 4: Write 01-verstehen/README.md

**Files:**
- Create: `01-verstehen/README.md`

**Step 1: Write content**

Sections:
1. **Das Problem** — Citizens are affected by municipal decisions they don't know about. Information exists but is scattered across bureaucratic systems designed for administration, not citizens. The gap isn't access — it's relevance and readability.

2. **Was kommunale Transparenz bedeutet** — Making government decisions findable, understandable, and relevant to the people they affect. Not open data dumps. Not transparency theater. Actual usability.

3. **Warum es bisher nicht funktioniert** — Council information systems (ALLRIS, SD.net, etc.) are built for internal workflow, not public communication. Documents are published as PDFs in bureaucratic language. No filtering by personal relevance. No plain-language summaries. Citizens would need to monitor multiple systems across governance levels (Bezirk, Land, Bund).

4. **Der Ansatz** — Start with user needs, not government structures (reference GDS principle #1). Organize information by life situation, location, and occasion — not by department or committee. Use AI to bridge the gap between bureaucratic source data and citizen-readable information.

5. **Quellen** — Link to relevant entries in quellen/README.md

**Step 2: Commit**

```bash
git add 01-verstehen/README.md
git commit -m "Add phase 1: Verstehen"
```

---

### Task 5: Write 02-daten-finden/README.md

**Files:**
- Create: `02-daten-finden/README.md`

**Step 1: Write content**

This is the longest and most methodological document. Three parts:

**Teil 1: Fallstudie Berlin**
- Berlin has two relevant governance levels: Land (Senat/Abgeordnetenhaus) and Bezirk (Bezirksamt/BVV)
- State level: PARDOK (pardok.parlament-berlin.de) — parliamentary documentation system. Covers bills, motions, written questions since 1989. Open data available in XML format, updated daily.
- District level: ALLRIS — Ratsinformationssystem used by Berlin Bezirke for BVV sessions, committee meetings, Drucksachen
- How the Berlin prototype was built: searched PARDOK and ALLRIS for Tempelhof-Schöneberg decisions, used AI to identify citizen-relevant items, translated from Amtsdeutsch to plain language, verified facts against original sources
- What worked: AI was effective at identifying relevance and translating language. Official sources provided authoritative grounding.
- What was harder: not all decisions are digitally accessible. Some require manual review of protocols.

**Teil 2: Recherche-Tools**
- Official sources are the foundation. They provide authority and verifiability.
- AI-powered research tools (Perplexity, etc.) complement official sources: finding news coverage, discovering context, identifying related decisions across governance levels, verifying information
- Framing: "Offizielle Quellen sind die Grundlage. Recherche-Tools helfen, Kontext zu finden, Zusammenhänge zu erkennen, und Lücken in den offiziellen Daten zu schließen."
- AI tools for processing: summarizing long documents, translating bureaucratic language, extracting structured data from PDFs
- Commercial options: Perplexity, Claude, ChatGPT
- Open-source/local options: Ollama, LM Studio — everything described here can be done without commercial tools
- Important: always verify AI-generated summaries against original sources

**Teil 3: Muster für andere Städte**
- Germany has no single standard system. The landscape:
  - SD.net (most common, 175+ municipalities in NRW alone)
  - Session (114 municipalities in NRW)
  - ALLRIS (21 municipalities in NRW, plus Berlin Bezirke)
  - more-rubin, Provox, BürgerPLUS, custom solutions
- OParl standard (oparl.org): standardized API for council data. Many cities expose OParl endpoints. Check api.oparl.org for a directory.
- Politik bei uns (politik-bei-uns.de): aggregates data from OParl-compliant systems — good starting point
- Checklist for finding data in your city:
  1. Search "[Stadt] Ratsinformationssystem" — most cities have one
  2. Check your city's open data portal (if it exists)
  3. Look for OParl API support (check api.oparl.org)
  4. Search for BVV/Stadtrat/Gemeinderat protocols on the city website
  5. Check if Politik bei uns covers your city
  6. Use Perplexity or similar to search for recent council decisions and news coverage
  7. Contact your local Code for Germany chapter (codefor.de) — they may already know the landscape
- Sources: link to quellen/README.md

**Step 2: Commit**

```bash
git add 02-daten-finden/README.md
git commit -m "Add phase 2: Daten finden"
```

---

### Task 6: Write 03-relevanz-gestalten/README.md

**Files:**
- Create: `03-relevanz-gestalten/README.md`

**Step 1: Write content**

Key framing: this phase is explicitly a starting point. The Berlin prototype demonstrates one approach. Other cities will have different needs.

Sections:

1. **Das Prinzip** — People care about government decisions through the lens of their own life, not through the government's organizational chart. A parent doesn't search by "Ausschuss für Jugend und Gesundheit." They search by "Was betrifft mein Kind?"

2. **Das Berliner Modell (ein Beispiel)** — The MeinBezirk prototype uses three filter axes:
   - Lebenslage (life situation): Eltern/Kita, Eltern/Schule, Mieter:in, Eigentümer:in, Gewerbetreibende, Senior:in
   - Ort (location): Schöneberg, Friedenau, Tempelhof, Mariendorf, Marienfelde, Lichtenrade
   - Anlässe (occasions): Kita-Anmeldung, Schuleingang, Heizsaison, Bauvorhaben, Wahlen
   - This is one model. It is not complete. It reflects one city, one set of assumptions.

3. **Weitere Dimensionen** — Other filter axes worth considering (none of these are prescriptive):
   - Alter/Altersgruppe (age groups)
   - Mobilität (mobility needs, accessibility)
   - Sprache (language — especially relevant in multilingual cities)
   - Wohnsituation (housing type: Altbau, Neubau, Sozialwohnung, WG)
   - Wirtschaftliche Situation (economic situation, relevant for benefit eligibility)
   - Barrierefreiheit (accessibility needs)
   - And many more — the right dimensions depend on your community

4. **Wie man die richtigen Dimensionen findet** — Methods, not answers:
   - Talk to residents. What questions do they bring to the Bürgeramt?
   - Analyze existing complaint and inquiry data (if accessible)
   - Look at local news: what government decisions generate public reaction?
   - Attend council meetings: what draws citizens to participate?
   - Review the GDS life events approach as inspiration (not as a template to copy)
   - Use AI to analyze large volumes of council decisions and identify patterns

5. **Quellen** — Link to quellen/README.md, especially GDS life events work

**Step 2: Commit**

```bash
git add 03-relevanz-gestalten/README.md
git commit -m "Add phase 3: Relevanz gestalten"
```

---

### Task 7: Write 04-umsetzen/README.md

**Files:**
- Create: `04-umsetzen/README.md`

**Step 1: Write content**

Sections:

1. **Gestaltungsprinzipien** — Adapted from GDS:
   - Mach die harte Arbeit, damit es einfach wird (do the hard work to make it simple)
   - Das ist für alle (this is for everyone — accessibility first)
   - Sei konsistent, nicht uniform (be consistent, not uniform — adapt to local context)
   - Fang mit Nutzer:innen-Bedürfnissen an (start with user needs, not system requirements)
   - Mach es offen (make things open: it makes things better)

2. **Sprache** — Translating Amtsdeutsch to human language:
   - Government documents use bureaucratic German by convention, not necessity
   - AI can help translate — but a human should verify the result preserves meaning
   - Examples: show before/after of a real council decision → plain language card
   - Consider Einfache Sprache / Leichte Sprache for broader accessibility

3. **Technische Umsetzung** — Start simple:
   - Static HTML is a valid first version. The Berlin prototype is a single file.
   - No framework, no build step, no database required to start
   - Progressive enhancement: add complexity only when you need it
   - Accessibility: semantic HTML, sufficient contrast, keyboard navigation, screen reader compatible (reference WCAG 2.1)
   - Mobile-first: citizens will use this on their phones

4. **Die Referenzimplementierung** — Link to index.html in this repo:
   - Single-file HTML with embedded CSS and vanilla JavaScript
   - Three-axis filtering with real-time updates
   - Mobile-responsive with collapsible filters
   - Two governance levels (Land vs. Bezirk) visually distinguished
   - No external dependencies
   - This is one way to build it. Not the only way.

5. **Weiterdenken** — For when you outgrow a static prototype:
   - CMS for non-technical editors to update cards
   - Data pipelines to pull from OParl or PARDOK automatically
   - Notification system (email, push) for subscribed topics
   - These are future considerations, not day-one requirements

6. **Quellen** — Link to quellen/README.md

**Step 2: Commit**

```bash
git add 04-umsetzen/README.md
git commit -m "Add phase 4: Umsetzen"
```

---

### Task 8: Write 05-betreiben/README.md

**Files:**
- Create: `05-betreiben/README.md`

**Step 1: Write content**

Sections:

1. **Warum Betrieb wichtig ist** — A civic transparency service that stops updating is worse than none. Citizens lose trust. Building it is the easy part. Running it is the commitment.

2. **Wer betreibt es?** — Three models:
   - **Kommunal betrieben:** The city/Bezirk runs it as a public service. Most sustainable, most authoritative. Requires political will and budget.
   - **Zivilgesellschaftlich betrieben:** A civic organization, Code for Germany chapter, or volunteer group runs it. More agile, but sustainability depends on continued engagement.
   - **Hybrid:** Civic initiative builds and iterates, municipality provides data access and eventually takes ownership. Often the most realistic path.

3. **Was Betrieb bedeutet** — Concrete tasks:
   - Monitoring council sessions and decisions (weekly/biweekly)
   - Writing or generating plain-language summaries
   - Tagging cards with relevant filters
   - Quality control: verifying accuracy against original sources
   - Updating the platform (new cards, removing outdated ones)
   - Responding to citizen feedback

4. **Wie man die Kommune überzeugt** — Arguments for municipal support:
   - Transparency obligations already exist (Informationsfreiheitsgesetz, Transparenzgesetze)
   - Reduces inquiry load at Bürgerämter when citizens can self-serve
   - Increases civic participation and trust
   - Demonstrates digital competence
   - Low cost relative to impact (especially if AI-assisted)
   - Aligns with federal digital strategy (OZG, Registermodernisierung)

5. **Aufwand und Kosten** — Realistic assessment:
   - Initial build: feasible in days with AI assistance (the Berlin prototype took ~90 minutes)
   - Ongoing: ~2-4 hours/week for monitoring and updating (estimate, depends on city size)
   - Technical hosting: minimal (static site, can run on city infrastructure)
   - The real cost is sustained attention, not money

6. **Quellen** — Link to quellen/README.md

**Step 2: Commit**

```bash
git add 05-betreiben/README.md
git commit -m "Add phase 5: Betreiben"
```

---

### Task 9: Write CONTRIBUTING.md

**Files:**
- Create: `CONTRIBUTING.md`

**Step 1: Write content**

In English. Structured as an invitation, not a rules document.

Sections:

1. **Opening:** "This toolkit was built for Berlin. But the problem is universal. Local governments everywhere make decisions that affect citizens — and citizens everywhere struggle to find out what those decisions are."

2. **How to contribute — another German city:**
   - Fork this repo
   - Follow the methodology in 02-daten-finden to find your city's data sources
   - Adapt the filters in 03-relevanz-gestalten to your community
   - Share your case study back as a PR
   - Especially valuable: documenting which Ratsinformationssystem your city uses

3. **How to contribute — another country:**
   - The methodology is transferable. The data landscape will be different.
   - Start with 01-verstehen — the problem statement is universal
   - Document how your country's local government publishes decisions
   - Consider translating the toolkit into your language
   - We'd love to see adaptations for other European countries, or beyond

4. **What makes a good contribution:**
   - Case studies from real cities (not hypothetical)
   - New data source patterns (systems we haven't documented)
   - New relevance dimensions (filter axes we haven't considered)
   - Translations
   - Corrections and improvements to existing content

5. **Technical:** Fork, branch, PR. No special tooling required. Content is Markdown.

**Step 2: Commit**

```bash
git add CONTRIBUTING.md
git commit -m "Add contribution guide (English)"
```

---

### Task 10: Final review and push

**Step 1:** Read through all files in order. Check for:
- Consistent tone (GDS-style, plain, direct)
- Working links between phases
- Sources referenced inline and collected in quellen/
- No claims of completeness in 03-relevanz-gestalten
- index.html unchanged (live URL still works)
- All German content except CONTRIBUTING.md

**Step 2:** Run `git log --oneline` to verify clean commit history

**Step 3:** Push to remote

```bash
git push origin main
```
