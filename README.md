# SYSTEM

**A personal productivity system for focus, routines, and daily progress.**

> **Status:** Active personal prototype  
> **Built with:** ChatGPT Sites · React · TypeScript · Cloudflare D1 / SQLite · Drizzle ORM

[**Open the live prototype →**](https://solo-system-daily.leodez.chatgpt.site)

![SYSTEM daily mission control](screenshots/01-today-overview.jpg)

SYSTEM began with a very ordinary problem: I had a structured day on paper, but I was still losing track of what I should be doing, how long I had actually focused, and whether I had made meaningful progress by the end of the day.

Pomodoro timers helped with concentration, but they lived separately from the routine. Task tools helped with lists, but not with execution. I wanted one simple loop that connected the plan to the work itself:

**PLAN → FOCUS → COMPLETE → REVIEW**

SYSTEM is the tool I built around that workflow.

## Why I built it

I was balancing cybersecurity study, technical learning, programming, personal projects, and creative work. My schedule was organized, but execution was fragmented across different tools.

The recurring problems were simple:

- I could lose track of the work block I was supposed to be in.
- Focus sessions were disconnected from the routine they were meant to support.
- A busy day did not always make it obvious how much planned work I had actually completed.
- Progress was difficult to see without opening multiple apps.

Instead of adding another productivity app to the pile, I built a small system around the way I actually work.

## How it works

SYSTEM uses a fixed daily routine and turns it into an execution loop.

1. **Plan** — Review eight predefined work and recovery blocks for the day.
2. **Focus** — Start a Pomodoro-style session from a routine block or use Free Focus.
3. **Complete** — Mark blocks as Done or Missed and complete focus cycles.
4. **Review** — See completion, focused minutes, streaks, XP, level, and recent sessions.

The goal is not to become a general-purpose task manager. The goal is to reduce friction between knowing what I should do and actually doing it.

## Current product

### Today

The daily execution view shows the scheduled blocks, daily completion, XP earned, focus progress, and direct controls for **Focus**, **Done**, and **Missed**.

![Routine blocks](screenshots/02-daily-routine-blocks.jpg)

### Focus

The working mode includes:

- Focus, short-break, and long-break phases
- 25/5 and 50/10 presets
- Custom focus and break durations
- Start, pause, resume, restart, skip, and cancel controls
- Routine-linked sessions or Free Focus
- Auto-start for the next phase
- Completion sound and adjustable volume
- Optional browser notifications
- Fullscreen focus mode
- Daily focus analytics
- Task and domain breakdowns
- Session history

![Focus mode](screenshots/03-focus-mode.jpg)

### Review

Focus sessions feed back into the same system through focused minutes, Pomodoros completed, streaks, task/domain breakdowns, XP, levels, and session history.

![Focus analytics and history](screenshots/04-focus-analytics.jpg)

### Distraction-free mode

For active work, SYSTEM can reduce the interface to the timer, current task, session context, and essential controls.

![Fullscreen focus mode](screenshots/05-focus-fullscreen.jpg)

## Focus is part of the routine

The timer is intentionally not a standalone feature.

A focus session can be linked directly to a routine block. When the session is completed, it becomes part of the same progress system: focused minutes, completed Pomodoros, task/domain breakdowns, streaks, XP, level progression, and session history.

That connection is the central product idea behind SYSTEM.

## Product decisions

| Decision | Why it exists |
| --- | --- |
| Fixed eight-block routine | Reduces daily planning friction and keeps the system focused on execution. |
| Done / Missed states | Keeps completion tracking binary and fast. |
| Routine-linked Pomodoro | Connects concentration with the work that was actually planned. |
| XP + levels | Makes consistency visible without turning the product into a complex game. |
| Fullscreen focus mode | Removes dashboard noise during active work. |
| Summary-first progress | Keeps the prototype useful before adding heavier analytics. |

More detail: [`docs/design-decisions.md`](docs/design-decisions.md)

## A timer that survives real browser behavior

One of the most useful lessons came from the timer itself.

A simple browser interval can become visually stale when a tab is minimized, backgrounded, or later restored. SYSTEM instead stores an **expected completion timestamp** and derives the remaining time from the clock. The UI refreshes when the page regains focus or visibility.

This turned a small Pomodoro feature into a useful lesson in state, persistence, and browser lifecycle behavior.

## Persistence

The current prototype stores routine activity, XP, timer state, preferences, and focus-session history server-side.

Confirmed implementation elements include:

- React + TypeScript frontend
- Vinext application framework
- API routes for activity and focus state
- Cloudflare D1 / SQLite persistence
- Drizzle ORM schema and migrations

The product remains a **single-user personal prototype**, not a finished multi-user platform.

## What I learned

**Reliable timers need a real source of truth.** A persisted deadline is more robust than trusting a client-side countdown alone.

**Persistence changes how trustworthy a tool feels.** Losing focus history or progress after a refresh would undermine the entire workflow.

**Constraints can be a feature.** A fixed routine is less flexible than a task manager, but that limitation reduces decisions when the real problem is execution.

**Small feedback loops are enough.** Done/Missed states, XP, progress bars, sound, and simple analytics can make progress visible without building an enormous dashboard.

**Using your own product exposes friction quickly.** SYSTEM evolved through day-to-day use rather than as a portfolio exercise designed only to look finished.

## Current status

**STATUS / ACTIVE PROTOTYPE**

SYSTEM is currently a working personal tool with persistent routine tracking, focus sessions, XP, levels, and progress feedback.

It is intentionally still constrained:

- the routine is fixed rather than freely editable
- there is no general task-creation workflow beyond Free Focus
- historical analytics are summary-based rather than chart-heavy
- there is no multi-user account model

These limitations are part of the current product state, not hidden behind roadmap language.

## Future directions

Possible next steps include exposing routine editing, richer historical views, optional notes, flexible tasks, and eventually multi-user or calendar integrations.

Those ideas are documented separately from the current implementation in [`docs/roadmap.md`](docs/roadmap.md).

## What this project represents

SYSTEM is less interesting to me as “another Pomodoro app” than as a small product-development loop:

**REAL PROBLEM → WORKFLOW → PROTOTYPE → DAILY USE → FRICTION → ITERATION**

It reflects the kind of work I enjoy as a Creative Technologist: understanding a system, building something tangible enough to use, finding where it breaks, and improving it through iteration.

**DESIGN → BUILD → TEST → IMPROVE**

---

### Live & documentation

- [**Live prototype**](https://solo-system-daily.leodez.chatgpt.site)
- [`Product overview`](docs/product-overview.md)
- [`Design decisions`](docs/design-decisions.md)
- [`Roadmap`](docs/roadmap.md)

> The current live prototype is built in ChatGPT Sites. This repository documents the product, design decisions, and development process; it does not claim to contain the full source code of the Site.
