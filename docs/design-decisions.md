# SYSTEM — Design Decisions

This document captures the product and interaction decisions that currently shape SYSTEM.

The goal is not to present every implementation detail. It is to explain why the product behaves the way it does and what was learned from using it.

---

## 1. Fixed daily routine

**DECISION**  
Use a fixed routine of eight daily work and recovery blocks.

**WHY**  
SYSTEM was created around a repeatable personal schedule. The primary problem was execution, not planning from scratch every morning.

**RESULT**  
The Today view always presents the same ordered structure from 07:00 to 18:00. Each block has a time range, title, status, XP reward, and direct actions.

**LEARNING**  
Constraints can reduce decision fatigue. A fixed routine is useful when the challenge is following a known plan rather than continuously reorganizing one.

---

## 2. Done / Missed instead of complex task states

**DECISION**  
Keep routine-state tracking to pending, done, or missed.

**WHY**  
The daily question is intentionally simple: was the block completed or not?

**RESULT**  
Each block can be marked Done or Missed. Done grants XP; Missed does not.

**LEARNING**  
A smaller state model is faster to use and easier to translate into meaningful completion metrics.

---

## 3. Connect focus sessions to routine blocks

**DECISION**  
Let a Pomodoro session reference a planned routine block.

**WHY**  
A standalone timer can tell you how long you focused, but not what part of the day that focus advanced.

**RESULT**  
Users can enter Focus from a routine block or choose Free Focus. Completed sessions later appear in task/domain analytics and history.

**LEARNING**  
Focus becomes more useful when it has context. Tracking time and tracking intent should not be completely separate systems.

---

## 4. Persist an expected completion timestamp

**DECISION**  
Use an expected completion time as the timer source of truth instead of relying only on a foreground browser countdown.

**WHY**  
Browser timers can become visually stale when tabs are backgrounded, minimized, or restored.

**RESULT**  
SYSTEM recalculates remaining time from the current clock and refreshes state when the page regains focus or visibility.

**LEARNING**  
For time-sensitive interactions, the deadline is more reliable than the display counter.

---

## 5. Persist progress server-side

**DECISION**  
Store routine activity, focus sessions, XP, timer state, and preferences in persistent storage.

**WHY**  
A productivity system loses trust immediately if a refresh or browser restart wipes meaningful progress.

**RESULT**  
The current prototype restores saved routine and focus data instead of behaving like a temporary demo.

**LEARNING**  
Persistence is not a secondary technical feature when the product itself is about continuity and progress.

---

## 6. Lightweight XP and levels

**DECISION**  
Use 10 XP for completed routine blocks and focus cycles, with level progression based on total XP.

**WHY**  
The interface needed visible feedback for consistency without requiring a large analytics system.

**RESULT**  
SYSTEM surfaces total XP, XP earned today, current level, and progress toward the next level.

**LEARNING**  
Gamification can stay small. A simple, transparent feedback loop can be enough to make progress feel visible.

---

## 7. Fullscreen focus mode

**DECISION**  
Provide a reduced-distraction fullscreen state for active focus sessions.

**WHY**  
The dashboard is useful before and after focused work, but it can become unnecessary visual noise during a session.

**RESULT**  
Fullscreen Focus Mode reduces the interface to the timer, current task, session information, and essential controls.

**LEARNING**  
A product does not need to be minimal everywhere. It can become minimal exactly when the workflow requires it.

---

## 8. Summary-first progress

**DECISION**  
Keep the Progress section concise instead of immediately building a large analytics dashboard.

**WHY**  
The first product need was execution and consistency, not data exploration.

**RESULT**  
Progress currently surfaces weekly completion, focus streak, total XP, and current level.

**LEARNING**  
Historical analytics should earn their complexity. Early prototypes benefit from showing only the signals that support an actual review behavior.

---

## 9. Mission-control visual language

**DECISION**  
Use a dark technical interface with mission-control language instead of a conventional to-do-list aesthetic.

**WHY**  
SYSTEM is intended to feel like an execution environment for study and technical work.

**RESULT**  
The product uses dark navy/near-black surfaces, cyan accents, technical labels, thin borders, circular timer geometry, XP/status indicators, and monospaced details.

**LEARNING**  
Visual language can reinforce behavior. The interface feels more like an operating console than an administrative list, which supports the product’s execution-first identity.

---

## 10. Keep the prototype personal and constrained

**DECISION**  
Do not prematurely turn SYSTEM into a broad multi-user productivity platform.

**WHY**  
The project exists because of one real personal workflow problem. Expanding the scope too early would make it harder to understand whether the original system actually works.

**RESULT**  
The current implementation remains single-user/shared-state, uses a fixed routine, and avoids generalized task-management features.

**LEARNING**  
A narrow product used every day can teach more than a broad product designed around hypothetical users.
