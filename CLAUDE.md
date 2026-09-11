# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A static marketing website for All About Landscaping, a landscaping business in Pontiac, MI. Two files, no build step:

- `index.html` — all page content and structure
- `styles.css` — all styling

There is no package.json, build tool, linter, or test suite. To view changes, open `index.html` directly in a browser or serve the directory with any static file server (e.g. `python3 -m http.server`).

## Origin and design source of truth

The visual design (layout, colors, copy) was drafted in a Claude Design canvas project ("All About Landscaping Website") and then hand-converted here into plain, dependency-free HTML/CSS — the canvas's templating syntax (`<sc-for>`, `{{ }}` bindings, `style-hover` attributes, the `<image-slot>` custom element) does not exist in this repo; those were all resolved into static markup and real CSS `:hover` rules. If the canvas project is updated, changes need to be re-applied here manually — there is no sync mechanism.

## Structure notes

- Single page, sections linked by anchor (`#about`, `#services`, `#areas`, `#contact`), navigated via the header nav.
- The phone number (`248-466-9929`) and address (`699 East Tennyson Ave, Pontiac, MI 48340`) are hardcoded in multiple places (header, hero, contact section, footer, and `tel:` links) — when either changes, update all occurrences.
- The services list (`#services`) and service-area list (`#areas`) are static, repeated `<div>` items rather than generated from a data source — add/remove list entries by editing the markup directly in each section.
- The `.hero` background in `styles.css` is currently a CSS placeholder pattern, not a real photo (the source image from the design canvas was a flyer screenshot, not a usable job photo). A comment directly above `.hero` in `styles.css` shows the exact CSS to swap in a real photo once one is available.

## Deployment

Hosted on Cloudflare Workers (static assets) at `https://all-about-landscaping.all-about-landscaping.workers.dev/`. **This is a manual dashboard upload, not connected to this git repo** — there is no CI/CD. Committing or pushing here does not update the live site; after editing `index.html`/`styles.css`, the updated folder must be re-uploaded through the Cloudflare Workers & Pages dashboard (drag-and-drop) to go live.
