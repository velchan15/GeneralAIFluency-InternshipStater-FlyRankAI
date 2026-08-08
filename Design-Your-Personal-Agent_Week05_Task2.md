# FL-06 — Design Your Personal Agent
**Evelyn Anastasia · General AI Fluency, Week 5**

---

## 1. Job to Be Done

**FlyRank Assignment Tracker & Logbook Writer.**

Each week I get multiple assignment cards across two FlyRank tracks (General AI Fluency, Machine Learning), each with different deliverable types: watch-only videos, written rationales, coding notebooks, live-build tasks. The agent's one job: take an assignment card (pasted as text) plus a short description of the work I actually did, and produce two things —

1. A correctly-formatted **deliverable draft** matching what that specific assignment type requires (a submission note, a rationale, a logbook-ready summary — never more than the card asks for).
2. A **formal Bahasa Indonesia logbook paragraph** summarizing that day's work, suitable for my internship activity report.

It does not track deadlines, does not submit anything on my behalf, and does not touch more than one assignment's scope at a time unless I explicitly say "these were done the same day."

## 2. User and Usage Frequency

**User:** me, sole user, no shared/team access needed.
**Frequency:** weekly — once per assignment card as I close it out, batched around whenever I sit down to submit and update my logbook (typically 1–3 times a week, several assignments per session).

## 3. Tools and Data Needed, With Access Plan

| Need | Access plan |
|---|---|
| Assignment card text | Manually pasted by me each time. No FlyRank API/scraping — the platform has no public API and I won't share login credentials with an agent, so this stays manual by design. |
| Reference for my logbook voice/format | A small set of my own past logbook paragraphs, stored as reference material in the agent's project knowledge, so tone and formality stay consistent. |
| Reference for portfolio facts (when relevant) | My GitHub repo URLs, fetched read-only on request — never write access. |
| Language preference | Explicit flag each time ("pake bahasa indonesia" / "pake bahasa inggris") — the agent must not assume. |

No tool in this spec writes, deletes, or submits anything externally. Everything the agent produces is a draft I paste in myself.

## 4. Draft Instructions

> You are my FlyRank assignment assistant. When I paste an assignment card:
> 1. Identify the deliverable type: watch-only video, written rationale/deliverable, or a coding/build task.
> 2. If it's watch-only: confirm no other deliverable is needed, give me the submission link format only.
> 3. If it's a written deliverable: help me build it from constraints and process, but never write the final personal rationale/decision paragraph in first person for me to submit unedited — that must be in my own words. Say so explicitly.
> 4. If it's a coding/build task: ask for my actual repo/notebook state before writing anything, validate outputs are real (not fabricated numbers), flag anything that looks suspicious (leakage, too-perfect scores).
> 5. After the deliverable is settled, offer a logbook paragraph in formal Bahasa Indonesia, using only facts I've actually confirmed were done — never invent metrics, dates, or outcomes.
> 6. If the card is ambiguous about deliverable format, ask before drafting anything.
> 7. Default explanation language: Bahasa Indonesia casual. Deliverable language: match what I specify; ask if unclear.

## 5. Eval Cases (defined before building)

1. **Watch-only video card** → agent should recognize there's no written deliverable, and output only a submission-link format, no invented rationale.
2. **Written-rationale card (e.g. "Three Roads")** → agent drafts constraints/options/trade-offs, but explicitly flags that the final decision paragraph must be written in my own words, not silently submitted as mine.
3. **Coding/build card (e.g. capstone model)** → given only my repo links, agent pulls real data/outputs and reports actual numbers — flags if a result looks "too good to be true" (e.g. suspiciously perfect score) instead of accepting it at face value.
4. **Ambiguous card** (missing deliverable format or workload detail) → agent asks a clarifying question instead of guessing and producing the wrong shape of output.
5. **Two assignments closed same day** → agent produces two separate, distinct logbook paragraphs (not merged into one), matching my stated formatting preference.
6. **Explicit language switch mid-task** ("pake bahasa inggris") → agent's next deliverable output switches language correctly without dropping content or restarting from scratch.

## 6. Risks and Guardrails

**Must confirm before proceeding:**
- Deliverable format/type, if the assignment card is ambiguous.
- Output language, if not explicitly stated.
- That any technical result (metric, score, output) reported in a logbook entry is one I've actually validated myself, not just AI-generated.

**Must never do:**
- Submit anything directly to FlyRank's platform — no auto-submission, no credential handling.
- Write a first-person "rationale in my own words" deliverable and present it as submit-ready without flagging that I need to personalize it.
- Invent facts, metrics, or outcomes in a logbook entry that weren't confirmed in our conversation — logbook entries are meant to be an honest record for an internship report.
- Merge multiple days'/assignments' work into a single ambiguous paragraph without being asked to.

## 7. Platform Choice and Justification

**Chosen: Claude Project**, with the assignment card text, my past logbook examples, and my portfolio/repo links available as project knowledge, using Claude's existing web-fetch capability to pull real repo/notebook content on request.

**Alternative considered — n8n agent workflow with FlyRank scraping:** would allow fully automated assignment pulling and even auto-drafting without me pasting cards manually. Rejected because FlyRank has no public API, and building a scraper would require handling my login credentials in a third-party automation tool — a security risk I'm not willing to take for a workload this small (a few assignments a week). The manual-paste version costs me 10 extra seconds per assignment and avoids that risk entirely.

**Alternative considered — Custom GPT:** paid, and doesn't offer anything Claude Project doesn't already do for my use case (no code execution or repo-fetch advantage that matters here); rejected mainly on cost with no real capability gain for this scope.

Claude Project is free, matches my current skill level, requires no new infrastructure, and is exactly the setup I've already been using successfully to close out assignments this term — this spec mostly formalizes a workflow that's already working, rather than inventing a new one.
