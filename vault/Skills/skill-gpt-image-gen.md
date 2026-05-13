---
title: Skill — gpt-image-gen
tags: [skill, image-generation, openai, gpt-image-2, project-skill]
aliases: [gpt-image-gen-skill, image-api-wrapper]
---

# Skill: gpt-image-gen

## מה הסקיל עושה

**מעטפת דקה ל-OpenAI Images API** — מקבל prompt, מחזיר PNG מפוענח לנתיב יעד. זהו הסקיל שיובל ([[agent-yuval]]) קורא לו בשלב 5 של ה-flow שלו.

### עיקרון הליבה

> "הסקיל אחראי רק על הקריאה ל-API ועל פיענוח. הסגנון, ה-prompt, ה-slug, וה-sidecar — באחריות הקורא (יובל)."

## פרטים

| שדה | ערך |
|-----|-----|
| **שם** | `gpt-image-gen` |
| **קובץ** | `.claude/skills/gpt-image-gen/SKILL.md` |
| **Endpoint** | `POST https://api.openai.com/v1/images/generations` |
| **מודל** | `gpt-image-2` (יצא 2026-04-21) |
| **דורש** | `OPENAI_API_KEY` ב-`.env` + (`jq` או `python3`) + `curl` |

## כלל ברזל — שם המודל

`gpt-image-2` הוא המודל הנכון. שוחרר אחרי ה-knowledge cutoff של רוב המודלים, אז ייתכן שיהיו "תיקונים" אוטומטיים ל-`dall-e-3` או `gpt-image-1` — **אסור**. השם תקין. שגיאות = key/parameters.

## פרמטרים נתמכים

| פרמטר | ערכים |
|--------|--------|
| `model` | `gpt-image-2` (קבוע) |
| `prompt` | string (Hebrew + emoji OK) |
| `size` | `1024x1024`, `1024x1536`, `1536x1024` |
| `quality` | `low`, `medium`, `high` |
| `output_format` | `png`, `jpeg`, `webp` |

## מתי להפעיל

- כשיובל ניסח prompt וצריך לקרוא ל-API
- כל פעם שצריך לייצר תמונה מבקשת טקסט
- **לא** לקריאות ישירות מ-ראובן או מסוכנים אחרים — רק יובל (כדי לשמור על עקביות ויזואלית)

## Path Variants

- **Path A** — `jq` + `base64`: יציב כשיש `jq`
- **Path B** — Python fallback: **מועדף ב-Git Bash על Windows** (`jq` לא מותקן בברירת מחדל)
- **One-liner** — `curl` + `python3 -c json.dumps` לבנייה + `python3 -c base64.b64decode` לפענוח. מטפל ב-quoting / Hebrew / quotes ב-prompt. **זו ברירת המחדל לסוכן**.

## Anti-Patterns

- ❌ להחליף את שם המודל "כי ה-API מחזיר שגיאה" — קודם בדוק key/parameters
- ❌ לקרוא ל-API עם `$OPENAI_API_KEY` ריק — אמת עם `test -n` קודם
- ❌ לכתוב לנתיב מחוץ לתיקייה של הקורא (יובל → `yuval/outputs/` בלבד)

## Related

[[agent-yuval]] | [[claude-md]] | [[env-example]]
