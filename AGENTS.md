# AGENTS.md — St. Peter Lutheran Church Foundation

Guidance for AI agents (Claude, Codex, Copilot, Cursor, etc.) and humans working in
this repository. Read this file before writing, editing, or reviewing anything here.

For current Foundation institutional facts — including Board membership, contact
information, and the standard board-meeting agenda/minutes format — also read
[`assets/guidance.md`](assets/guidance.md) and treat it as the concise reference
for recurring Foundation information.

---

## Project overview

A single-page marketing and information site for the **St. Peter Lutheran Church
Foundation**. Its job is to explain the Foundation's mission, describe the ways a
person can give (cash, appreciated stock, IRA distributions, bequests, and similar
planned gifts), and publish the Foundation's governing documents.

- **Audience:** congregation members and prospective donors — largely non-technical,
  many on phones or older desktop browsers.
- **Product shape:** a static site. No build step, no framework, no backend, no
  database, no analytics pipeline.
- **Hosting:** GitHub Pages, deployed by `.github/workflows/static.yml` on every
  push to `main`. The workflow uploads the whole repository root as the Pages
  artifact, so file paths in the repo are the URLs on the live site.

### Repo layout

```
/
├── index.html                     ← The entire site (inline CSS, hand-authored)
├── Gift Acceptance Policy.dc.html ← Published policy document page
├── support.js                     ← GENERATED runtime for .dc.html documents — do not edit
├── assets/church-logo.png         ← Logo used by index.html
├── uploads/                       ← Additional uploaded imagery
├── scraps/                        ← Design references and screenshots, not shipped content
└── .github/workflows/static.yml   ← GitHub Pages deploy
```

### Conventions that matter

- `index.html` carries its styling inline. That is intentional for a
  zero-build site — keep edits local and readable rather than extracting a
  design system.
- `support.js` is generated (`// GENERATED from dc-runtime/src/*.ts — do not edit`).
  Never hand-edit it; if it needs to change, that change belongs upstream.
- Typography is Cormorant Garamond for headings; keep the existing typographic
  scale and colour palette unless a restyle is explicitly requested. A previous
  colour-scheme change was reverted — do not reintroduce one on your own
  initiative.
- Content about gifts, tax treatment, and Foundation policy is **substantive, not
  filler**. Do not reword, summarise, or "improve" it without an explicit request;
  when in doubt, leave the wording alone and ask.
- Everything in the repo root is published. Do not commit drafts, personal data,
  or donor information.

### Working agreement

1. Read the surrounding markup before changing it.
2. Make the smallest change that satisfies the request.
3. Verify by opening `index.html` in a browser at both phone and laptop widths.
4. Keep the site static — no dependencies, no bundler, no tracking scripts.

---

## Commit conventions — Conventional Commits

Every commit in this repository **must** follow the
[Conventional Commits 1.0.0](https://www.conventionalcommits.org/en/v1.0.0/)
specification. This applies to agents and humans alike, and to every branch.

### Format

```
<type>(<optional scope>): <description>

<optional body>

<optional footer(s)>
```

- **Type** is required and lowercase.
- **Scope** is optional, lowercase, and names the area touched (see below).
- **Description** is a short imperative summary — "add", not "added"/"adds" — no
  trailing period, and ideally ≤ 72 characters for the whole subject line.
- **Body** explains *why*, wrapped at ~72 columns, separated by a blank line.
- **Footers** carry metadata: `Refs: #12`, `Closes: #12`, `BREAKING CHANGE: ...`.

### Allowed types

| Type | Use for |
|---|---|
| `feat` | A new user-visible section, page, or capability |
| `fix` | Correcting broken markup, links, layout, or wrong information |
| `docs` | README, this file, or other documentation |
| `style` | Formatting/visual changes with no change in content or behaviour |
| `refactor` | Restructuring markup with no visible change |
| `perf` | Image or load-time improvements |
| `test` | Adding or updating tests |
| `build` | Asset pipeline or generated-file updates |
| `ci` | `.github/workflows/**` changes |
| `chore` | Housekeeping that doesn't fit above |
| `revert` | Reverting a previous commit |

### Suggested scopes

`content`, `giving`, `policy`, `layout`, `assets`, `pages`, `deps`

### Breaking changes

Mark either with a `!` after the type/scope or with a `BREAKING CHANGE:` footer
(both is fine). For this site, "breaking" means a changed URL or a removed page.

```
feat(pages)!: move gift acceptance policy to /policies/gift-acceptance.html

BREAKING CHANGE: the previous /Gift Acceptance Policy.dc.html URL now 404s;
add a redirect or update any printed materials that reference it.
```

### Examples

```
feat(giving): add IRA qualified charitable distribution section
fix(layout): stop hero heading overflowing on 320px screens
docs(agents): document conventional commit requirements
style(content): align section spacing with the rest of the page
ci(pages): pin actions/checkout to v4
chore(assets): compress church-logo.png
```

### Rules of thumb

- One logical change per commit. Do not mix content edits with restyling.
- Never commit generated output and source changes in the same commit as
  unrelated content edits.
- Pull request titles follow the same format as commit subjects, so a squash
  merge produces a valid conventional commit.
- If a commit needs "and" in its description, it should probably be two commits.

---

## Skills to use

This project expects agents to work with the following skill packs. Install them
once, then invoke them by name or slash command as the task warrants.

### 1. ponytail — write the least code that works

<https://github.com/DietrichGebert/ponytail>

Claude Code (send as **two separate prompts**):

```
/plugin marketplace add DietrichGebert/ponytail
/plugin install ponytail@ponytail
```

Other agents: copy the matching rules file from the repo — `.cursor/rules/`,
`.windsurf/rules/`, `.clinerules/`, `.github/copilot-instructions.md`,
`.kiro/steering/ponytail.md`, or the repo's `AGENTS.md` for everything else.

Commands: `/ponytail [lite|full|ultra|off]`, `/ponytail-review`,
`/ponytail-audit`, `/ponytail-debt`, `/ponytail-gain`, `/ponytail-help`.

**Use it here:** this is a static, hand-authored site — ponytail's default posture
is exactly right. Run `/ponytail-review` on the diff before opening a PR, and
treat any suggestion to add a framework, build step, or abstraction as a signal
to stop.

### 2. marketing skills — copy, SEO, and campaign work

<https://github.com/coreyhaines31/marketingskills>

```bash
npx skills add coreyhaines31/marketingskills
# or a subset:
npx skills add coreyhaines31/marketingskills --skill copywriting seo-audit
```

Claude Code plugin:

```
/plugin marketplace add coreyhaines31/marketingskills
/plugin install marketing-skills
```

**Use it here:** headline and body copy for giving sections, page structure and
site architecture, SEO audits, schema markup for a local organisation, and
donor-facing email or announcement copy. Anything that changes what the page
*says* to a donor is marketing work — reach for these skills rather than
improvising. Keep the Foundation's voice: warm, plain, never high-pressure.

### 3. business analysis skills — framing before building

<https://github.com/45ck/business-analysis-skills>

```bash
git clone https://github.com/45ck/business-analysis-skills.git
cd business-analysis-skills
bash install.sh          # installs to ~/.claude/skills/ and ~/.agents/skills/
```

Project-level instead: `cp -R .claude .agents /path/to/this-repo/`.

Useful entry points: `/business-problem-framing`, `/stakeholder-analysis`,
`/requirements-elicitation`, `/acceptance-criteria-writer`,
`/requirements-quality-check`, `/assumptions-constraints-log`.

**Use it here:** when a request arrives as a vague wish ("we should make it
easier to give"), frame the problem and write acceptance criteria before
touching `index.html`. Stakeholders include the Foundation board, the church
office, and donors — `/stakeholder-analysis` is worth the five minutes.

### How they fit together

1. **Frame** with business-analysis skills — what problem, whose, done when?
2. **Draft** the donor-facing content with the marketing skills.
3. **Build** under ponytail — the smallest change that ships it.
4. **Commit** using Conventional Commits, one logical change at a time.
