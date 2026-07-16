# Setup Guide: Adding PM Skills Globally

## Step 1: Clone/Navigate to Repo

```bash
cd /Users/mmgl0/Documents/pming
```

## Step 2: Link Skills Globally (One-Time Setup)

### Find your global Claude Code directory:

```bash
ls ~/.claude/
```

Should show: `settings.json`, `skills/`, etc.

### Link this repo's skills to global:

```bash
ln -s /Users/mmgl0/Documents/pming/.claude/skills/* ~/.claude/skills/
```

Verify:
```bash
ls ~/.claude/skills/
```

Should now include: `pm-sprint-health.md`, `pm-next-sprint-ready.md`, etc.

## Step 3: Test Skills (From Any Directory)

```bash
cd ~
/pm:daily-standup
```

Should work from anywhere now.

## Step 4: Publish to GitHub (Optional)

```bash
cd /Users/mmgl0/Documents/pming

# Initialize remote
git remote add origin https://github.com/YOUR_USERNAME/pming-skills.git

# Push
git add .
git commit -m "Initial: PM sprint management skills"
git push -u origin main
```

## Troubleshooting

**Skills not found when running `/pm:sprint-health`?**
- Check symlink: `ls -la ~/.claude/skills/ | grep pm-`
- If link broken: re-run Step 2
- Restart Claude Code if already open

**"Permission denied" on symlink?**
- Run with sudo: `sudo ln -s /Users/mmgl0/Documents/pming/.claude/skills/* ~/.claude/skills/`

**Want to uninstall?**
```bash
rm ~/.claude/skills/pm-*.md
```

---

*Ready to use. Skills are global now.*
