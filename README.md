# About

I'm a technology leader who builds things to learn them. The projects here represent my most recent forays into AI driven coding, largely utilizing Claude Code. I present them as proof-of-concept, and as support for my engagement with these technologies reaching beyond the theoretical.

Currently, I move back and forth bewteen

- an AI-powered job search pipeline (because of course),
- a website that produces PDF's on demand for sets of reference cards (specifically, D&D spell cards, because the homebrew was out of control)
- a suite of technical enhancements to a passion project around the Negro Leagues, and
- an NFL simulation engine (because sports simulations are hard and fascinating).

More info at each below.

---

## Active Projects

### Alemi Spells *(private)*
A members-only web application for managing and printing D&D 5e spell cards. ~2,000 spells imported from structured source documents, stored in SQLite, and rendered as print-ready PDF card sheets. Includes fairly complex search interface, and a user management component.

**Stack:** Python · Flask · SQLite · Playwright · Jinja2 · vanilla JS  
**Interesting problems:** Import process from repetitively structured Word documents, text overflow detection and automatic multi-card splitting with related dynamic formatting; a named-rule auto-formatter for spell description markup; Playwright-driven PDF generation; real human usable search interface covering multi-variant queries.

Publicly hosted via DigitalOcean, which has also required a lifelong Windows nerd to delve back into the arcane reaches of LINUX, which is good for me.

This is the most _complete_ project: from vision through prototypes all the way through public usage. Mostly done intentionally via Claude Chat, as I wanted to be able to both modify and examine all of the code--from python files through HTML and css--as a learning process, and to shake off whatever development rust I was feeling.

---

### [i9s](https://github.com/mknnmknn/i9s) *(public)*

Documentation and tooling for a Negro Leagues historical projection project at [i9s.org](https://www.i9s.org). Built atop WordPress, data served by Pods.

**Interesting problems:** Building an import engine for future player display, improving Pods' native displays to include additional information and totals, data quality tools and a custom admin suite.

---

### WFL Sim *(private)*
A cross-era NFL football historical simulation engine. Players are rated by season; outcomes are probability-driven rather than physics-based.

**Stack:** Python · Flask · SQLite · SQLAlchemy · HTMX · Alpine.js  
**Interesting problems:** Simulating plays that "feels like" an actual sport: currently, focused on creating a structure for individual plays that is sensitive to the contributions of all 22 players on the field. Cross-era player normalization and rating systems; single-player simulation loop with meaningful variance.

---

### [career-ops-dml](https://github.com/mknnmknn/career-ops-dml) *(original fork public, customizations maintained locally)*
AI-powered job search pipeline built on Claude Code. 14 skill modes, Go TUI dashboard, Playwright PDF generation, batch processing with parallel workers. Active daily use. All credit to santifer's original work.

---

*Private repos are not open for contributions or licensing at this time.*
