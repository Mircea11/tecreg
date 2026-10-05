# TECHREG — PROJECT BLUEPRINT
Version: 0.1
Date: 2026-10-05

## 1. Purpose

TechReg is a regulatory-intelligence and AI-governance project that turns legislation, governance frameworks and standards into structured, traceable, practical information.

Primary principle:

> Source → structured data → interpretation → comparison → assessment → decision support.

The project must preserve the distinction between:
- binding law;
- national implementation;
- governance frameworks;
- standards;
- guidance;
- international comparator regimes.

EU law is the primary baseline. Japan and South Korea are international comparator jurisdictions and should normally be represented as differences from the EU baseline rather than as duplicated full analyses.

---

## 2. Current project architecture

```text
techreg/
├── index.html
├── style.css
├── assets/
│
├── data/
│   ├── source_register.csv
│   │
│   ├── sources/
│   │   ├── eu/
│   │   │   ├── original/
│   │   │   ├── consolidated/
│   │   │   └── standardisation/
│   │   ├── be/
│   │   │   ├── original/
│   │   │   └── current/
│   │   ├── governance/
│   │   │   ├── oecd/
│   │   │   ├── nist/
│   │   │   └── eu_hleg/
│   │   ├── standards/
│   │   │   └── iso/
│   │   │       ├── metadata/
│   │   │       └── licensed/
│   │   └── international/
│   │       ├── japan/
│   │       └── south_korea/
│   │
│   ├── json/
│   │   ├── raw/
│   │   ├── semantic/
│   │   ├── frameworks/
│   │   └── crosswalks/
│   │
│   └── schema/
│
├── regulations/
├── learn/
├── tools/
├── insights/
└── about/
```

---

## 3. Source families

### A. Binding legislation — primary baseline
- EU AI Act
- GDPR
- NIS2
- Belgian NIS2 Law
- Belgian NIS2 Royal Decree
- Cyber Resilience Act
- Data Act
- Machinery Regulation

### B. Governance / historical lineage
- OECD AI Principles / Recommendation on AI
- OECD 2019 scoping paper
- EU HLEG Ethics Guidelines for Trustworthy AI
- EU HLEG ALTAI
- NIST AI RMF 1.0
- NIST AI RMF Playbook
- NIST Generative AI Profile

### C. Standards
Core:
- ISO/IEC 42001:2023 — AI management systems
- ISO/IEC 27001:2022 — information security management
- ISO/IEC 27701:2025 — privacy information management
- ISO/IEC 23894:2023 — AI risk management
- ISO/IEC 22989:2022 — AI concepts and terminology
- ISO/IEC 5338:2023 — AI system lifecycle
- ISO/IEC 5259 series — data quality for analytics and machine learning

Important maturity logic:
- ISO 27001 maturity is a proxy for information-security management maturity.
- ISO 27701 maturity is a proxy for privacy-management maturity.
- Together they indicate organisational readiness for many management-system disciplines required by ISO 42001.
- Awareness, implementation and certification must be recorded separately.

### D. International comparators
- Japan
- South Korea

Comparison rule:
- EU = baseline
- store only material deviations from EU where possible
- retain exact local source and practical effect

---

## 4. Data layers

### Layer 1 — Source library
Exact official or lawfully obtained documents.

Contains:
- PDFs
- XML/HTML
- official metadata pages
- checksums
- version information

### Layer 2 — Raw JSON
Represents what the source says and how it is structured.

Typical fields:
- document identity
- source provenance
- version
- legal nodes
- parent/child structure
- exact text
- source locator
- references

No business interpretation here.

### Layer 3 — Semantic JSON
TechReg interpretation of source nodes.

Common concepts:
- scope
- actors
- applicability criteria
- classification
- obligations
- evidence requirements
- reporting requirements
- governance requirements
- dates
- penalties
- authorities
- cross-regulation relations

### Layer 4 — Crosswalks
Connects:
- law ↔ governance frameworks
- law ↔ standards
- standard ↔ standard
- EU ↔ Japan
- EU ↔ South Korea
- requirements ↔ controls ↔ evidence

### Layer 5 — Applications
Outputs for users:
- regulation pages
- comparisons
- assessments
- readiness scores
- evidence checklists
- dashboards
- RAG / question answering
- consulting deliverables

---

## 5. Project status

Legend:
- [DONE]
- [IN PROGRESS]
- [NEXT]
- [LATER]

### Phase 0 — Infrastructure
- [DONE] Git repository
- [DONE] GitHub Pages
- [DONE] initial TechReg website / control-room concept
- [IN PROGRESS] EU.org domain
- [DONE] local source-library structure

### Phase 1 — Source control
- [DONE] initial EU / Belgian legal-source library
- [DONE] governance / standards downloader
- [DONE] governance reference register
- [IN PROGRESS] merge all source metadata into `data/source_register.csv`
- [NEXT] verify downloaded files and expected ISO metadata pages
- [NEXT] verify SHA-256 manifests
- [NEXT] add Japan / South Korea official source documents
- [LATER] add further international comparators only if useful

### Phase 2 — Common data model
- [DONE] decision to use JSON as main data path
- [DONE] `data/json/raw/`
- [DONE] `data/json/semantic/`
- [DONE] `data/schema/`
- [IN PROGRESS] common raw JSON model
- [NEXT] common semantic JSON model
- [NEXT] crosswalk model
- [LATER] formal JSON Schema after models are stable

### Phase 3 — Extraction
- [LATER] extract complete AI Act
- [LATER] extract complete NIS2
- [LATER] validate generic structure
- [LATER] extract remaining core legislation
- [LATER] extract governance frameworks where licensing permits
- [LATER] extract licensed standards only within licence conditions

### Phase 4 — Semantic mapping
- [LATER] actors
- [LATER] applicability
- [LATER] obligations
- [LATER] evidence
- [LATER] deadlines
- [LATER] authorities
- [LATER] penalties
- [LATER] cross-regulation mapping

### Phase 5 — Governance / standards crosswalk
- [LATER] OECD ↔ AI Act
- [LATER] NIST AI RMF ↔ AI Act
- [LATER] ISO 42001 ↔ AI Act
- [LATER] ISO 27001 ↔ NIS2 / CRA / AI Act cybersecurity
- [LATER] ISO 27701 ↔ GDPR / AI data governance
- [LATER] ISO 23894 ↔ AI risk-management requirements

### Phase 6 — International comparison
- [LATER] EU baseline ↔ Japan differences
- [LATER] EU baseline ↔ South Korea differences
- [LATER] Japan ↔ South Korea derived comparison

### Phase 7 — TechReg assessment prototype
- [LATER] AI governance maturity assessment
- [LATER] ISO 27001 awareness / implementation / certification
- [LATER] ISO 27701 awareness / implementation / certification
- [LATER] ISO 42001 readiness
- [LATER] AI Act organisational readiness
- [LATER] evidence-gap analysis

### Phase 8 — Public product
- [LATER] regulation catalogue
- [LATER] searchable concepts
- [LATER] differences / crosswalk pages
- [LATER] assessment interface
- [LATER] RAG assistant
- [LATER] update/status dashboard

---

## 6. Immediate next milestone

### Milestone: SOURCE LIBRARY CONTROLLED

Definition of done:
1. `data/source_register.csv` is the single master register.
2. Every downloaded source has a unique source ID.
3. Every local source has:
   - official URL
   - local path
   - issuer
   - source class
   - binding status
   - version/date
   - access status
   - last checked date
4. Every freely downloaded file has SHA-256 recorded.
5. Licensed ISO full texts are separated from public material.
6. Missing documents are clearly marked.
7. Japan and South Korea source placeholders exist.

Only after this milestone should large-scale extraction begin.

---

## 7. Update and modification control

This becomes a permanent TechReg subsystem.

### Fields to maintain in `source_register.csv`

Recommended update-control fields:

- `source_id`
- `short_title`
- `source_class`
- `issuer`
- `official_url`
- `local_path`
- `version`
- `publication_date`
- `effective_date`
- `last_checked`
- `last_changed`
- `sha256`
- `etag`
- `last_modified_http`
- `update_frequency`
- `change_status`
- `change_type`
- `supersedes`
- `superseded_by`
- `review_required`
- `reprocess_required`
- `notes`

### Change states

```text
UNCHANGED
NEW_VERSION
AMENDED
CONSOLIDATED_VERSION_CHANGED
REPLACED
REPEALED
URL_CHANGED
DOWNLOAD_FAILED
MANUAL_REVIEW
```

### Future update workflow

```text
official source
      ↓
check URL / metadata / version
      ↓
download temporary copy
      ↓
compare version + SHA-256
      ↓
UNCHANGED ───────────────→ update last_checked
      │
      └─ CHANGED
             ↓
       archive previous version
             ↓
       save new version
             ↓
       update source_register
             ↓
       flag semantic data for review
             ↓
       regenerate affected crosswalks/pages
```

### Special rule for ISO

For ISO documents:
- automate monitoring of official metadata/version pages;
- do not automatically redistribute licensed full text;
- if a new edition/amendment appears, flag it for manual acquisition and review.

---

## 8. Project-control rule

At any point, answer four questions:

1. **Where are we?**
   Current phase and current milestone.

2. **What is complete?**
   Only evidence-backed completed items.

3. **What is the next smallest useful action?**
   One concrete step.

4. **What stays parked?**
   Anything that does not improve the current milestone.

This prevents project dispersion.

---

## 9. Current answer to those four questions

### Where are we?
Phase 1 — Source control.

### What is complete?
- local source folders
- first EU and Belgian legal documents
- governance / standards downloader
- JSON directory structure
- initial source metadata

### What is the next smallest useful action?
Verify the local source library and the three core ISO metadata references:
- ISO/IEC 42001
- ISO/IEC 27001
- ISO/IEC 27701

Then verify / install the merged `source_register.csv`.

### What stays parked?
- full regulatory extraction
- RAG
- assessment scoring
- dashboards
- multilingual interface
- advanced website redesign
- automated regulatory monitoring

until source control is stable.

---

## 10. Definition of TechReg v0.3

TechReg v0.3 should contain:

- controlled source library
- one master source register
- stable raw JSON model
- stable semantic JSON model
- at least one complete regulation extracted
- first governance/standards crosswalk
- first EU-vs-international difference model
- public regulations catalogue page

That is the next meaningful product milestone.
