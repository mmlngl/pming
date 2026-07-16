# /pm:daily-standup

**Generate today's PM tasks from the sprint calendar.**

## What it does
Tells you: what day is it? What should you do today for N | N+1 | N+2? With time estimates + checklist.

## Usage
```
/pm:daily-standup
```

Optionally with date:
```
/pm:daily-standup Wed Week 1
```

## What you get back
- Today's date + sprint day (e.g., "Wed, Day 3 of 10")
- Tasks for Sprint N (execute): what to monitor
- Tasks for Sprint N+1 (plan): what to finalize
- Tasks for Sprint N+2 (spec): what to refine
- Time estimates: how long each takes
- Checklist: copy-paste into Slack or notes

## When to use
- **Every morning:** "What's my day?"
- **After meetings:** "Where was I in the plan?"
- **End of day:** "Did I do everything?"

## Requirements
- Know your current sprint number
- Know what day of the 10-day cycle you're on

## Example
```
/pm:daily-standup Wed Week 1

TODAY: Wednesday, Sprint 12, Day 3 (Mid-Sprint)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

SPRINT N (Execute) — 15 min
[ ] CRITICAL: Burndown analysis (actual vs. ideal?)
[ ] Identify stuck stories (flag in Slack)
[ ] Re-scope decision: pull stories if needed?
[ ] Update stakeholders: forecast

SPRINT N+1 (Backlog + Design) — 15 min
[ ] Design check: AC refined? On track for finalization?
[ ] Groom remaining stories
[ ] Estimate unclear stories

SPRINT N+2 (Spec + Plan) — 15 min
[ ] AC final pass (edge cases?)
[ ] Designer briefing: scope locked?
[ ] Confirm design start date

TOTAL TIME: ~45 min
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
END OF DAY CHECK:
[ ] N burndown analyzed + stakeholders updated
[ ] N+1 AC refined, grooming complete
[ ] N+2 ready for design brief
```
