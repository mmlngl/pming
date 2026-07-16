# /pm:mid-sprint-check

**Run Wednesday ritual: analyze burndown, decide re-scope.**

## What it does
Pulls burndown data, compares actual vs. ideal, identifies stuck stories, calculates if team will hit sprint goal. Recommends: pull stories, push to next sprint, or stay course?

## Usage
```
/pm:mid-sprint-check
```

## What you get back
- Burndown analysis: pace vs. goal
- Stuck stories (2+ days in same state)
- Velocity forecast: will we make goal?
- Re-scope recommendation: pull N stories?
- Stakeholder message: what to say

## When to use
- **Wed morning (Day 3):** Your scheduled checkpoint
- **If pace feels slow:** "Are we actually behind?"
- **Before scope changes:** Data to justify

## Requirements
- Current sprint with burndown chart
- Stories have clear state transitions
- Blockers logged in comments

## Example
```
/pm:mid-sprint-check

Mid-Sprint Analysis (Sprint 12, Day 3 of 10):
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Ideal Pace: 7/10 stories done
Actual:     5/10 stories done
Status:     ⚠️  SLIGHTLY BEHIND (expected 10% variance)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Stuck Stories: 1 (auth, 3 days in "In Progress")
Forecast: 8/10 by Friday (miss by 2)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
RECOMMENDATION:
→ Pull 2 low-priority stories to Sprint 13
→ Escalate auth blocker (needs decision)
→ New forecast: 8/8 ✅

Message to stakeholders:
"Sprint 12 tracking 80% of goal. One blocker (auth). 
Pulling 2 stories to Sprint 13 to maintain quality. 
New forecast: 8 stories by Friday."
```
