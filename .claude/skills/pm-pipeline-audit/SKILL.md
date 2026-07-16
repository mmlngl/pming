---
name: pm-pipeline-audit
description: Provides full health check of all three concurrent sprints at once, showing phase, completion, blockers, and risks. Use end-of-week to see full pipeline health or when you feel behind to pinpoint where things broke.
---

## Full Pipeline Audit

End-of-week or anytime: snapshot health of all 3 concurrent sprints (N | N+1 | N+2).

### Workflow

1. **Identify sprint numbers** for N, N+1, N+2 (most recent active + next two)

2. **For Sprint N (EXECUTE):**
   - Fetch all stories
   - Calculate: % done, blockers, QA rejection rate (see pm-sprint-health for methodology)
   - Status: ON TRACK / AT RISK / BEHIND

3. **For Sprint N+1 (READY):**
   - Fetch all stories
   - Calculate: % in "Ready" state, % with designs linked, dependencies
   - Status: READY / NEEDS WORK

4. **For Sprint N+2 (PLAN):**
   - Fetch all stories
   - Calculate: % with AC written, % with estimates, design start date
   - Status: ON TRACK / BEHIND SCHEDULE

5. **Identify risks across all three:**
   - Which sprint is lagging?
   - Any cross-sprint blockers?
   - Design bottleneck?
   - Capacity risk?

### Output format

```
Pipeline Health (Sprints [N] | [N+1] | [N+2]):
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Sprint [N] (EXECUTE)     | [%] done | [X] blockers | QA: [%] [status]
Sprint [N+1] (READY)     | Backlog [%] ✅ | Design [%] ✅ | [ready/blocked]
Sprint [N+2] (PLAN)      | AC [%] | Design [%] | [on track/behind]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[Risk summary]
- [Sprint N issue if any]
- [Sprint N+1 issue if any]
- [Sprint N+2 issue if any]
```

### Implementation notes

- Use same methodologies as individual skills (pm-sprint-health, pm-next-sprint-ready, etc.)
- Report only ONE headline metric per sprint (burndown for N, readiness for N+1, planning for N+2)
- Flag if any sprint is red
- 3-sprint view shows bottlenecks: if N+1 not ready but N+2 planning on time, design is likely bottleneck
