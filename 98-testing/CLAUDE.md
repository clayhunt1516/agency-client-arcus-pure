# 98 — Testing

> **For Claude:** Read this file before working in this folder.

## What this folder is

This folder holds the deployment's **validation and testing structure** — the materials used to confirm the Company Brain works: that an agent can orient correctly, route between the Git and Notion layers, and answer client questions accurately.

## What lives here

Created and added to as testing happens:

- A test suite — the set of questions or scenarios used to exercise the brain.
- `captures/` — recorded test runs, kept for longitudinal comparison (does retrieval get crisper or hedgier over time?).

## The fresh-session validation

The first deployment of any new vertical — and any deployment with significant hand-built structure — runs the **fresh-session validation procedure**: a cold Claude Code session confirming end-to-end orientation. The procedure itself is a framework artifact (`deployment-process/setup/fresh-session-validation.md`); the *results* of running it for this client are recorded here.

## Conventions

- Test-run captures are append-only — a new run is a new capture, not an edit of an old one.
- Captures use the loose-date format.

---

## How to populate this file

This file is largely complete as shipped. Populate the test suite and `captures/` as testing happens. Remove this footer once the deployment's testing approach is established.
