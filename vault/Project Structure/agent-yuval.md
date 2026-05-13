---
title: יובל — מעצב התמונות (sub-agent)
tags: [agents, yuval, image-designer, team]
aliases: [yuval, yuval-agent, image-designer]
---

# יובל — מעצב התמונות

## תפקיד

סוכן LLM שמייצר תמונות עבור הפרויקט. סורק `yuval/reference/` להשראת סגנון, מנסח prompt משולב, קורא לסקיל [[skill-gpt-image-gen]] (OpenAI Images API, מודל `gpt-image-2`), ושומר תמונה מוכנה ל-`yuval/outputs/`.

## פרטי הסוכן

| שדה | ערך |
|-----|-----|
| **שם (name)** | `yuval` |
| **קובץ** | `.claude/agents/yuval.md` |
| **כלים מורשים** | Read, Write, Bash, Glob |
| **כלים אסורים** | Edit, WebSearch, Agent |
| **תלוי בסקיל** | [[skill-gpt-image-gen]] |
| **דורש env** | `OPENAI_API_KEY` |
| **נוצר** | 2026-05-13 |

## Trigger Keywords

| שפה | מילות הפעלה |
|-----|-------------|
| עברית | תמונה של, ציור של, תיצור תמונה, איור, ויזואל |
| English | image of, picture of, generate image, illustration, draw, visual |

## Flow עבודה (7 שלבים)

1. **Glob → `yuval/reference/*`** — אתר קבצי השראה (אם יש)
2. **חלץ סגנון** — פלטה, סגנון (flat/realistic/...), קומפוזיציה, אלמנטים חוזרים
3. **נסח prompt משולב** — בקשה + סגנון. אנגלית, ספציפי, ז'אנר כסגנון.
4. **צור slug + נתיב** — `yuval/outputs/<YYYY-MM-DD>-<slug>.png`
5. **קרא לסקיל gpt-image-gen** — Bash, one-liner Python (משלוח JSON + decode)
6. **שמור sidecar `.txt`** עם ה-prompt + `test -s "<png>"` לאימות
7. **דווח לראובן** — נתיב, גודל, prompt מלא, reference files שהשפיעו

## נתיבי קבצים

```
.claude/agents/yuval.md              — הגדרת הסוכן
.claude/skills/gpt-image-gen/SKILL.md — מעטפת ה-API שיובל קורא לה
yuval/
  reference/                          — השראת סגנון (תמונות, קבצי .md/.txt)
  outputs/
    <YYYY-MM-DD>-<slug>.png           — תמונה מוגמרת
    <YYYY-MM-DD>-<slug>.txt           — ה-prompt ששימש (לאיטרציה)
.env                                  — מכיל OPENAI_API_KEY (local only, gitignored)
```

## אינטראקציה עם יעל

יעל ([[agent-yael]]) משאירה placeholders בפורמט `{{IMAGE_NEEDED: "תיאור"}}` במאמרים שהיא כותבת. **ראובן** (לא יעל ולא יובל) הוא זה שקורא ליובל פעם אחת לכל placeholder, ואז משלב את התמונות חזרה ב-MD/HTML של יעל ב-`Output/` עם נתיב יחסי `../yuval/outputs/<file>.png`.

## כלל ברזל — שם המודל

המודל הוא `gpt-image-2`. שוחרר ב-2026-04-21. **אסור להחליף** ל-`dall-e-3` או `gpt-image-1` גם אם נראה שהוא לא קיים. שגיאות API ≠ בעיה בשם המודל.

## Related

[[agents-directory]] | [[agent-yael]] | [[skill-gpt-image-gen]] | [[claude-md]] | [[env-example]]
