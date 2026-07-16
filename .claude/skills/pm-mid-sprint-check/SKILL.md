---
name: pm-mid-sprint-check
description: Runs the mid-sprint ritual by analyzing burndown, identifying stuck stories, forecasting completion, and recommending re-scope decisions. Use Wednesday morning (Day 3) of sprint to see if team will hit goal or need to adjust scope.
---

## Mid-Sprint Check (Day 3 Ritual)

Wednesday morning: pull data, forecast, decide on re-scope.

### Workflow

1. **Fetch sprint stories** via `mcp__shortcut__iterations-get-stories`
2. **Analyze pace:**
   - Ideal: total_stories / 10 days * 3 days = expected stories done by Wed
   - Actual: count stories in "Done" state
   - Variance: (actual - ideal) / ideal * 100
   - Status: ON TRACK if variance >= -10%, AT RISK if -10% to -25%, BEHIND if < -25%

3. **Identify stuck stories:**
   - Any story 2+ days in same state
   - Extract from story "updated_at" timestamps
   - Flag by name + state + duration

4. **Forecast completion:**
   - Velocity so far = actual / 3 days
   - Projected velocity if sustained = velocity * 7 remaining days
   - Forecast = actual + projected
   - Completion gap = total - forecast

5. **Recommend re-scope:**
   - If forecast < total by 2+: pull lowest-priority N stories to Sprint N+1
   - Calculate new forecast with pulled stories
   - Show stakeholder message with confidence level

### Output format

```
Mid-Sprint Analysis (Sprint [N], Day 3 of 10):
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Ideal Pace: [ideal]/[total] stories
Actual:     [actual]/[total] stories
Variance:   [%] — [ON TRACK / AT RISK / BEHIND]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Stuck Stories: [count]
  - [story name] ([days] days in [state])

Velocity: [actual/3] stories/day
Forecast by Friday: [forecast]/[total] (gap: [N] stories)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
RECOMMENDATION:
→ [Action: pull / escalate / stay course]
→ [New forecast if pulling stories]

Message to stakeholders:
"Sprint [N] tracking [%] of goal. [X] blocker(s). 
[Action taken]. New forecast: [N] stories by Friday."
```

### Implementation notes

- "Stuck" = same state since before yesterday's standup
- Use story history or updated_at to calculate days in state
- For forecast, assume current velocity continues (no acceleration)
- Round forecast down (conservative estimate)
- Escalate blockers immediately via Slack
