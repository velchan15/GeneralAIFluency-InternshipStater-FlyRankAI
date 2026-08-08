# FL-07 — Build Log
**Evelyn Anastasia · General AI Fluency, Week 5**

---

## Build Session 1 — August 08, 2026

**What I tried:**
Set up a new Claude Project ("FlyRank Assignment Tracker"). Filled in Project Instructions with the 7 points from the FL-06 spec (identify deliverable type, never write a final rationale on my behalf, validate real outputs, offer a logbook entry at the end, etc). Filled Project Knowledge with 3 examples of past logbook paragraphs as a style/format reference (pasted as text rather than uploaded as files, since I'm on the free Claude plan). Then ran the first test with a video-only assignment card (BE: "Build the Systems That Build Software").

**What broke / didn't work as expected:**
Nothing broke — the first run worked as instructed right away. The agent correctly identified this as a video-only deliverable, gave the correct submission link format, and asked me to confirm I'd actually watched the video before offering a logbook entry (didn't assume or invent that status).

**What I changed:**
No changes made to the instructions after this run.

**Anything cut from the FL-06 spec, and why:**
Project Knowledge was filled in by pasting text directly instead of uploading files as originally planned in the spec, because the free Claude plan doesn't support file uploads to Project Knowledge. The result still worked the same way as planned.

---

## Build Session 2 — August 08, 2026

**What I tried:**
Ran a second test with a different assignment type: a written-rationale card ("Three Roads: Choose Your Stack with AI"). The goal was to test the most critical guardrail in the spec — whether the agent would actually refuse to write the final rationale paragraph on my behalf.

**What broke / didn't work as expected:**
Nothing broke. The agent explicitly stated that the final rationale paragraph had to be written by me, in my own words, and asked for four constraints (skill level, sitemap/content map, dynamic requirements, display preferences) before producing stack options — matching the process order in the assignment brief.

**What I changed:**
No changes made to the instructions after this run.

**Anything cut from the FL-06 spec, and why:**
No additional deviations in this run.

---

## First successful end-to-end run

**Date/time:** [fill in recording date & time]
**What I fed the agent (assignment card used):** Three Roads: Choose Your Stack with AI (General AI Fluency, Week 4)
**What it produced:** A request for 4 constraints up front, followed by three stack options (simplest → most powerful) each with build approach, free hosting, backend requirement, and trade-offs, closing with an explicit request that I write the final decision paragraph myself.
**Anything still rough about the output:** [fill in if anything — e.g. instructions felt long on first read, or a section needed re-explaining]

---

## Summary of deviations from FL-06 spec

| Spec item | What I actually built | Why it changed |
|---|---|---|
| Project Knowledge via file upload | Filled in by pasting text directly | Free Claude plan doesn't support file uploads to Project Knowledge; functional result is the same |
| GitHub connector (optional in spec) | [fill in: used / not used] | [fill in reason] |
