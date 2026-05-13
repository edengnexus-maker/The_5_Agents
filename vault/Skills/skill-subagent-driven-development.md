---
title: Skill — Subagent-Driven Development
tags: [skill, agents, development, quality]
aliases: [subagent-dev-skill]
---

# Skill: subagent-driven-development

## מה הסקיל עושה

**פיתוח מבוסס תת-סוכנים** — כל משימה מתוכנית → סוכן חדש נשלח → review כפול (spec + quality).

### עיקרון הליבה

> "סוכן רענן לכל משימה + review דו-שלבי = איכות גבוהה, איטרציה מהירה"

### תהליך

1. **לכל משימה**: שלח subagent חדש עם קונטקסט מדויק
2. **Review שלב 1**: spec compliance — האם הכוד עומד בדרישות?
3. **Review שלב 2**: code quality — האם הקוד עצמו טוב?
4. **המשך** — ללא עצירה לבדיקות עם המשתמש בין משימות

> **עצור רק** אם: BLOCKED שלא ניתן לפתור, עמימות שמונעת התקדמות, כל המשימות הסתיימו.

## מתי להפעיל

כשיש תוכנית יישום עם משימות ברובן עצמאיות, ורוצים לישאר בsession הנוכחי.

## נתיב

```
.claude/skills/subagent-driven-development/SKILL.md
.claude/skills/subagent-driven-development/implementer-prompt.md
.claude/skills/subagent-driven-development/spec-reviewer-prompt.md
.claude/skills/subagent-driven-development/code-quality-reviewer-prompt.md
```

## Related

[[skill-dispatching-parallel-agents]] | [[skill-executing-plans]] | [[skill-requesting-code-review]] | [[skills-overview]]
