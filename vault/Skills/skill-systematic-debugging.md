---
title: Skill — Systematic Debugging
tags: [skill, debugging, root-cause]
aliases: [debugging-skill, systematic-debug]
---

# Skill: systematic-debugging

## מה הסקיל עושה

**דיבוג שיטתי — חיפוש גורם שורש** — מונע "תיקונים אקראיים" שיוצרים bugs חדשים.

### Iron Law

```
ללא חקירת גורם שורש — אסור להציע תיקונים
```

### שלבים

- **Phase 1**: ניתוח הסימפטומים, איסוף נתונים, שחזור עקבי
- **Phase 2**: זיהוי גורם השורש (לא הסימפטום!)
- **Phase 3**: הצעת תיקון ממוקד לגורם השורש

### קבצי עזר בסקיל

| קובץ | תוכן |
|------|------|
| `root-cause-tracing.md` | טכניקות לאיתור גורם שורש |
| `defense-in-depth.md` | שכבות הגנה בדיבוג |
| `condition-based-waiting.md` | המתנה לתנאי במקום sleep |
| `find-polluter.sh` | איתור "מזהם" בטסטים |

## מתי להפעיל

לכל בעיה טכנית: כישלון טסטים, bugs, התנהגות בלתי צפויה, בעיות performance.

## נתיב

```
.claude/skills/systematic-debugging/SKILL.md
.claude/skills/systematic-debugging/root-cause-tracing.md
.claude/skills/systematic-debugging/defense-in-depth.md
.claude/skills/systematic-debugging/condition-based-waiting.md
.claude/skills/systematic-debugging/find-polluter.sh
```

## Related

[[skill-tdd]] | [[skill-verification-before-completion]] | [[skills-overview]]
