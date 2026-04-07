# Square Face Generator Coding Agent Task Prompt

## Purpose

This document is a ready-to-use prompt for Codex / coding agents to implement the AdSense remediation and site quality upgrade plan for `squarefacegenerator.run`.

It is designed to work together with:

- `docs/adsense-remediation-plan.md`

The goal is to upgrade the site from a thin single-tool landing page into a more complete product website with:

- stronger trust signals
- better site structure
- more indexable content
- more useful internal linking
- better AdSense review readiness
- better long-term SEO / AEO growth potential

---

## Recommended usage

Use this prompt in stages if possible.

Recommended sequence:

1. Phase 1 prompt: foundation and trust pages
2. Phase 2 prompt: examples and guides content layer
3. Phase 3 prompt: sitemap, robots, schema, shareable avatar URL support

If the coding agent is strong and stable, the full prompt can also be used in one pass.

---

# Full implementation prompt

```text
You are working on a Next.js App Router website called “Square Face Generator”.

Repository context:
- This site already has a working avatar generator.
- The generator supports feature selection, color selection, random generation, reset, canvas rendering, and PNG download.
- The current site looks too much like a thin single-tool landing page with repetitive SEO copy, weak trust pages, and weak internal link structure.
- The goal is to improve the site so it feels like a real product website with useful content, stronger trust signals, and better AdSense review readiness.
- Do NOT break the existing generator functionality.

Primary goal:
Turn the site from a “single-page SEO tool” into a more complete product website:
1. Keep the generator.
2. Reduce low-value / repetitive homepage copy.
3. Add trust pages and content sections.
4. Add examples and guides.
5. Improve metadata, internal linking, sitemap, robots, and structured data.
6. Keep the implementation clean, maintainable, and production-ready.

Important constraints:
- Use the existing Next.js App Router structure.
- Preserve current generator behavior unless changes are clearly beneficial.
- Do not remove the generator from the homepage.
- Do not add a database.
- Avoid overengineering.
- Prefer static or lightweight solutions.
- Use TypeScript.
- Keep UI style consistent with the current site.
- Keep the site fast and simple.
- Do not add unnecessary dependencies unless clearly justified.
- Do not generate fake legal claims or fake company details.
- If Vercel Analytics remains enabled, update the Privacy Policy to reflect that honestly.
- Remove obvious template traces such as “v0.app” branding where appropriate.
- Replace placeholder or inconsistent contact/brand details with a coherent site identity based on the current domain: https://squarefacegenerator.run
- Do not overcomplicate the solution. Prefer practical changes that can be reviewed and deployed quickly.

What to implement:

==================================================
PHASE 1 — SITE FOUNDATION AND TRUST
==================================================

1. Update app/layout.tsx
- Improve global metadata.
- Add metadataBase using https://squarefacegenerator.run
- Add proper title template.
- Add canonical support.
- Add Open Graph metadata.
- Add Twitter metadata.
- Remove low-trust template leftovers such as generator metadata pointing to v0.app.
- Keep icons configured properly.

2. Rewrite the homepage in app/page.tsx
The current homepage has too much repetitive keyword-heavy copy.
Refactor it into a cleaner product homepage with these sections:
- Hero section with clear value proposition
- Existing generator component
- “How it works” section with 3 simple steps
- “Use cases” section (Discord, TikTok, X, YouTube, gaming, profile icons)
- “Example styles” preview section linking to example pages
- Short FAQ preview section
- Internal link section linking to Examples, Guides, About, Contact, FAQ
Do NOT keep bloated repetitive SEO paragraphs.
Write concise, helpful, user-readable copy.

3. Upgrade navigation and footer
- Improve footer links.
- Add links to:
  - About
  - Contact
  - FAQ
  - License
  - Examples
  - Guides
  - Privacy Policy
  - Terms of Service
- Keep the footer visually aligned with the current design system.

4. Add trust pages
Create these routes:
- app/about/page.tsx
- app/contact/page.tsx
- app/faq/page.tsx
- app/license/page.tsx

Content expectations:
- About: explain what the tool is, who it is for, and what it helps users do
- Contact: clear email/contact section, feedback/copyright/business inquiry guidance
- FAQ: practical questions about usage, privacy, download, social profile use, and commercial use
- License: clearly explain personal use, social profile use, non-commercial use, and that commercial use may require permission; do not make up complex legal language

5. Rewrite legal pages for consistency
Update:
- app/privacy-policy/page.tsx
- app/terms-of-service/page.tsx

Requirements:
- Make them consistent with actual site behavior
- If Vercel Analytics is enabled, privacy policy must mention anonymous/aggregated analytics honestly
- Remove inconsistent brand/contact/domain references
- Keep the language simple, credible, and relevant to this product
- Do not use obviously generic boilerplate wording if avoidable

==================================================
PHASE 2 — CONTENT LAYER
==================================================

6. Add Examples hub
Create:
- app/examples/page.tsx

This page should:
- Explain what users can make
- Show a grid of example styles
- Link to individual example pages

7. Add Guides hub
Create:
- app/guides/page.tsx

This page should:
- List practical guides
- Organize guides clearly
- Link to individual guide pages

8. Add at least 6 example pages
Create these routes:
- app/examples/cute-square-avatar/page.tsx
- app/examples/gaming-square-avatar/page.tsx
- app/examples/pastel-square-avatar/page.tsx
- app/examples/pixel-square-avatar/page.tsx
- app/examples/anime-square-avatar/page.tsx
- app/examples/discord-square-avatar/page.tsx

Each page should include:
- A strong H1
- Short intro
- Style explanation
- Who it is good for
- Tips for recreating the look using the generator
- Link back to homepage generator
- Internal links to related examples/guides

9. Add at least 6 guide pages
Create:
- app/guides/how-to-make-a-discord-avatar/page.tsx
- app/guides/best-profile-picture-size-for-x/page.tsx
- app/guides/how-to-create-a-cute-avatar/page.tsx
- app/guides/avatar-color-combination-guide/page.tsx
- app/guides/how-to-make-a-pixel-avatar/page.tsx
- app/guides/picrew-alternative-guide/page.tsx

Each guide should:
- Solve a clear user problem
- Be concise but useful
- Avoid fluff
- Include practical tips
- Include links to examples and the homepage tool

10. Add reusable content/preset data
Create lightweight reusable data modules such as:
- lib/avatar-presets.ts
- lib/site-content.ts (optional)

Use them to:
- power example cards
- avoid duplicating titles/descriptions everywhere
- keep content maintainable

==================================================
PHASE 3 — SEO / DISCOVERABILITY / STRUCTURE
==================================================

11. Add sitemap and robots
Create:
- app/sitemap.ts
- app/robots.ts

Requirements:
- Include main routes
- Include example and guide routes
- Point robots to sitemap
- Keep indexing open for the public pages

12. Add structured data support
Create a reusable component such as:
- components/structured-data.tsx

Use it for:
- WebApplication schema on the homepage
- FAQPage schema on FAQ content where appropriate
- BreadcrumbList schema on example/guide pages

13. Add better page-level metadata
For examples, guides, about/contact/faq/license pages:
- unique title
- unique description
- canonical
- useful OG data where possible

14. Improve internal linking
- Homepage should link to examples/guides
- Example pages should cross-link to guides and related examples
- Guide pages should link back to examples and homepage
- Footer should expose trust pages and content hubs

==================================================
PHASE 4 — OPTIONAL BUT STRONGLY RECOMMENDED
==================================================

15. Add shareable avatar URL support without a database
Implement a lightweight URL/state approach:
- encode current AvatarState in the URL
- allow restoring generator state from URL
- add a “Copy Link” or “Share” action in the generator UI

Suggested files:
- lib/avatar-url.ts
- optionally update components/square-face-generator.tsx

If feasible within reasonable effort, also add:
- app/avatar/[slug]/page.tsx

This page can:
- restore an avatar preset/state from URL data
- show a preview
- include “Remix this avatar” and “Open in generator” links

Keep it simple. No database. No authentication.

==================================================
QUALITY REQUIREMENTS
==================================================

- Preserve generator functionality.
- Keep styles visually consistent.
- Avoid keyword stuffing.
- Avoid duplicated long-form copy.
- Prefer clarity over SEO spam.
- Use server components where sensible.
- Use client components only where needed.
- Keep code organized and easy to review.
- Do not leave dead routes or broken links.
- Do not invent missing assets unless handled with a clean placeholder/fallback strategy.
- Ensure the site builds cleanly.

==================================================
DELIVERABLES
==================================================

1. Inspect the current structure first.
2. Produce a short implementation plan.
3. Implement the code changes.
4. Summarize all changed files.
5. Explain any assumptions made.
6. Highlight any places where manual content refinement may still help.
7. Use small reusable data structures instead of hardcoding everything inline when it improves maintainability.

Focus on practical, reviewable improvements rather than excessive abstraction.
```

---

# Phase-based prompts

## Phase 1 prompt — foundation and trust pages

```text
You are modifying a Next.js App Router site called “Square Face Generator”.

Goal:
Improve the site foundation, trust signals, and homepage quality without changing the core generator functionality.

Tasks:
1. Update app/layout.tsx
- add metadataBase: https://squarefacegenerator.run
- improve title/description
- add Open Graph and Twitter metadata
- add canonical support
- remove low-trust template leftovers like v0.app generator metadata

2. Refactor app/page.tsx
- keep the generator on the homepage
- remove repetitive keyword-stuffed copy
- replace it with:
  - hero
  - how it works
  - use cases
  - example styles preview
  - short FAQ preview
  - internal links to examples/guides/about/contact

3. Update components/footer.tsx
Add links to:
- About
- Contact
- FAQ
- License
- Examples
- Guides
- Privacy Policy
- Terms of Service

4. Add these pages:
- app/about/page.tsx
- app/contact/page.tsx
- app/faq/page.tsx
- app/license/page.tsx

5. Rewrite:
- app/privacy-policy/page.tsx
- app/terms-of-service/page.tsx

Requirements:
- Keep wording honest and product-specific
- If Vercel Analytics remains enabled, privacy policy must mention analytics honestly
- Use consistent branding and contact info for squarefacegenerator.run
- Keep code clean and TypeScript-friendly

Deliverables:
- implement changes
- summarize changed files
- note any follow-up work needed
```

---

## Phase 2 prompt — examples and guides content layer

```text
Continue improving the Next.js App Router site “Square Face Generator”.

Goal:
Add a useful content layer so the site feels like a real product website, not a thin tool page.

Tasks:

1. Add hub pages:
- app/examples/page.tsx
- app/guides/page.tsx

2. Add at least these example pages:
- app/examples/cute-square-avatar/page.tsx
- app/examples/gaming-square-avatar/page.tsx
- app/examples/pastel-square-avatar/page.tsx
- app/examples/pixel-square-avatar/page.tsx
- app/examples/anime-square-avatar/page.tsx
- app/examples/discord-square-avatar/page.tsx

3. Add at least these guide pages:
- app/guides/how-to-make-a-discord-avatar/page.tsx
- app/guides/best-profile-picture-size-for-x/page.tsx
- app/guides/how-to-create-a-cute-avatar/page.tsx
- app/guides/avatar-color-combination-guide/page.tsx
- app/guides/how-to-make-a-pixel-avatar/page.tsx
- app/guides/picrew-alternative-guide/page.tsx

4. Add reusable content/preset data if helpful:
- lib/avatar-presets.ts
- optional lightweight content config files

Requirements for every content page:
- unique H1
- concise intro
- practical value
- no filler
- link back to homepage generator
- cross-link to related examples/guides

Also:
- improve internal linking across homepage, footer, examples, and guides
- keep styling consistent with the existing site

Deliverables:
- implement the pages
- summarize file changes
- list any pages that may still need manual copy polishing
```

---

## Phase 3 prompt — sitemap, robots, schema, and share links

```text
Continue improving the Next.js App Router site “Square Face Generator”.

Goal:
Improve discoverability, structure, and product depth.

Tasks:

1. Add:
- app/sitemap.ts
- app/robots.ts

Include:
- homepage
- trust pages
- examples hub
- guides hub
- all example pages
- all guide pages

2. Add reusable structured data support
Create:
- components/structured-data.tsx

Use it for:
- WebApplication schema on homepage
- FAQPage schema where appropriate
- BreadcrumbList on example and guide pages

3. Improve page-level metadata
Ensure example/guide pages have:
- unique title
- unique description
- canonical
- useful OG metadata when possible

4. Add lightweight shareable avatar URL support
Implement URL-based avatar state sharing without a database:
- encode current avatar state in URL
- restore avatar state from URL
- add a “Copy Link” or similar action to the generator UI

Suggested files:
- lib/avatar-url.ts
- update components/square-face-generator.tsx

Optional if reasonable:
- app/avatar/[slug]/page.tsx
This page should restore a shared avatar state and offer:
- preview
- Remix this avatar
- Open in generator

Requirements:
- keep implementation lightweight
- no database
- no auth
- do not break existing generator features

Deliverables:
- implement changes
- summarize changed files
- explain assumptions
```

---

# Notes for maintainers

## Why this document exists

Many coding agents perform better when given:

- explicit file targets
- ordered phases
- design constraints
- output quality rules
- clear non-goals

This prompt is structured to reduce common agent failure modes:

- unnecessary abstraction
- overengineering
- breaking existing generator behavior
- adding too many dependencies
- generating generic or low-trust legal text
- recreating the same keyword-heavy copy problem on new pages

---

## Non-goals

This prompt does **not** ask the coding agent to:

- redesign the whole site visually
- add a backend or database
- add auth
- build a CMS
- build user accounts
- introduce heavy architecture changes
- replace the current generator rendering model

---

## Recommended review checklist after agent output

After the coding agent finishes, manually verify:

- the generator still works
- pages render without broken links
- metadata is unique across new pages
- About / Contact / FAQ / License pages feel credible
- Privacy Policy matches actual analytics usage
- homepage is shorter and less repetitive
- example/guide pages are not thin copies of each other
- sitemap and robots are accessible
- internal links are visible from homepage and footer
- no obvious placeholder text remains

---

## Suggested next document

If needed, create a follow-up internal doc such as:

- `docs/manual-copy-refinement-checklist.md`

for polishing copy tone after the coding agent completes the first pass.
