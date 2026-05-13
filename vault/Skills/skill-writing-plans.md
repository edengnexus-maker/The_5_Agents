---
title: Skill — Writing Plans
tags: [skill, planning, implementation]
aliases: [writing-plans-skill]
---

# Skill: writing-plans

## מה הסקיל עושה

**כתיבת תוכנית יישום מפורטת** — מפרק spec למשימות bite-sized עם הוראות מלאות לכל מפתח שאין לו קונטקסט של הפרויקט.

### עקרונות הסקיל

- **DRY, YAGNI, TDD** — ללא הכפלה, רק מה שצריך, טסטים קודם
- **Commits תכופים** — כל משימה קטנה מסתיימת ב-commit
- **מיפוי קבצים** — לפני הגדרת משימות, מפה אילו קבצים ייוצרו/ישתנו
- **גבולות ברורים** — כל קובץ אחריות אחת

### פלט הסקיל

מסמך plan נשמר ב:
```
docs/superpowers/plans/YYYY-MM-DD-<feature-name>.md
```

## מתי להפעיל

לאחר שיש spec מאושר (מ-brainstorming), לפני נגיעה בקוד.

## נתיב

```
.claude/skills/writing-plans/SKILL.md
.claude/skills/writing-plans/plan-document-reviewer-prompt.md
```

## Related

[[skill-brainstorming]] | [[skill-executing-plans]] | [[skill-subagent-driven-development]] | [[skills-overview]]
