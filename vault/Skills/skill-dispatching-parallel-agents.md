---
title: Skill — Dispatching Parallel Agents
tags: [skill, agents, parallel, delegation]
aliases: [parallel-agents-skill]
---

# Skill: dispatching-parallel-agents

## מה הסקיל עושה

**שליחת סוכנים מרובים במקביל** — כשיש 2+ בעיות עצמאיות, שולחים סוכן לכל אחת בו-זמנית במקום לעבוד סדרתית.

### עיקרון הליבה

> "שלח סוכן אחד לכל domain עצמאי. תן להם לעבוד במקביל."

### מתי כדאי

```
מספר כישלונות/משימות → האם עצמאיים? → האם יכולים להיות מקביל?
```

- **כן** → Parallel dispatch
- **לא** → Sequential agents
- **קשורים** → Agent אחד לכולם

### כיצד להשתמש

1. **זהה** את הבעיות/משימות העצמאיות
2. **בנה** הוראות מפורטות לכל סוכן (בלי קונטקסט משיחה זו)
3. **שלח** את כולם בהודעה אחת עם מספר Agent tool calls
4. **אסוף** תוצאות וסנתז

## מתי להפעיל

כשיש 2+ משימות עצמאיות שאין ביניהן תלויות state.

## נתיב

```
.claude/skills/dispatching-parallel-agents/SKILL.md
```

## Related

[[skill-subagent-driven-development]] | [[skill-executing-plans]] | [[skills-overview]]
