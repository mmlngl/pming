# /pm:pipeline-audit

**Full health check of all three sprints (N | N+1 | N+2) at once.**

## What it does
Scans Shortcut for all three concurrent sprints. Shows phase, completion, blockers, risks. Answers: "Is my entire pipeline healthy?"

## Usage
```
/pm:pipeline-audit
```

## What you get back
- **Sprint N (Execute):** Burndown %, blockers, QA rate
- **Sprint N+1 (Plan):** Backlog %, design %, ready date
- **Sprint N+2 (Spec):** Spec status, backlog draft %, design start date
- **Risks:** Which phase is lagging? What to fix?

## When to use
- **End of week:** Full pipeline health snapshot
- **If you feel behind:** Pinpoint where
- **Before stakeholder call:** Data to share

## Requirements
- Three sprints active in Shortcut
- Stories tagged with sprint N, N+1, N+2
- Backlog states consistent (Ready, In Progress, In QA, Done)

## Example
```
/pm:pipeline-audit

Pipeline Health (Sprints 12 | 13 | 14):
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Sprint 12 (EXECUTE)    | 60% done | 1 blocker | QA: 12% ⚠️
Sprint 13 (READY)      | 100% backlog ✅ | Designs ✅ | Kick off Mon
Sprint 14 (PLAN)       | AC: 50% | Design: 20% | On track
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
⚠️  Sprint 12 QA spiking — review AC clarity
✅ Sprint 13 ready
✅ Sprint 14 pacing well
```
