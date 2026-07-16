# /pm:next-sprint-ready

**Verify Sprint N+1 is ready to kick off Monday.**

## What it does
Checks if backlog is 100% finalized, all designs linked, team capacity booked, dependencies resolved. Answers: "Can we start Monday?"

## Usage
```
/pm:next-sprint-ready
```

## What you get back
- Backlog completion: # of stories in "Ready" state
- Design status: all mocks linked? approved?
- Team capacity: anyone out Monday?
- Dependencies: any stories blocked by Sprint N?
- Handoff readiness: design team signed off?

## When to use
- **Thu afternoon (Day 4):** Before declaring N+1 ready
- **Fri morning:** Final confirmation before weekend
- **If kickoff delayed:** "What's still missing?"

## Requirements
- Sprint N+1 stories in Shortcut
- All AC written + estimated
- Design mocks in Figma, linked to stories
- Capacity plan logged (team availability)

## Example
```
/pm:next-sprint-ready

Sprint 13 Readiness Check:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Backlog: 10/10 stories in "Ready" ✅
Design: 10/10 mocks finalized + linked ✅
Capacity: 2 devs available Mon ✅
Dependencies: 0 blockers ✅
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
✅ READY TO KICK OFF MONDAY
```
