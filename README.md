## About

**99names — a disciplined, document-driven research infrastructure**, not a typical code project.  
Documentation and process matter as much as code.

![Projectcover](https://github.com/N04D/99names/blob/main/assets/PWMdNeRgOZ45f3ywvZcs--0--ktc3z.jpg)


## What is this project?

**99names** is a structured infrastructure for processing, analyzing and documenting Islamic source data  
with a focus on discipline, reproducibility and clear traceability.

This repository is *not* a quick experiment or an app — it is a system for long-term research, batch processing, and disciplined workflows.

---

## Core Principles

This project is guided by:

- **One source of truth** for decisions (`DECISIONS.md`)
- **Clear roles** with defined responsibilities (`/roles/`)
- **Structured workflows** (`WORKFLOW.md`)
- **Explicit reporting** and review processes

Everything is meant to be:
- understandable without prior context
- reproducible and documentable
- explicit in assumptions and decisions

---

## Infrastructure Overview

The infrastructure supports batch jobs such as translation and data analysis, designed for stability over speed and clarity over cleverness.

### Device Responsibilities

- **rpi5-ml** — execution of machine-learning, translation and processing tasks  
- **rpi5-n8n** — orchestration and workflow control  
- **Odroid UX4** — storage of datasets, output and logs  
- **rpi3** — version control and general infra support

Stateful data lives on the UX4, not in scripts. Orchestration is separated from execution logic. :contentReference[oaicite:1]{index=1}

---

## Data Structure (Odroid UX4)


/data
├── raw/ # raw input files
├── processing/ # in-progress work
├── translated/ # completed output
├── reports/ # analysis and summaries
├── logs/ # run logs


This layout is definitive for batch tasks.

---

## Workflow Summary

Work flows through the system in a set sequence:



Reports and reviews are written, not whispered. Decisions are stored in `DECISIONS.md`. :contentReference[oaicite:2]{index=2}

---

## What this project is *not*

- Not a real-time system  
- Not an interactive application  
- Not a development sandbox  
- Not a place for untracked experiments

If it can’t be explained simply, it doesn’t belong here.

---

## Getting Started

You should begin with:

1. `PROJECT_OVERVIEW.md` — context and boundaries  
2. `ONBOARDING.md` — how to join in properly  
3. Your role description in `/roles/`  
4. `WORKFLOW.md` — understanding work flow before code

---

## Reporting and Reviews

- Output is stored in `/reports/`  
- Reviews live under `/reviews/`  
- Structured templates guide every report and review

This ensures discipline and traceability across all work.

---

## Contributing

Contributions are guided by:
- roles and workflows
- documented decisions
- structured reviews

Discuss additions before implementing them.

---

