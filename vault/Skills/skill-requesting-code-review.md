---
title: Skill — Requesting Code Review
tags: [skill, code-review, quality]
aliases: [code-review-request-skill]
---

# Skill: requesting-code-review

## מה הסקיל עושה

**בקשת ביקורת קוד מ-subagent** — שולח reviewer מתמחה לבדוק את העבודה לפני שהיא מתמזגת.

### עיקרון הליבה

> "Review מוקדם, Review תכוף."

### מתי חובה

- אחרי כל משימה ב-subagent-driven-development
- לאחר השלמת פיצ'ר גדול
- לפני merge ל-main

### תהליך

1. **השג git SHAs**: BASE_SHA ו-HEAD_SHA
2. **צור בריף לreviewer** — מה בנית, spec requirements, git range
3. **שלח subagent** עם הקונטקסט המדויק (ללא היסטוריית שיחה)
4. **קבל ממצאים** וטפל בהם

## נתיב

```
.claude/skills/requesting-code-review/SKILL.md
.claude/skills/requesting-code-review/code-reviewer.md
```

## Related

[[skill-receiving-code-review]] | [[skill-verification-before-completion]] | [[skill-finishing-a-development-branch]] | [[skills-overview]]
