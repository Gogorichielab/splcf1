# Project Guidance — St. Peter Lutheran Church Foundation

This repository supports the public website and published materials of the **St. Peter Lutheran Church Foundation**.

Use this file as a concise operating guide for anyone making changes. For detailed agent and tooling instructions, read [`AGENTS.md`](AGENTS.md). Claude-specific instructions live in [`CLAUDE.md`](CLAUDE.md).

## Purpose

The site should help congregation members and prospective donors understand:

- the Foundation's mission and role;
- available ways to give;
- planned-giving and gift-acceptance information; and
- official Foundation policies and governing documents.

Write for a broad, non-technical audience. Favor clarity, dignity, accessibility, and a warm, low-pressure tone.

## Source of truth

Before editing content, prefer official Foundation records over assumptions or inferred wording. Examples include:

- approved board minutes;
- adopted policies;
- bylaws and governing documents;
- approved donor-facing language; and
- current information supplied by Foundation officers or the church office.

Do not invent names, titles, dates, financial terms, policy requirements, or legal/tax claims.

## Content rules

Giving, tax, estate-planning, and policy language is substantive. Do not casually rewrite or simplify it in a way that changes meaning.

When editing donor-facing content:

1. Preserve factual and policy accuracy.
2. Use plain language without pressure, urgency, or exaggerated claims.
3. Distinguish general educational information from legal, tax, or financial advice.
4. Keep terminology consistent across the site and official documents.
5. When a requested change could alter legal or policy meaning, flag it for Foundation review rather than guessing.

## Privacy and sensitive information

The repository is public and its root is published through GitHub Pages.

Never commit:

- donor names or donor-identifying information unless explicitly approved for public publication;
- account numbers, tax IDs, banking information, signatures, private email addresses, or phone numbers;
- confidential board discussions or draft deliberations;
- credentials, tokens, secrets, or private configuration; or
- unapproved drafts that are not intended to become public.

Use anonymized or placeholder data when examples are needed.

## Website constraints

Keep the site simple and dependable.

- The project is a static site with no framework, backend, database, or build system.
- `index.html` is the main site and intentionally contains inline styling.
- Do not add dependencies, trackers, analytics, or a JavaScript framework unless explicitly requested and approved.
- `support.js` is generated runtime code and must not be hand-edited.
- Preserve the established typography, visual identity, and color palette unless a redesign is explicitly requested.
- Treat mobile usability and readable text sizing as requirements, not optional polish.

## Change discipline

Make the smallest change that fully satisfies the request.

Before committing:

- read the surrounding content or markup;
- confirm links and file paths;
- verify the page at phone and desktop widths when visual changes are involved;
- check that no private or draft information has entered the public repository; and
- confirm that policy or donor-facing wording still matches the intended source material.

## Git and commits

All commits must follow the Conventional Commits rules documented in [`AGENTS.md`](AGENTS.md#commit-conventions--conventional-commits).

Examples:

```text
docs: add project guidance
feat(giving): add planned giving information
fix(content): correct board officer title
fix(layout): improve mobile navigation spacing
```

Keep one logical change per commit.

## Working with Foundation records

When creating or editing minutes, policies, notices, or other official records:

- use full names and titles where the governing format requires them;
- retain motions, seconds, votes, approvals, and adjournment details accurately;
- clearly distinguish approved records from drafts;
- do not manufacture missing procedural details; and
- preserve the meaning of adopted language.

If a transcript is the source, clean up speech disfluencies while preserving decisions, motions, votes, assignments, and material discussion.

## Review standard

A change is ready when it is accurate, respectful of Foundation governance, safe for public publication, easy for congregation members to understand, and no more technically complex than necessary.
