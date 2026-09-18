# St. Peter Lutheran Church Foundation

This repository supports the **St. Peter Lutheran Church Foundation (SPLCF)** website and related project resources. It contains the public-facing website source, Foundation reference material, project guidance, and supporting files used to maintain and develop the site.

The published site is live at [`stpeterlutheranfoundation.org`](https://stpeterlutheranfoundation.org).

## Repository Guidance

Foundation-specific guidance and reference information can be found in [`assets/guidance.md`](assets/guidance.md). This file is intended to serve as a central reference for basic Foundation information and standardized practices, including board information and Foundation meeting guidance.

## Agent Instructions

The repository includes [`AGENTS.md`](AGENTS.md), which contains instructions and context for AI coding agents and other automated development tools working with this project.

The repository also includes [`CLAUDE.md`](CLAUDE.md) for Claude-specific project guidance.

## Deployment

The site is hosted on GitHub Pages and redeployed automatically by [`.github/workflows/static.yml`](.github/workflows/static.yml) on every push to `main`. That workflow spellchecks the repository, stages only the public files into a build directory, verifies every local link and asset in the staged pages, and deploys only if all of it passes.

Adding a file to the repository does not publish it. A new page or asset reaches the site only once the workflow's staging and link-verification steps name it.

## Spellcheck Word List

The [`.wordlist.txt`](.wordlist.txt) file contains project-specific words, names, terminology, and other accepted terms used by the repository's spellcheck configuration. Add legitimate Foundation or project terminology to this file when it should be accepted by automated spellchecking.

## Key Files

- `index.html` — Main website page.
- `404.html` — Not-found page shown for any address that does not exist.
- `Gift Acceptance Policy.dc.html` — Published Gift Acceptance Policy page.
- `support.js` — Generated runtime that renders the policy page. Never edit it by hand; it is rebuilt from an upstream project.
- `favicon.ico` — Browser tab icon, cropped from the church logo.
- `apple-touch-icon.png` — Home-screen icon for phones and tablets, same crop.
- `assets/` — Website assets and Foundation reference material.
- `assets/guidance.md` — Foundation guidance and organizational reference information.
- `AGENTS.md` — Instructions for AI agents working in the repository.
- `CLAUDE.md` — Claude-specific project instructions.
- `.wordlist.txt` — Accepted project-specific words for automated spellchecking.
- `.spellcheck.yml` — Spellcheck configuration.
- `CNAME` — The custom domain the published site answers on.
- `.github/workflows/static.yml` — Validation and GitHub Pages deployment workflow.
- `.github/dependabot.yml` — Monthly grouped updates for the workflow's actions.

## Purpose

The goal of this repository is to provide a maintainable home for the St. Peter Lutheran Church Foundation website while retaining the documentation and guidance needed to keep Foundation information and future development consistent.
