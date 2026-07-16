---
name: pm-sprint-health
description: Audits current sprint health by analyzing burndown, blockers, QA rejection rate, and support burden. Use when checking sprint progress, during mid-sprint checkpoints, or to identify re-scope decisions.
---

## Sprint Health Audit

Use Shortcut MCP to fetch and analyze current sprint (N) health.

### Workflow

1. **Get sprint number** from user context or most recent active sprint
2. **Fetch all stories** in sprint using `mcp__shortcut__iterations-get-stories`
3. **Calculate metrics:**
   - Total stories forecasted
   - Stories completed (in "Done" state)
   - Burndown % = completed / total
   - Blockers = stories stuck 2+ days in same state (check story comments for timestamps)
   - QA rejection rate = stories bounced from "In QA" back to "In Progress" / total attempted
   - Support burden = time spent on unplanned work this sprint (from story comments or custom field)

4. **Compare to ideal:**
   - Ideal pace = total_stories / sprint_days * days_elapsed
   - Actual = completed
   - On track if actual >= ideal - 10%

5. **Flag risks:**
   - Velocity dropping (actual < ideal - 15%)
   - QA rate > 15% (quality issue)
   - Support > 25% (capacity drain)
   - Blocked stories (escalate immediately)

### Output format

```
Sprint [N] Health Check (Day [X] of 10):
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Burndown: [completed]/[total] stories ([%]) — [ON TRACK / AT RISK / BEHIND]
Ideal:    [ideal_count]/[total] (expected pace)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Blockers: [count] ([story names])
QA Rejection Rate: [%] (target <15%)
Support Burden: [%] (expected <20%)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[Red flags or action items]
```

### Implementation notes

- Use `mcp__shortcut__iterations-get-stories` with `full: true` to get AC + comments
- Parse story comments for blocker timestamps and support work notes
- Map workflow states to phases: "Backlog" = 0%, "To Do" = 0%, "In Progress" = 50%, "In QA" = 75%, "Done" = 100%
- For multi-day metrics, look at story "updated_at" field to determine how long in current state
