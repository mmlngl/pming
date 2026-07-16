# PM Skills for Sprint Management

Claude Code skills to manage the three-sprint pipeline (N | N+1 | N+2).

## Skills Included

- **`/pm:sprint-health`** — Is Sprint N on track? (burndown, blockers, QA rate)
- **`/pm:next-sprint-ready`** — Is Sprint N+1 ready to kick off? (backlog ✅, designs ✅, capacity ✅)
- **`/pm:pipeline-audit`** — Full health check (all three sprints at once)
- **`/pm:mid-sprint-check`** — Wednesday ritual (burndown analysis + re-scope decision)
- **`/pm:daily-standup`** — What's my PM task today? (with checklist + time)

## Installation

### Option 1: Local Skills (This Repo)

Skills live in `.claude/skills/`. Use them from this directory only.

```bash
cd /Users/mmgl0/Documents/pming
claude /pm:sprint-health
```

### Option 2: Global Skills (Use Anywhere)

Link skills to your global Claude Code directory:

```bash
# 1. Find your global Claude Code directory
ls ~/.claude/skills/

# 2. Link this repo's skills to global
ln -s /Users/mmgl0/Documents/pming/.claude/skills/* ~/.claude/skills/

# 3. Now use skills from anywhere
/pm:sprint-health
```

Or add to `.claude/config.yml`:

```yaml
skills:
  - path: /Users/mmgl0/Documents/pming/.claude/skills
```

## Usage

### Daily Workflow

```bash
# Morning: What's my task today?
/pm:daily-standup

# Mid-week (Wed): Am I on track?
/pm:mid-sprint-check

# End of week: Full pipeline health?
/pm:pipeline-audit

# Thursday: Is next sprint ready?
/pm:next-sprint-ready

# Anytime: Current sprint status?
/pm:sprint-health
```

## Requirements

- Shortcut project set up + burndown chart visible
- Stories linked to sprint N, N+1, N+2
- Consistent story states (Ready, In Progress, In QA, Done)
- QA verdicts recorded in story comments
- Team capacity logged (availability)

## Publishing to GitHub

```bash
cd /Users/mmgl0/Documents/pming
git add .
git commit -m "Initial: PM sprint management skills"
git remote add origin https://github.com/YOUR_USERNAME/pming-skills.git
git push -u origin main
```

## Contributing

Update skills as your process evolves. Skills live in `.claude/skills/` as `.md` files.

---

*Last updated: 2026-07-16*
