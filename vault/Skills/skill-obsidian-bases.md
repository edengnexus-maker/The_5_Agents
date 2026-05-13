---
title: Skill — Obsidian Bases
tags: [skill, obsidian, bases, database, views]
aliases: [obsidian-bases-skill]
---

# Skill: obsidian-bases

## מה הסקיל עושה

**יצירת Obsidian Bases** — קבצי `.base` שיוצרים views (table, cards, list, map) של פתקים בvault, כמו database.

### תהליך

1. **צור קובץ** `.base` עם YAML תקין
2. **הגדר scope** עם `filters` (לפי tag, folder, property, תאריך)
3. **הוסף formulas** (אופציונלי) — מאפיינים מחושבים
4. **הגדר views** — table/cards/list/map עם `order` של מאפיינים
5. **אמת** YAML ובדוק רפרנסים
6. **בדוק** ב-Obsidian שה-view נטען

### דוגמת Base

```yaml
filters:
  and:
    - tag: skill

formulas:
  type_label: "upper(prop('type'))"

views:
  - type: table
    name: All Skills
    order:
      - title
      - type_label
```

## מתי להפעיל

כשעובדים עם קבצי `.base`, יוצרים database-views של פתקים, או כשהמשתמש מזכיר: Bases, table views, card views, filters, formulas.

## נתיב

```
.claude/skills/obsidian-bases/SKILL.md
```

## Related

[[skill-obsidian-markdown]] | [[skill-obsidian-vault-workflow]] | [[skills-overview]]
