# About

I'm a technology leader who builds things to learn them. The projects here are how I stay close to the work — not as a credential, but because the best way to have a real opinion about a technology is to use it to solve a real problem. Currently: an AI-powered job search pipeline (because of course), a D&D spell card renderer (because the homebrew was out of control), technical enhancements to a passion project around the Negro Leagues, and an NFL simulation engine (because sports simulations are hard and fascinating).

---

## Active Projects

### Alemi Spells *(private)*
A web application for managing and printing D&D 5e spell cards. ~2,000 spells imported from structured source documents, stored in SQLite, and rendered as print-ready PDF card sheets.

**Stack:** Python · Flask · SQLite · Playwright · Jinja2 · vanilla JS  
**Interesting problems:** Import process from repetitively structured Word documents, Spell card overflow detection and automatic multi-card splitting with related dynamic formatting; a named-rule auto-formatter for spell description markup; Playwright-driven PDF generation.

---

### [i9s](https://github.com/mknnmknn/i9s) *(public)*

Documentation and tooling for a Negro Leagues historical projection project at [i9s.org](https://www.i9s.org). Built atop WordPress, data served by Pods.

---

### WFL Sim *(private)*
A cross-era NFL fantasy football simulation engine. Players are rated by season; outcomes are probability-driven rather than physics-based.

**Stack:** Python · Flask · SQLite · SQLAlchemy · HTMX · Alpine.js  
**Interesting problems:** Simulating plays that "feels like" an actual sport: currently, focused on creating a structure for individual plays that is sensitive to the contributions of all 22 players on the field. Cross-era player normalization and rating systems; single-player simulation loop with meaningful variance.

---

### [career-ops-dml](https://github.com/mknnmknn/career-ops-dml) *(original fork public, customizations maintained locally)*
AI-powered job search pipeline built on Claude Code. 14 skill modes, Go TUI dashboard, Playwright PDF generation, batch processing with parallel workers. Active daily use. All credit to santifer's original work.

---

*Private repos are not open for contributions or licensing at this time.*
