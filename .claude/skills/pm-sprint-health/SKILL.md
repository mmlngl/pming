---
name: pm-sprint-health
description: Audits current sprint health by analyzing burndown, blockers, QA rejection rate, and support burden. Use when checking sprint progress, during mid-sprint checkpoints, or to identify re-scope decisions.
---

## What it does
Checks Sprint N burndown, identifies blockers, calculates QA rejection rate, flags velocity concerns. Answers: "Am I on track?"

## Usage
```
/pm:sprint-health
```

## What you get back
- Burndown status (actual vs. ideal)
- # stories completed vs. forecasted
- Blockers (stuck 2+ days)
- QA rejection rate
- Support/interrupt burden
- Red flags (velocity dropping, QA spiking, design delayed)

## When to use
- **Wed morning (Day 3):** Mid-sprint checkpoint
- **Any day:** "Wait, are we behind?"
- **Before re-scoping:** Data to decide what to pull

## Requirements
- Shortcut project set up + burndown chart visible
- Stories linked to sprint N
- QA verdicts recorded in story comments

## Example
```
/pm:sprint-health

Sprint 12 Health Check:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Burndown: 6/10 stories done (60%) — ON TRACK
Ideal:    7/10 (70%)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Blockers: 1 (auth story stuck 3 days — escalate)
QA Rejection Rate: 12% (OK, target <15%)
Support Burden: 22% (expected 20%)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
⚠️  One story needs attention. Re-scope decision: pull low-priority story?
```
