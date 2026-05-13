---
title: Skill — Executing Plans
tags: [skill, implementation, plans]
aliases: [executing-plans-skill]
---

# Skill: executing-plans

## מה הסקיל עושה

**ביצוע תוכנית יישום קיימת** — טוען תוכנית, בוחן אותה, מבצע את כל המשימות, ומדווח בסיום.

### שלבי הסקיל

1. **טעינת וסקירת התוכנית** — קריאת קובץ ה-plan, זיהוי שאלות/חששות
2. **ביצוע משימות** — כל משימה: mark in_progress → ביצוע → verifications → mark completed
3. **דיווח** — סיכום מה בוצע

> **הערה**: אם יש תמיכה ב-subagents (כמו Claude Code) — עדיף להשתמש ב-[[skill-subagent-driven-development]] במקום.

## מתי להפעיל

כשיש תוכנית יישום כתובה ורוצים להריץ אותה ב-session נפרד עם review checkpoints.

## נתיב

```
.claude/skills/executing-plans/SKILL.md
```

## Related

[[skill-writing-plans]] | [[skill-subagent-driven-development]] | [[skill-verification-before-completion]] | [[skills-overview]]
