---
name: pm-daily-standup
description: Generates today's PM tasks for all three concurrent sprints (N|N+1|N+2) with time estimates and checklists. Use each morning to see what to work on today, or after meetings to find your place in the sprint cycle.
---

## Daily PM Standup

Every morning: identify today's sprint day, generate prioritized task list for N | N+1 | N+2.

### Workflow

1. **Determine sprint cycle:**
   - Get active sprint number (N) from Shortcut
   - Calculate: what day of 10? (Mon=1, Tue=2, ... Fri=5, then Mon=6, etc.)
   - Week number (1 or 2 of sprint)

2. **Map day to task focus:**
   - **Day 1 (Mon Week 1):** Kickoff. Focus: N starts, N+1 backlog review, N+2 spec brief
   - **Day 2-4 (Tue-Thu):** Execution. Focus: N burndown monitor, N+1 grooming, N+2 spec/design
   - **Day 3 (Wed):** Mid-sprint. Focus: N burndown analysis + re-scope decision
   - **Day 5 (Fri Week 1):** Sprint close. Focus: N acceptance + closure, N+1 final readiness, N+2 queue
   - **Day 6+ (Week 2):** Same as Week 1, repeat

3. **Generate task list per sprint:**
   - **N tasks:** monitor burndown, accept stories, escalate blockers (varies by day)
   - **N+1 tasks:** finalize backlog, review designs, estimate unclear items (varies by day)
   - **N+2 tasks:** spec features, draft stories, brief designer (varies by day)

4. **Add time estimates** (use from SPRINT_AGENDA.md calendar)

5. **Generate end-of-day checklist** (sub-items from task list)

### Output format

```
TODAY: [Day Name], Sprint [N], Day [X] of 10 (Week [1/2])
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

SPRINT N ([Phase]) — [time] min
[ ] [Task 1]
[ ] [Task 2]
[ ] [Task 3]

SPRINT N+1 ([Phase]) — [time] min
[ ] [Task 1]
[ ] [Task 2]

SPRINT N+2 ([Phase]) — [time] min
[ ] [Task 1]
[ ] [Task 2]

TOTAL TIME: ~[X] min
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
END OF DAY CHECK:
[ ] N: [milestone 1] + [milestone 2]
[ ] N+1: [milestone 1] + [milestone 2]
[ ] N+2: [milestone 1]
```

### Implementation notes

- Look up day from "today" or accept user-specified date
- Use SPRINT_AGENDA.md daily tasks as reference (already broken down by day)
- Time estimates: ~45 min total per day (15 per sprint)
- Copy checklist to Slack + task manager
- End-of-day check verifies sprint health: all phases progressing?
