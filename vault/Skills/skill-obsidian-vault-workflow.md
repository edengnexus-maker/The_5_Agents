---
title: Skill — Obsidian Vault Workflow
tags: [skill, obsidian, vault, memory, workflow]
aliases: [vault-workflow-skill, obsidian-vault]
---

# Skill: obsidian-vault-workflow

## מה הסקיל עושה

**ניהול vault הזיכרון ארוך-הטווח של הפרויקט** — קריאת קונטקסט רלוונטי לפני כל משימה, ועדכון קובץ הנושא אחרי כל משימה.

### עיקרון הליבה

> "הvault ב-`vault/` הוא הזיכרון ארוך-הטווח. קריאה לפני + עדכון אחרי = **חובה**."

### Phase 1 — לפני המשימה

1. **זהה נושא** בביטוי קצר
2. **מצא קובץ נושא** ב-`vault/` (exact match → close match → חדש בסוף)
3. **קרא** את קובץ הנושא מלא אם קיים
4. **קרא** 2-3 Meeting Notes אחרונים + Content Briefs רלוונטיים + Brand Guidelines
5. **דווח** מה טענת (משפט אחד)

### Phase 2 — אחרי המשימה

1. **בחר תיקייה**: Meeting Notes / Content Briefs / Publishing Log / Brand Guidelines
2. **קבע שם קובץ**: `<נושא-בminus>.md` (ללא תאריך)
3. **עדכן Overview** רק אם השתנה scope/status
4. **עדכן Open Questions** — הוסף חדשות, הסר שנפתרו
5. **הוסף Session Log entry** בתחתית
6. **וודא** Read-back לאימות

### מבנה קובץ נושא

```markdown
# כותרת הנושא

## Overview
2-6 משפטים על הנושא

## Open Questions
- שאלה פתוחה

## Session Log
### YYYY-MM-DD — כותרת [status]
- **What was done:** ...
- **Decisions:** ...
- **Notes / Caveats:** ...
- **Related:** [[wikilink]]
```

### תגי Status

`[shipped]` `[spiked]` `[wip]` `[reverted]` `[planned]` `[debug]`

## מתי להפעיל

**כל משימה** — קוד, תוכן, ארכיטקטורה, UI, bugfix, review.
חריג יחיד: שאלות read-only שלא נוגעות בקבצים ולא מייצרות החלטות.

## נתיב

```
.claude/skills/obsidian-vault-workflow/SKILL.md
vault/  (הvault עצמו)
```

## Related

[[skill-obsidian-markdown]] | [[skill-obsidian-bases]] | [[skill-using-superpowers]] | [[skills-overview]]
