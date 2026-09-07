# AILIN — AI Legal Intelligence Network

Legal-tech platform for insolvency administrators, live at
[ailinnetwork.com](https://ailinnetwork.com). We built it as a freelance
developer and it runs in production today.

> This repository is a text-only showcase — the source stays private.
> Demo walkthrough available on request.

## What the platform does

- Case management for insolvency administrators: OWNER/ADMIN roles,
  dashboards, document workflows
- Document intelligence: a spaCy NER pipeline extracts organizations and
  people (ORG/PER) from legal texts; a hybrid regex + AI layer detects
  template fields in documents
- Document generation: templates rendered to HTML, then to PDF with
  WeasyPrint
- Penalty interest calculator for Civil Code Art. 619 (Republic of
  Moldova): multi-invoice batches, export to PDF and XLSX
- Integration with the BNS statistics API, cached in two local tiers so
  external calls stay predictable

## Architecture

Next.js 14 (TypeScript) SPA → Caddy → FastAPI → PostgreSQL
(async SQLAlchemy, Alembic migrations)
                      ↘ spaCy NER · WeasyPrint PDF pipeline · BNS client

- Deployment: production Docker Compose with Caddy, provisioned by cloud-init
- Auth: JWT with OWNER/ADMIN roles
- Testing: pytest, including the NER service

## Stack

FastAPI · PostgreSQL · async SQLAlchemy · Alembic · spaCy · WeasyPrint ·
Next.js 14 · TypeScript · Docker Compose · Caddy · pytest
