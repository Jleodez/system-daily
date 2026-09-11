# SYSTEM — Product Overview

## Problem

Daily planning, focus, and progress tracking often live in separate tools.

A calendar or schedule can show what should happen. A Pomodoro timer can protect concentration. A to-do list can record completion. But those tools do not automatically answer a simple question:

**Did the focused work I just completed actually move today's plan forward?**

SYSTEM was built to connect those pieces into one execution loop:

**PLAN → FOCUS → COMPLETE → REVIEW**

## Context

The project started as a personal response to a real workflow problem.

The user was balancing cybersecurity study, technical learning, programming, personal projects, and creative work. The schedule itself was already structured; the challenge was following it consistently and seeing meaningful progress without switching between several disconnected tools.

SYSTEM therefore focuses on execution rather than broad task management.

## User

The current prototype is designed for one personal user with a repeatable daily routine.

It is most useful when the main problem is not “what should I do?” but rather:

- what block should I be in right now?
- can I stay focused long enough to complete it?
- did I actually complete what I planned?
- how much focused work did I finish today?

## Core workflow

1. **Review the day** — open Today and see the eight fixed work/recovery blocks.
2. **Start execution** — choose a block and enter Focus, or use Free Focus.
3. **Run a session** — use a preset or custom focus/break duration.
4. **Record outcome** — mark blocks Done or Missed and complete focus cycles.
5. **Review progress** — see completion, focused minutes, streak, XP, level, and session history.

## Current functionality

### Today

The Today view contains the fixed routine and daily execution summary.

Current elements include:

- eight predefined work and recovery blocks
- time range and block title
- pending, done, or missed state
- 10 XP reward for completed routine blocks
- direct Focus, Done, and Missed controls
- completed-block count
- daily completion percentage and progress bar
- XP earned today
- focus status summary and daily goal progress

### Focus

The Focus view is the active work surface.

Current functionality includes:

- routine-linked sessions or Free Focus
- Focus, Short Break, and Long Break phases
- 25/5 and 50/10 presets
- custom focus, short-break, and long-break durations
- Start, Pause, Resume, Restart, Skip, and Exit/Cancel
- long break after four completed focus cycles
- completion sound
- adjustable sound volume and test control
- optional browser notifications
- auto-start next phase
- fullscreen focus mode
- daily focus analytics
- focused minutes and completed Pomodoros
- current streak
- planned-study percentage
- task and inferred-domain breakdowns
- session history with deletion

### Progress

The Progress view currently keeps review intentionally lightweight.

It shows:

- weekly completion across the latest seven calendar days
- focus streak
- total XP
- current level

## Focus integration

The timer is not treated as an isolated utility.

A focus session can reference a routine block, so the work being timed has context. Completed sessions then feed the broader SYSTEM feedback loop through focused minutes, completed Pomodoros, task/domain breakdowns, streak, XP, level progression, and history.

This connection between **planned work** and **focused work** is the central product decision in the current prototype.

## Timer behavior

The timer stores an expected completion timestamp and derives remaining time from the current clock.

This allows the interface to recover more reliably after browser behaviors such as:

- losing tab focus
- minimizing the browser
- switching tabs
- restoring the page
- returning to a previously hidden tab

The UI refreshes timer state when the page regains focus or visibility instead of trusting only a foreground browser interval.

## Persistence

The current prototype persists routine activity, XP, timer state, focus preferences, and focus-session history server-side.

Confirmed implementation elements from the current project review include:

- React + TypeScript frontend
- Vinext application framework
- API routes for activity and focus state
- Cloudflare D1 / SQLite persistence
- Drizzle ORM schema and migrations

## Current status

**STATUS / ACTIVE PERSONAL PROTOTYPE**

SYSTEM is functional and used as an execution tool rather than being presented as a finished commercial product.

It is currently single-user/shared-state and intentionally constrained around one fixed routine.

## Known limitations

The current implementation does not expose:

- editing of routine titles, times, order, or block count
- general task creation beyond Free Focus
- detailed historical charts or calendar heatmaps
- notes attached to blocks or sessions
- multi-user accounts or user-specific data separation
- calendar or external productivity integrations

Browser sound and notification behavior also depends on browser permissions and capabilities.

## Future directions

Possible future improvements include:

- editable routine structure
- richer history and review views
- optional notes and reflections
- flexible task creation
- multi-user profiles
- calendar or external-tool integrations

These are future directions only and are intentionally separated from the current feature set.
