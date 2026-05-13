---
title: .env.example
tags: [config, api-keys, environment]
aliases: [env-template, environment-variables]
---

# .env.example

## מה הקובץ עושה

`.env.example` הוא **תבנית** למשתני הסביבה הנדרשים להפעלת המערכת. הקובץ **מגיע ל-Git** (בניגוד ל-`.env` האמיתי) כדי שכל מפתח יידע אילו מפתחות API הוא צריך להגדיר.

### משתנים בקובץ

| משתנה | חובה/אופציונלי | שימוש |
|--------|----------------|-------|
| `ANTHROPIC_API_KEY` | **חובה** | מפתח Claude API — משמש את **כל** הסוכנים |
| `OPENAI_API_KEY` | **חובה ליובל** | יצירת תמונות דרך [[skill-gpt-image-gen]] (מודל `gpt-image-2`) |
| `TAVILY_API_KEY` | אופציונלי | חיפוש ברשת עבור **חן** (חוקרת) |
| `BRAVE_SEARCH_API_KEY` | אופציונלי | חלופה לחיפוש ברשת עבור **חן** |

## שיוך — למי שייך

| מפתח | סוכן |
|------|------|
| `ANTHROPIC_API_KEY` | כל הצוות (ראובן, יעל, יובל, חן) |
| `OPENAI_API_KEY` | **יובל** — מעצב התמונות |
| `TAVILY_API_KEY` | **חן** — החוקרת |
| `BRAVE_SEARCH_API_KEY` | **חן** — החוקרת (גיבוי) |

## נתיב בפרויקט

```
.env.example  (שורש הפרויקט — מגיע ל-Git)
.env          (שורש הפרויקט — לא מגיע ל-Git, מוסתר ע"י .gitignore)
```

## Related

[[claude-md]] | [[gitignore]] | [[agents-directory]]
