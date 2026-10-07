# About

The projects here represent my most recent forays into AI-driven coding, largely in Claude Code. I present them as proof of concept, and as support for how my engagement with these technologies reaches beyond the theoretical.

Right now I spend my programming time moving back and forth between

- an NFL simulation engine (because sports simulations are hard and fascinating),
- a long-running, cross-era baseball league with an LLM-driven co-commissioner (believe it or not, this may be the most challenging in terms of applying AI to real-world problems),
- an AI-powered job search pipeline (because of course),
- a suite of technical enhancements to a passion project around the Negro Leagues,
- a website that produces PDFs on demand for sets of reference cards (specifically, D&D spell cards, because the homebrew was out of control), and
- a small toolkit for my music library.

More on each below. First, though, what they have in common.

---

## What keeps coming up

The same few problems show up in all of them. This issue is, I think, at the crux of the challenge facing most AI deployments, from the personal to the enterprise.

**The LLM is a collaborator with no memory.** Every session starts from zero. So in each of these, the real engineering ended up being the arrangement around the model: what it always needs to know, what it should go look up, where decisions get written down so the 90th session doesn't reopen what the 12th settled, and how a correction becomes a rule that actually holds while comments do not become lazily translated as ultimatums.

That last pair is harder than it sounds. A rule filed somewhere the model doesn't read doesn't, in any meaningful sense, exist, and even the rules it does read wear off. And, an over-interpreted comment that is read as a rule can dictate later behavior in unexpected ways. It's knowledge management and governance, the same problems as running a team, compressed into a much tighter loop. And note that the LLM's preferred solve--_let me just make a note of that so it doesn't recur again_--is often numbingly ineffective.

**Perfect information doesn't exist.** It's easy to build these systems in a perfectly informed world. Those don't really exist in real-world applications, and they don't exist in any project here either. This is part of why LLMs are so amazing at demos and sandbox exercises: when nothing exposes gaps in the data or edge cases in the UI or human preference in the UX, their designs are spectacular. Let me know the next time your problem space fits those dimensions.

Here, Negro Leagues statistics are partial were often kept by hand, and are subject to vastly different interpretive lenses. A century of NFL data was recorded differently in every era, and the detailed play-level data only exists for recent seasons. The baseball league exists only in its own game exports, while the model shows up already "knowing" the real players. Job postings arrive from a dozen channels, plenty are missing key facts, and most importantly, your application is swimming upstream against the ATS.

So most of the design work is deciding what you can defensibly conclude from what's actually there, and making the gaps visible.

**Which is why a human stays in the middle.** The tools propose, draft, check and flag. I decide. The job search pipeline never submits anything, the listening recaps land in WordPress as drafts, and the football sim's coaching AI has to be able to make recommendations to a human player as well as make the calls itself. When the information is incomplete, a guardrail with a person behind it is worth more than a confident automated answer.

---

## Active projects

### WFL Sim *(private)*

A cross-era American football simulation engine. Every player is rated for a single season, so a 1969 linebacker and a 2020 wide receiver can line up in the same game. The question underneath everything is whether they produce football that feels real when they do.

That's really three problems stacked on top of each other:

- **Measurement.** Ratings have to come from evidence that exists in every era, 1920 through 2025. An otherwise-good model can die simply because it leans on a stat that only exists from 1999 on.
- **Modeling.** Deciding what the engine has to simulate and what can be a stand-in, judged by one question: does it change the outcomes?
- **Validation.** With dice and thousands of plays, a wrong result looks just as plausible as a right one. Every check has to say what it measured, and how big an effect it could actually have caught.

It's also the biggest codebase here, built across more than a hundred Claude sessions, so it's where the no-memory problem gets tested hardest. Decisions get written up as decision records before the code, each in-progress branch carries its own record of where things stand, and the only thing I type to start a session is "orient." This project has also had the most maturation, from a more casual approach in the beginning to, pretty quickly, formal test suites and an ADR driven process.

**Stack:** Python · Flask · SQLite · SQLAlchemy · pandas · SciPy · HTMX · Alpine.js

---

### WBL: The Whirled Baseball League *(private)*

A fictional league stocked with players from across baseball history, simulated in Out of the Park Baseball and now in its third season, with an LLM as my co-commissioner and a weekly publication on top.

The league is a closed world. Every fact has to come from the game's own exports, and nothing outside it can settle an argument. But the model shows up already knowing who Roberto Clemente actually was and his year-by-year record for the Pirates, and that knowledge leaks in, mostly through names.

Worse, in prose a made-up fact reads exactly like a checked one. In code, a wrong answer breaks when it runs. Here, nothing breaks, other than the belief of a close reader.

So the fixes have to be structural. Facts sit behind tools, so "how many wins does he have" is answered by a query. Nothing gets claimed ahead of the query that supports it, and any recommendation that real-world knowledge influenced has to say so. On the memory side, there's one thin, always-loaded file of guardrails for the mistakes that keep recurring; everything else is fetched when it's needed, and every correction gets rewritten as a rule going forward.

It doesn't fully work, and the league keeps a record of that too. Some corrections come back after they've been written down, and the model will still bend its reasoning toward the answer it wants (or toward my pushback). This is the most useful project in terms of the AI-as-Advisor push that you see at times. The AI is a puppy dog, intent on responding to the smallest cues of what you want it to say, and those errors compound hard over time, requiring strict scaffolding behind it all. But that scaffolding gets in the way of the collaborative, co-working feel you're pursuing. So.

**Stack:** Out of the Park Baseball 27 · Python · pandas · WordPress REST API · about 300,000 words of Markdown canon

---

### [career-ops-dml](https://github.com/mknnmknn/career-ops-dml) *(public)*

This started as a fork of [career-ops](https://github.com/santifer/career-ops), an AI job search pipeline built on Claude Code, and all credit for the original is santifer's. I've run it as my actual job search every week since April 2026, which has meant a lot of divergence: more than 3,000 postings tracked and 2,000 evaluated so far.

The core problem is applying my judgment at weekly volume without giving up any of the decisions. Several of the tools have no write path at all, on purpose, so a confidently wrong verdict can't turn into a confidently wrong action. A posting only gets closed on positive evidence from its own text; a failed fetch or an empty page comes to me for a look. And everything it writes on my behalf (CVs, cover letters, form answers) can only draw on facts from my own source files.

The other problem is that upstream ships constantly. Two upgrades in 11 days this fall pulled in nearly 700 upstream commits, and both times the updater quietly overwrote some of my changes. So every divergence is a numbered patch with a keep, merge or retire call at each upgrade, and the automated gate blocks only on damage (a lost row, a broken link). Everything else that changed goes to a ledger I read.

But the end state--the ability of the LLM to construct custom output (in this case, CVs) from a large suite of known, validated, approved facts--is pretty impressive, I think. It speaks to the ability of these systems to serve excellently in document creation, grant response, audit response, anything where the bulk of the text is drawn from a central, honest content repository.

**Stack:** Node.js · Playwright · YAML · Markdown and TSV as the system of record

---

### [i9s](https://github.com/mknnmknn/i9s) *(public)*

Documentation and tooling for [i9s.org](https://www.i9s.org), a historical projection project: what Negro Leagues players' careers might have looked like in the majors. Built on WordPress, with the data served by Pods.

The technical problem is making a content management system act like a stats database, on top of a record that's incomplete and kept by hand. I stayed on the platform and extended it where it allows: a custom plugin, shortcodes that build the stats tables and career totals, SQL straight against the Pods tables, and an admin suite for imports and data quality.

There were things I wanted to do for years, ranging from career totals to administrative tooling for data import and quality control, that were always full of a little too much friction to implement. This is a strong example of how LLMs can be used to eliminate that surrounding friction, allowing me to focus solely on the desired features.

That changes the scope, too. The goal is a few thousand players, and data entry was always the bottleneck, so the import tool was built to take a player's entry from 15-20 minutes down to under a minute.

**Stack:** WordPress · Pods · PHP · MySQL · jQuery

---

### Alemi Spells *(private)*

A members-only web application for managing and printing D&D 5e spell cards. About 2,200 spells imported from structured source documents, stored in SQLite, and rendered as print-ready PDF card sheets. Includes a fairly complex search interface, and a user management component.

**Interesting problems:** Import process from repetitively structured Word documents; text overflow detection and automatic multi-card splitting with related dynamic formatting; a named-rule auto-formatter for spell description markup; Playwright-driven PDF generation; a search interface covering multi-field, multi-variant queries, with a UX design suitable for real humans with relatively low tolerance for technical friction.

Publicly hosted via DigitalOcean, which has also required a lifelong Windows nerd to delve back into the arcane reaches of Linux, which is good for me.

This is the most _complete_ project: from vision through prototypes all the way through public usage. Mostly done intentionally via Claude Chat, as I wanted to be able to both modify and examine all of the code, from Python files through HTML and CSS, as a learning process, and to shake off whatever development rust I was feeling.

I plan to release this publicly with a db seeded with the public domain spells for 5e.

**Stack:** Python · Flask · SQLite · Playwright · Jinja2 · vanilla JS

---

### [mediamonkey-wrench](https://github.com/mknnmknn/mediamonkey-wrench) *(public)*

Tools around [MediaMonkey 5](https://www.mediamonkey.com/) and my listening data. The main one, `listen-here`, drafts monthly listening-recap posts for the WordPress site at [mankinlevine.com](https://mankinlevine.com).

Small, but it runs on the same ideas. My listening lives in two incomplete records, desktop plays in MediaMonkey and phone plays in Last.fm, and the tool merges them into one view without ever writing to my library. It leaves my library's naming conventions alone, even when they break a lookup. And it only ever creates drafts; I publish.

**Stack:** Python · SQLite · FastAPI · WordPress REST API

---
[LinkedIn](https://www.linkedin.com/in/daniel-m-levine/) | [LinkedIn Articles](https://www.linkedin.com/in/daniel-m-levine/recent-activity/all/)

[Personal Blog](https://mankinlevine.com/)

---

*Private repos are not open for contributions or licensing at this time.*
