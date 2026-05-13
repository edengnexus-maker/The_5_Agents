---
title: .claude/agents/ — תיקיית הסוכנים
tags: [agents, directory, team]
aliases: [agents-dir, team-definitions]
---

# .claude/agents/

## מה התיקייה עושה

`.claude/agents/` היא המקום שבו **ממוקמות הגדרות הסוכנים** של הצוות. כל סוכן מקבל קובץ הגדרות משלו שמתאר לו מי הוא, מה תפקידו, ואיך לפעול.

> **מצב נוכחי** (2026-05-13): שני סוכנים פעילים — `yael-content-writer.md` (כותבת התוכן) ו-`yuval.md` (מעצב התמונות). `chen.md` עוד לא נוצר.

## הסוכנים בצוות

| סוכן | קובץ | מצב | תפקיד |
|------|------|------|--------|
| **יעל** | `yael-content-writer.md` | ✅ פעיל | כותבת תוכן — ניסוח, עריכה, כתיבה יוצרת. מסמנת `{{IMAGE_NEEDED}}` placeholders. |
| **יובל** | `yuval.md` | ✅ פעיל | מעצב תמונות — קורא לסקיל `gpt-image-gen`, שומר ל-`yuval/outputs/` |
| **חן** | `chen.md` | ⏳ עתידי | חוקרת — איסוף מידע, מחקר, עובדות |

## שיוך — למי שייכת

> **יעל, יובל, חן** — כל שלושת הסוכנים. ראובן (מנכ"ל) מנתב אליהם.

## מבנה קובץ סוכן (עתידי)

```markdown
---
name: יעל
role: כותבת תוכן
---

# יעל — כותבת התוכן

[הוראות לסוכן: איך לכתוב, אילו כלים להשתמש, סגנון...]
```

## נתיב בפרויקט

```
.claude/agents/
  yael-content-writer.md    ✅ פעיל
  yuval.md                  ✅ פעיל
  chen.md                   (עתידי)
```

## Related

[[claude-md]] | [[agent-yael]] | [[agent-yuval]] | [[commands-directory]] | [[env-example]]
