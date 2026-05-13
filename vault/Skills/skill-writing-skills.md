---
title: Skill — Writing Skills
tags: [skill, meta, documentation, tdd]
aliases: [writing-skills-skill]
---

# Skill: writing-skills

## מה הסקיל עושה

**יצירת סקילים חדשים** — TDD מיושם על תיעוד תהליכים: כותבים test cases (תרחישי לחץ), רואים agents נכשלים, כותבים סקיל, ורואים agents עוקבים.

### עיקרון הליבה

> "כתיבת סקילים = TDD לתיעוד. אם לא ראית agent נכשל בלי הסקיל — אתה לא יודע אם הסקיל מלמד את הדבר הנכון."

### מהו סקיל?

- **הוא**: מדריך לטכניקות מוכחות, patterns, כלים
- **הוא לא**: סיפור על איך פתרתי בעיה פעם אחת

### TDD Mapping

| TDD מקורי | סקילים |
|-----------|--------|
| RED — טסט נכשל | תרחיש לחץ עם agent ללא הסקיל |
| GREEN — קוד עובר | כתיבת הסקיל שמתקנת התנהגות |
| REFACTOR — שיפור | סגירת פרצות, בהירות |

### קבצי עזר

| קובץ | תוכן |
|------|------|
| `anthropic-best-practices.md` | best practices של Anthropic לכתיבת סקילים |
| `persuasion-principles.md` | עקרונות שכנוע לניסוח אפקטיבי |
| `testing-skills-with-subagents.md` | כיצד לבדוק סקיל עם subagent |

## נתיב

```
.claude/skills/writing-skills/SKILL.md
.claude/skills/writing-skills/anthropic-best-practices.md
.claude/skills/writing-skills/persuasion-principles.md
.claude/skills/writing-skills/testing-skills-with-subagents.md
.claude/skills/writing-skills/render-graphs.js
.claude/skills/writing-skills/graphviz-conventions.dot
```

## Related

[[skill-tdd]] | [[skill-using-superpowers]] | [[skills-overview]]
