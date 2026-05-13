---
title: Skill — Using Git Worktrees
tags: [skill, git, worktrees, isolation]
aliases: [git-worktrees-skill]
---

# Skill: using-git-worktrees

## מה הסקיל עושה

**הקמת workspace מבודד לעבודה** — מבטיח שהעבודה קורית בבידוד. מעדיף כלים מובנים של הפלטפורמה, ונופל ל-git worktree ידני כחלופה.

### עיקרון הליבה

> "זהה בידוד קיים קודם. אחר כך כלים מובנים. אחר כך git. לעולם אל תילחם בharness."

### שלב 0: זהה בידוד קיים

לפני יצירת כלום — בדוק אם כבר בworktree:
```bash
GIT_DIR=$(git rev-parse --git-dir)
GIT_COMMON=$(git rev-parse --git-common-dir)
```
אם שונים ואין superproject → כבר מבודד.

### שלב 1: כלים מובנים

כשיש Agent tool עם `isolation: "worktree"` — השתמש בו.

### שלב 2: git worktree ידני

```bash
git worktree add ../feature-branch feature-branch
```

## מתי להפעיל

לפני:
- עבודה על פיצ'ר שצריך בידוד מה-workspace הנוכחי
- ביצוע implementation plans

## נתיב

```
.claude/skills/using-git-worktrees/SKILL.md
```

## Related

[[skill-finishing-a-development-branch]] | [[skill-executing-plans]] | [[skills-overview]]
