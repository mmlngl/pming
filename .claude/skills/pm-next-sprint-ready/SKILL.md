---
name: pm-next-sprint-ready
description: Verifies that the next sprint is ready to kick off by checking backlog completion, design finalization, team capacity, and dependencies. Use on Thursday or Friday before sprint kickoff to ensure Monday launch won't be delayed.
---

## Next Sprint Readiness Check

Thursday afternoon or Friday morning: verify Sprint N+1 is 100% ready to kick off Monday.

### Workflow

1. **Fetch Sprint N+1 stories** via `mcp__shortcut__iterations-get-stories` with full=true
2. **Backlog completion:**
   - Count stories in "Ready" state
   - Count stories with AC written (check description length > 50 chars)
   - Count stories with estimates (check custom field "estimate")
   - All linked to design specs? (search description for Figma link or attachment)
   - Target: 100% ready, 100% estimated

3. **Design status:**
   - Check each story for Figma mock link in description
   - Count mocks in Figma (compare to story count)
   - Target: 100% stories have linked designs

4. **Team capacity:**
   - Check for planned absences (query via custom field or comment)
   - Verify minimum team available Monday
   - Target: all required roles available

5. **Dependencies:**
   - Identify stories blocked by Sprint N (check linked story relationships)
   - Flag any external dependencies
   - Target: zero blockers

6. **Design handoff readiness:**
   - Designer signed off on all specs? (check story comments for approval)
   - All questions answered? (no open design threads)
   - Target: clean handoff

### Output format

```
Sprint [N+1] Readiness Check:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Backlog: [X]/[total] stories in "Ready" ✅
Design: [X]/[total] mocks finalized + linked ✅
Estimates: [X]/[total] stories estimated ✅
Capacity: [X] devs available Mon ✅
Dependencies: [0] blockers ✅
Design handoff: [approved/pending]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[✅ READY TO KICK OFF MONDAY or ⚠️ BLOCKED: [list issues]]
```

### Implementation notes

- "Ready" = backlog state in Shortcut, all AC written, estimated
- Design links: search story description for "figma.com" or "design:" references
- Handoff approval: look for designer comment with "approved" or checkmark
- If missing: flag specific stories, not the sprint
- If all clear: team starts Monday without delays
