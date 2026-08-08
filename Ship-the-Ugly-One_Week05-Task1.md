# Week 5 — Ship the Ugly One

**Evelyn Anastasia · General AI Fluency**

---

## Live URL

[https://anstevelynnn.web.app/](https://anstevelynnn.web.app/)

All pages in the sitemap (About, Skills, Projects, Experience, Organization, Certificate, Blog, Contact) are reachable and navigation works.

---

## Real Person Reaction

**Reviewer:** WhatsApp contact

**First impression:** The site feels clean and modern, the design is nice and not too crowded, the colors work well.

**What was confusing:** Mixing English and Indonesian across different pages with no clear pattern. The project descriptions were also noted as having a lot of text, making them hard to scan quickly.

**Reaction to the PureStream case study:** The story landed well — the reviewer specifically liked the honesty (wrong sensor readings, the calibration problem, the unexpected final result). But asked for standard Indonesian in the description instead of slang.

**Bug found:** The Experience page was failing to load / appeared empty — traced to the section `div` missing the `active` class (a leftover from the site's earlier single-page-app structure that hadn't been fully updated to multi-page). Fixed and redeployed before this submission.

---

## Still Ugly List

- English/Indonesian mixing is still inconsistent across pages
- Project descriptions (especially PureStream) are still too long to scan quickly
- Slang in the PureStream description needs to be replaced with standard Indonesian
- Blog page is still empty, no articles published yet
- Experience page doesn't yet include the FlyRank internship (case study not ready yet)
- Profile card still shows "Class of 2023" — needs to be double-checked
- PLN experience video doesn't have a proper image poster/thumbnail yet
