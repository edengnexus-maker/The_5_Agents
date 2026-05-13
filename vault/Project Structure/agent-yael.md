---
title: יעל — כותבת התוכן (sub-agent)
tags: [agents, yael, content-writer, team]
aliases: [yael, yael-agent, content-writer]
---

# יעל — כותבת התוכן

## תפקיד

סוכן LLM שמשכתב מאמרי גלם מ-`Content/` בסגנון המותג ושומר תוצרים ב-`Output/`.

## פרטי הסוכן

| שדה | ערך |
|-----|-----|
| **שם (name)** | `yael-content-writer` |
| **קובץ** | `.claude/agents/yael-content-writer.md` |
| **כלים מורשים** | Read, Write, Edit, Glob, Grep |
| **כלים אסורים** | Bash, WebSearch, API, Agent |
| **נוצר** | 2026-05-13 |

## Trigger Keywords

| שפה | מילות הפעלה |
|-----|-------------|
| עברית | שכתב, ערוך, נסח מחדש, תרגם, סכם, מאמר, תוכן, פוסט |
| English | rewrite, edit, rephrase, translate, summarize, article, content, post |

## Flow עבודה

1. Glob → `Content/` לאיתור מאמר
2. קרא `yael/style-guide.md` + `yael/reference/*.md` (אם קיימים)
3. שכתב — הסר CTAs/קישורי מחבר, שמור מותגים בסיפור
4. שמור `Output/<name>.md` + `Output/<name>.html` (מתבנית `yael/templates/article.html`)
5. החזר סיכום קצר לראובן

## נתיבי קבצים

```
.claude/agents/yael-content-writer.md   — הגדרת הסוכן
yael/
  templates/article.html               — תבנית HTML ({{TITLE}}, {{BODY_HTML}})
  style-guide.md                        — מדריך סגנון (עתידי, ימולא ע"י המשתמש)
  reference/                            — דוגמאות לטקסטים (עתידי)
Content/                                — מאמרי גלם לשכתוב
Output/                                 — תוצרים מוכנים (md + html)
```

## Related

[[agents-directory]] | [[claude-md]]
