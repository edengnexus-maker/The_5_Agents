---
title: .claude/settings.local.json
tags: [config, claude-code, permissions]
aliases: [claude-settings, settings-local]
---

# .claude/settings.local.json

## מה הקובץ עושה

`.claude/settings.local.json` הוא קובץ הגדרות **מקומי** של Claude Code לפרויקט זה. הוא מגדיר **הרשאות Bash** — אילו פקודות Claude יכול להריץ ישירות ללא אישור המשתמש.

> **שים לב**: קובץ זה **לא נשמר ב-Git** (מוסתר ע"י `.gitignore`) כי הוא per-machine.

### הרשאות נוכחיות

הקובץ מכיל רשימת `allow` עם פקודות git ספציפיות שאושרו בעבר:

- `git commit` — יצירת commit ראשוני
- `git remote add` — הוספת remote
- `git ls-remote` — בדיקת remote
- `git remote -v` — הצגת remotes
- `git log --oneline` — היסטוריית commits
- `git status` — מצב העבודה

### מבנה JSON

```json
{
  "permissions": {
    "allow": ["Bash(...)"],
    "deny": []
  }
}
```

## שיוך — למי שייך

> **ראובן** — מנכ"ל / תשתית. קובץ זה מגדיר מה Claude (ראובן) יכול לעשות אוטומטית.

## נתיב בפרויקט

```
.claude/settings.local.json  (לא ב-Git)
```

## Related

[[claude-md]] | [[gitignore]]
