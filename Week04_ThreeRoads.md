# Week 4 — Three Roads: Choose Your Stack with AI

**Evelyn Anastasia · General AI Fluency**

---

## Constraints

- **Budget:** free only
- **Skill level:** strong — comfortable full-stack, familiar with JS frameworks, understands basic backend
- **Portfolio needs** (from content map): image galleries, repo/demo links, downloadable CV, long-form case studies, plus a contact form that actually writes data
- **Dynamic requirement:** yes — the contact form writes to Firebase (not sent as email), so some backend/database is already needed, this isn't a fully static site

---

## Three Options Considered

### Option 1 — Vanilla HTML/CSS/JS + Firebase Hosting + Firestore *(current stack)*
- **Build:** plain HTML/CSS/JS, no build step
- **Host:** Firebase Hosting (free)
- **Backend:** Firestore, just for storing contact form submissions
- **Trade-off:** easiest to understand and maintain right now, but every new page means copy-pasting the header/nav manually across HTML files. Changing the nav bar means editing it in 8 separate files.

### Option 2 — Static Site Generator (e.g. Eleventy/Astro) + Firebase Hosting + Firestore
- **Build:** templates/partials for header/footer/nav, edit once and it generates across all pages
- **Host:** Firebase Hosting or Netlify (free)
- **Backend:** same, Firestore for the form only
- **Trade-off:** cleaner to maintain long-term given the site will have 8 pages with repeated structure, but adds a new build step to learn, and means migrating the already-live site — a rewrite, not an addition.

### Option 3 — React/Next.js SPA + Vercel/Firebase + Firestore
- **Build:** reusable components, client-side routing
- **Host:** Vercel (free) or Firebase Hosting
- **Backend:** Firestore, possibly API routes if server-side logic is needed later
- **Trade-off:** most powerful and reusable, but most of the portfolio content is static (text, images, links) — doesn't need that level of interactivity. The build tooling and state management overhead isn't worth it here.

---

## Pressure-Testing the Front-Runner (Option 1)

- **What breaks if I pick the simplest?** As pages keep growing, manual nav/header maintenance gets tedious — but for 8 pages, it's still manageable, not a real scaling problem.
- **What do I maintain if I pick the most powerful?** A build pipeline, dependency updates, and likely learning curve for features I wouldn't use, since the content itself is static.
- **Can I finish in two weeks?** Option 1: already done (it's live). Options 2/3 need a rewrite from scratch, which risks not finishing on time while also managing the internship.
- **Does it show my work the way it needs to be shown?** Option 1 already proves it can handle galleries, repo links, CV downloads, and the form — everything in my content map is already met.

---

## Decision

I chose vanilla HTML/CSS/JS + Firebase Hosting + Firestore, because it's what I'm already using and it's already live. I don't need a complex backend — just writing contact form data, and Firestore is enough for that. I considered a static site generator to avoid manually copy-pasting the nav across pages, but that means rewriting a site that already works, and my time is limited because of the internship. I skipped React/Next.js because most of my content is static — there's no strong reason to add that much build tooling. I can maintain the vanilla version myself since I wrote it from scratch, and it already shows my work the way it needs to be shown (gallery, repo links, CV download, form).
