# The Prompt Ladder

**Evelyn Anastasia · Machine Learning Track**
**Context:** All prompts were run against the real "Refresh / Content Opportunity Scoring" lane dataset (`content_refresh_anonymized.csv`, 30,000 rows, 44 columns).

---

## Baseline (weak prompt)

**Prompt:**
> "Explain this data"

**Output:**
> This data contains information about website content, such as visits, clicks, and performance. There are columns like `impressions_90d`, `ctr`, `trend_direction`, and others that show how these pages are performing in search. This data can be used to analyze content performance over time.

---

## Version 1 — added: Clear Goal

**Prompt:**
> "Explain this data. My goal: I want to know which pages need to be reviewed first."

**Output:**
> To figure out which pages need review, focus on the `trend_direction` and `ctr` columns. Pages with `trend_direction = "down"` indicate declining performance, and a low `ctr` means the page isn't attracting clicks from search results. Together, these two can be a useful indicator of which pages to prioritize.

**Notes:**
- **What changed in the prompt:** added one sentence stating an explicit goal.
- **What actually improved in the output:** the response stopped just describing columns and started pointing to two specific columns relevant to the goal.
- **What still failed:** still no real numbers (how many pages are declining, what the average CTR is) — still felt templated.
- **What I'd try next:** give it real data context instead of just column names.

---

## Version 2 — added: Real Context

**Prompt:**
> "Explain this data. My goal: I want to know which pages need to be reviewed first. The data: 30,000 rows, 44 columns, from the 'Refresh/Content Opportunity Scoring' lane. Key columns: `trend_direction` (down/stable/up/new/flat), `ctr`, `avg_position`."

**Output:**
> Out of 30,000 pages, 54.2% (16,262 pages) are marked "down" — more than half the dataset. Declining pages average a CTR of 0.32, compared to 0.73 for non-declining pages — more than double the difference. Interestingly, search position (`avg_position`) is barely different between declining pages (15.9) and stable ones (16.8) — so position alone isn't a strong signal; CTR is far more informative for identifying problem pages.

**Notes:**
- **What changed in the prompt:** added real dataset stats and the lane name.
- **What actually improved in the output:** this was the biggest jump — the response now has concrete numbers and even surfaced an insight I didn't ask for (search position turns out to be a weak signal) — went from generic to analytical.
- **What still failed:** language was still fairly technical for a non-technical reader ("CTR," "avg_position" used without explanation).
- **What I'd try next:** define who's actually going to read this.

---

## Version 3 — added: Defined Audience

**Prompt:**
> (same as V2) + "This will be read by a non-technical content editor who wants to prioritize which pages to review this week. Don't use technical terms without explaining them."

**Output:**
> More than half your pages (54%) are losing traffic. The simplest way to decide which to review first: look for pages that are "trending down" AND rarely get clicked (a low click-per-view ratio) — that means people see the page in Google but aren't interested enough to click. Interestingly, Google ranking position barely matters here — even well-ranked pages can still lose clicks if the title or description isn't compelling.

**Notes:**
- **What changed in the prompt:** added a specific audience plus an instruction to avoid jargon.
- **What actually improved in the output:** "CTR" became "click-per-view ratio," and the explanation shifted toward actionable insight ("the title or description isn't compelling") instead of just reporting statistics.
- **What still failed:** still a long paragraph — for an editor scanning many pages quickly, this isn't easy to skim.
- **What I'd try next:** ask for a more structured output format.

---

## Version 4 — added: Specified Output Format

**Prompt:**
> (same as V3) + "Format the answer as a table: Finding | Why it matters | What the editor should do."

**Output:**

| Finding | Why it matters | What the editor should do |
|---|---|---|
| 54% of pages (16,262) are declining in performance | This isn't a minority case — more than half the content needs attention | Start reviewing "down" pages first |
| Declining pages average a click ratio of just 0.32, vs. 0.73 for healthy pages | People see the page but aren't clicking — it's not a visibility problem | Check titles and meta descriptions, not just the article content |
| Google ranking position is nearly identical between declining and healthy pages | The problem isn't SEO ranking | Don't waste time on keyword optimization — focus on click appeal instead |

**Notes:**
- **What changed in the prompt:** requested a 3-column table format.
- **What actually improved in the output:** far easier to scan quickly, every row now ends with a concrete "what to do" — moved from information to action.
- **What still failed:** nothing notable at this step.
- **What I'd try next:** try a constraint to make it even tighter.

---

## Version 5 — added: Constraint (⚠️ this one backfired)

**Prompt:**
> (same as V4) + "Answer in 50 words maximum."

**Output:**
> 54% of pages are declining. Low CTR (0.32 vs 0.73) is the main signal, not ranking position. Prioritize reviewing "down" pages with the lowest CTR first, and check titles and meta descriptions.

**Notes:**
- **What changed in the prompt:** added a 50-word limit.
- **What actually improved in the output:** nothing — this was the weakest version so far.
- **What still failed:** the table disappeared (had to be cut to fit 50 words), the insight that search position "doesn't matter here" got compressed into a single clause that's easy to miss, and the "what to do" step became generic again because there was no room to be specific.
- **What I'd try next:** drop the word constraint, keep the table, and fold the insight into a clean final prompt instead.

**This is the honest "made it worse" moment:** a constraint that looked like it should help ("more concise = better") actually damaged the most important insight in the output.

---

## Final Prompt (reusable — works without me in the room)

```
I'm analyzing content performance data for [dataset/context — e.g. "the Refresh/Content
Opportunity Scoring lane, 30,000 content pages with 90-day traffic metrics"].

Goal: identify which pages need editorial review first, and explain why in a way a
non-technical content editor can act on this week.

Please:
1. Cite specific numbers from the data (percentages, averages, counts) — don't
   generalize without evidence.
2. Avoid technical jargon (e.g. explain "CTR" as "click-through rate" or plain
   language) unless you define it inline.
3. Format the answer as a table: Finding | Why it matters | What the editor should do.
4. Flag any claim where you're inferring beyond what the data directly shows, so I
   can verify it before sharing with the team.
```
