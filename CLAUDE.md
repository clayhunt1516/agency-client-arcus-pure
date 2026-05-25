# Arcus Pure — Operational Intelligence System

> **For Claude (and other AI tools):** This file is your entry point to Arcus Pure's operational intelligence system. Read it before doing anything else in this folder. It is intentionally short — depth lives in the subdirectories and in Notion.

---

## What this system is

This system is Arcus Pure's organized, AI-readable Company Brain. It has **two layers**:

- **The framework layer** — this Git repository. It holds agent orientation (`CLAUDE.md` files), conventions, SOPs, report specifications, and templates. It changes deliberately and is version-controlled.
- **The client-knowledge layer** — a Notion workspace. It holds the actual content about the company: who they are, key relationships, operational and project state, discovery questions, and current context. It is mutable and human-maintained.

This file is the index and operating manual. When you need *client knowledge*, go to Notion (see the "Notion" section). When you need *conventions or procedures*, stay in Git.

## About Arcus Pure

Arcus Pure is a whole-space disinfection company based in Cedar City, Utah. Full company context — history, ownership, key people, and relationships — lives in Notion → Company Overview.

- **Industry:** whole-space disinfection
- **Primary location(s):** Cedar City, Utah
- **Size:** 4–6

For deeper company context — history, ownership, key people — see Notion → Company Overview.

## Notion — client knowledge layer

The Arcus Pure client knowledge content lives in Notion. Use the Notion
MCP server to access it. Stable IDs below.

For company knowledge — profile, key relationships, entity map, glossary,
locations:
  Notion: "Arcus Pure" → Company Overview
  Page ID: 36b2582b-bb25-8129-8cb7-f23db6f57776

For discovery questions — open items, resolved questions, Q-numbering:
  Notion: "Arcus Pure" → Discovery Questions database
  Database ID: ae098c66-f062-44c9-9521-c39353059eec

For current operational state — open items, recent log:
  Notion: "Arcus Pure" → Active Context page
  Page ID: 36b2582b-bb25-81b2-a1e8-ce22051013ae

For marketing content — brand voice, SEO, paid advertising, social,
conversion tracking, CRM, account access:
  Notion: "Arcus Pure" → Marketing
  Page ID: 36b2582b-bb25-8172-8e82-cd926d7ef02e

For framework conventions, SOPs, report specs, agent orientation:
  Stays in Git. See ./01-accounting/, ./98-testing/, and the optional
  module folders.

## Folder map

| Folder | What lives here |
|---|---|
| `/00-company-overview/` | Orientation for company-level knowledge. The content itself lives in Notion (see above). |
| `/01-accounting/` | Financial operations: AR/AP, GL, reporting, month-end, financial controls. SOPs and report specs are Git-resident here. |
| `/03-marketing/` | Marketing orientation. Live content — brand voice, SEO, paid advertising, social, conversion tracking, CRM, account access — lives in Notion (see above). |
| `/06-executive/` | Executive-level reporting. The folder is a slot; no industry module is deployed for this client, so report specs are not populated. |
| `/98-testing/` | Deployment validation and testing structure. |
| `/99-archive/` | Superseded content kept for reference. Read only if explicitly relevant. |
| `/.claude/skills/` | Auto-loaded skills available to Claude Code. |

Each folder has its own `CLAUDE.md`. Read it before working inside that folder. Do not pattern-match from the folder name alone.

## Operating principles

These are non-negotiable rules for how Claude should work in this system.

1. **Read the relevant `CLAUDE.md` first.** Before working in a folder, read its `CLAUDE.md`. Before invoking a skill, read its `SKILL.md`.

2. **Client knowledge comes from Notion — fetch it live.** Do not answer client-knowledge questions from memory, from auto memory, or from archived copies. Fetch the current state from Notion.

3. **Do not fabricate.** If a fact, number, name, date, or procedure isn't in the files or in Notion (or appears stale), say so. Ask the user or flag the gap. Never invent.

4. **Cite your source.** When referencing an SOP or report spec, give the relative Git path. When referencing client knowledge, name the Notion page or database. Citations make claims traceable.

5. **Treat `/data/` as read-only.** The `data/` subfolders hold reference snapshots and exports from authoritative systems. Read them; do not modify them.

6. **Surface staleness.** If a file or Notion page references dates, prices, people, or processes that look outdated, flag it before working from it.

7. **Push back when something looks wrong.** If a request conflicts with a documented SOP, an operating principle, or basic sense, say so before executing. Default to interrogating, not agreeing.

8. **One question at a time.** When clarification is needed, ask one focused question rather than a list.

## Generality tags
Generality tags mark how broadly a claim applies, so future deployments can tell which framework-layer content lifts directly to a template and which is engagement-specific. They appear inline, immediately after the claim they qualify.
- `[universal]` — applies to any client regardless of industry
- `[industry]` — applies to clients in this industry (e.g., real-estate development)
- `[client]` — specific to this deployment's client

The two tag axes are independent: a claim can carry a generality tag, an epistemic tag, both, or neither (e.g. `[client] [verify]`, `[industry] [discovery]`, or plain `[universal]`).

## Epistemic tags

Epistemic tags mark the confidence status of a claim in framework-layer and client-knowledge content. They appear inline, immediately after the claim they qualify.

- `[discovery]` — unknown; information not yet gathered
- `[verify]` — potentially wrong; claim contradicted by primary-source evidence

**Resolving `[discovery]`:** When an open item is answered, update the corresponding discovery-question record in Notion (status → 🟢, with date and answer summary) and update the content page or file to remove the `[discovery]` marker.

**Resolving `[verify]`:** Replace the contested claim with the correct content. Do not supplement the original — audit trail is preserved through version history, not by accumulating contradictions in the content itself.

## Claude Code auto memory

Claude Code maintains an auto-memory folder for this project — notes it writes itself and loads automatically at the start of every session.

- Auto memory is for **durable engagement learnings only**: how this client works, recurring conventions, workflow preferences, gotchas discovered over time.
- Auto memory is **not** for client state. Client state — open items, project status, current priorities, discovery-question answers — is volatile and lives in Notion. Fetch it live; never read it from auto memory.
- **Never write client-state snapshots to auto memory.** A snapshot goes stale the moment Notion changes, and a future cold session will load the stale copy and trust it. If you find a client-state snapshot in auto memory, treat it as stale, do not rely on it, and remove it.

## Communication style

- Plain, direct language. No filler, no AI-flavored throat-clearing.
- Concrete over abstract: examples, names, numbers, paths.
- Lead with the answer; put context after.
- Match Arcus Pure's register — technical.

## Data freshness

- The Git files here are conventions, SOPs, report specs, and orientation — not live data and not client state.
- Client-knowledge state lives in Notion and is current as of its last human update. Treat it as authoritative for client knowledge, but not as a real-time feed.
- For current numbers — financials, operational metrics — the authoritative source is the underlying system: QuickBooks Online. Exports in `/data/` folders are only as fresh as their export date.
- If a question needs real-time data, say so and point to the live system.

## Where to find things not in this file

| If you need… | Look in… |
|---|---|
| Company background, history, ownership, key people | Notion → Company Overview |
| Glossary of company-specific terms | Notion → Company Overview → Glossary |
| Current priorities, open issues | Notion → Active Context |
| Discovery questions and their status | Notion → Discovery Questions |
| Marketing content and strategy | Notion → Marketing |
| Conventions and SOPs for a department/operational area | That folder's `CLAUDE.md` and SOPs (Git) |
| How to perform a specific task | The relevant skill in `/.claude/skills/`, or an SOP in the relevant folder |

## System metadata

- **Framework version:** v0.3.0
- **Universal core version:** v0.3.0
- **Industry module:** none
- **Deployed:** 2026-05-25
- **Last reviewed:** 2026-05-25
- **Maintainer:** Clay Hunter

Full deployment details live in `DEPLOYMENT.md`.
