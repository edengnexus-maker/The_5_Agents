---
title: .gitignore
tags: [config, git, security]
aliases: [git-ignore]
---

# .gitignore

## מה הקובץ עושה

`.gitignore` מגדיר אילו קבצים **לא ייכנסו ל-Git**. מניעת שמירת סודות ומידע מקומי ב-repository.

### קטגוריות מוסתרות

| קטגוריה | קבצים | סיבה |
|----------|--------|-------|
| **סודות** | `.env`, `.env.local`, `.env.*.local` | מפתחות API — לעולם לא ל-Git |
| **הגדרות מקומיות** | `.claude/settings.local.json` | הגדרות per-machine של Claude Code |
| **מערכת הפעלה** | `.DS_Store`, `Thumbs.db` | קבצי Mac/Windows — לא שייכים ל-repo |
| **עורכי קוד** | `.vscode/`, `.idea/`, `*.swp` | הגדרות IDE אישיות |

## שיוך — למי שייך

> **כלל הצוות** — אין סוכן ספציפי, זהו קובץ תשתית כללי

## נתיב בפרויקט

```
.gitignore  (שורש הפרויקט)
```

## Related

[[env-example]] | [[settings-local-json]]
