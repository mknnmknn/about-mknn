# About

I build things to learn them. The projects here represent my most recent forays into AI driven coding, largely utilizing Claude Code. I present them as proof-of-concept, and as support for my engagement with these technologies reaching beyond the theoretical.

Currently, I spend my programming time moving back and forth between

- an AI-powered job search pipeline (because of course),
- a website that produces PDFs on demand for sets of reference cards (specifically, D&D spell cards, because the homebrew was out of control),
- a suite of technical enhancements to a passion project around the Negro Leagues, and
- an NFL simulation engine (because sports simulations are hard and fascinating), and
- a long-running, cross-era baseball simulation with an LLM-driven co-commisioner (believe it or not, this may be the most challenging in terms of the application of AI to real-world problems).

More info at each below.

---

## Active Projects

### Alemi Spells *(private)*
A members-only web application for managing and printing D&D 5e spell cards. ~2,000 spells imported from structured source documents, stored in SQLite, and rendered as print-ready PDF card sheets. Includes fairly complex search interface, and a user management component.

**Stack:** Python · Flask · SQLite · Playwright · Jinja2 · vanilla JS  
**Interesting problems:** Import process from repetitively structured Word documents, text overflow detection and automatic multi-card splitting with related dynamic formatting; a named-rule auto-formatter for spell description markup; Playwright-driven PDF generation; search interface covering multi-field, multi-variant queries with a UX design suitable for real humans with relatively low tolerance for technical friction.

Publicly hosted via DigitalOcean, which has also required a lifelong Windows nerd to delve back into the arcane reaches of Linux, which is good for me.

This is the most _complete_ project: from vision through prototypes all the way through public usage. Mostly done intentionally via Claude Chat, as I wanted to be able to both modify and examine all of the code--from python files through HTML and css--as a learning process, and to shake off whatever development rust I was feeling.

I plan to release this publicly with a db seeded with the public domain spells for 5e.

---

### [i9s](https://github.com/mknnmknn/i9s) *(public)*

Documentation and tooling for a Negro Leagues historical projection project at [i9s.org](https://www.i9s.org). Built atop WordPress, data served by Pods.

**Interesting problems:** Building an import engine for future player display, improving Pods' native displays to include additional information and totals, data quality tools and a custom admin suite.

There were things I wanted to do for years--ranging from career totals to administrative tooling for data import and quality control--that were always full of a little too much friction to implement. This is a strong example of how LLMs can be used to eliminate that surrounding friction, allowing me to focus solely on the desired features.

---

### WFL Sim *(private)*
A cross-era NFL football historical simulation engine. Players are rated by season; outcomes are probability-driven rather than physics-based.

**Stack:** Python · Flask · SQLite · SQLAlchemy · HTMX · Alpine.js  
**Interesting problems:** Simulating plays that "feels like" an actual sport: currently, focused on creating a structure for individual plays that is sensitive to the contributions of all 22 players on the field. Cross-era player normalization and rating systems; single-player simulation loop with meaningful variance.

---

### [mediamonkey-wrench](https://github.com/mknnmknn/mediamonkey-wrench) (public)

Tools around [MediaMonkey 5](https://www.mediamonkey.com/) and listening data. First tool — `listen-here` — drafts monthly listening-recap posts for the WordPress engine at [mankinlevine.com](https://mankinlevine.com).

**Stack:** Python · SQLite · WordPress REST API · HTML · external integrations

---

### WBL (The Whirled Baseball League) *(private)*
A cross-era baseball simulation.

The relevance here is the challenge of using an LLM as a sounding board/co-commisioner. It's quite a hill to climb: how to force an LLM to draw hard boundaries around what it is allowed to know (in-game knowledge) and other extraneous information (who Roberto Clemente actually was IRL and his year by year record for the Pittsburgh Pirates). Combine that with the challenge of how to architect the system memory: what needs to be always available, what should the LLM fetch on demand, etc. and you have a fascinating set of LLM challenges.

---

### [career-ops-dml](https://github.com/mknnmknn/career-ops-dml) *(original fork public, customizations maintained locally)*
AI-powered job search pipeline built on Claude Code. 14 skill modes, Go TUI dashboard, Playwright PDF generation, batch processing with parallel workers. Active daily use. All credit to santifer's original work.

---
[LinkedIn](https://www.linkedin.com/in/daniel-m-levine/) | [LinkedIn Articles](https://www.linkedin.com/in/daniel-m-levine/recent-activity/all/)

[Personal Blog](https://mankinlevine.com/)

---

*Private repos are not open for contributions or licensing at this time.*
