---
title: יצירת sub-agent יובל (מעצב התמונות) + סקיל gpt-image-gen
tags: [meeting-notes, agents, yuval, gpt-image-gen, image-generation, infrastructure]
aliases: [yuval-setup, image-agent-creation]
---

# Yuval Agent Creation

## Overview

הסוכן השני בצוות (אחרי [[agent-yael]]) — **יובל**, מעצב התמונות — נוצר ב-2026-05-13 יחד עם הסקיל התומך `gpt-image-gen`. המבנה: יובל סורק `yuval/reference/` להשראת סגנון, מנסח prompt משולב, קורא לסקיל שמוציא בקשה ל-OpenAI Images API (`gpt-image-2`), ושומר את התמונה ל-`yuval/outputs/<YYYY-MM-DD>-<slug>.png` יחד עם sidecar `.txt` של ה-prompt. ראובן (orchestrator) מתאם בין יעל ([[agent-yael]]) שמזהה איפה צריך תמונה (placeholder `{{IMAGE_NEEDED: "..."}}`) לבין יובל שמייצר אותה.

## Open Questions

- האם `gpt-image-2` מקבל פרמטרים נוספים (style, seed, negative_prompt) שלא תיעדנו? לבדוק כשתהיה גישה ל-API rate-limiting / docs.
- מה הטיפול ב-multi-image בקשות (גלריה של 3 תמונות לאותו מאמר)? כרגע יובל נקרא פעם אחת לכל placeholder — אם זה איטי, אפשר לעבור ל-batch.
- האם `yuval/reference/` יזין סגנון אחד אחיד או יחזיק תיקיות-משנה (מותג A, מותג B)? תלוי איך הסדנה תתפתח.

## Session Log

### 2026-05-13 — Yuval + gpt-image-gen infrastructure [shipped]

- **What was done:**
  - יצירת [[skill-gpt-image-gen]] ב-`.claude/skills/gpt-image-gen/SKILL.md` — מעטפת ל-OpenAI Images API (`gpt-image-2`). כולל warning בולט על שם המודל (post-cutoff, אסור להחליף), canonical curl call, וגם jq וגם Python fallback ל-decode (Python מועדף ב-Git Bash).
  - יצירת [[agent-yuval]] ב-`.claude/agents/yuval.md` עם 7 שלבי workflow: סריקת reference, חילוץ סגנון, ניסוח prompt משולב, יצירת slug+נתיב, קריאה לסקיל, sidecar `.txt`+verification, דיווח מובנה.
  - יצירת `yuval/reference/` ו-`yuval/outputs/` (עם `.gitkeep`).
  - עדכון `.env` + `.env.example` — uncomment של `OPENAI_API_KEY`.
  - עדכון [[claude-md]] — הוסיף את יובל לרשימת הצוות עם trigger keywords (תמונה של / ציור של / איור; image of / picture of / illustration). הוסיף סעיף "חיבור יעל ↔ יובל" שמתאר את ה-orchestration המלא של מאמר עם תמונות. עודכן גם folder tree.
  - עדכון [[agent-yael]] (`yael-content-writer.md`) — הוסיף שלב 3.5 שבו יעל משאירה `{{IMAGE_NEEDED: "תיאור"}}` placeholders, ושינה את שלב 5 כך שהסיכום לראובן כולל את רשימת ה-placeholders שלה.
- **Decisions:**
  - **שם הקובץ של יובל**: `yuval.md` flat (לא `yuval-image-designer.md`). הוסכם עם המשתמש שהקובץ של יעל נשאר `yael-content-writer.md` (יש כבר frontmatter+ trigger קיים), אבל הקובץ החדש flat. אי-עקביות מודעת.
  - **שילוב תמונות ב-MD/HTML**: ראובן מחליף placeholders בנתיב יחסי `../yuval/outputs/<file>.png` (ולא מעתיק ל-`Output/images/`). פשטות מנצחת fan-out של תיקיות.
  - **שם מודל**: `gpt-image-2` — מודל אמיתי שיצא ב-2026-04-21, אחרי ה-knowledge cutoff. תועד warning בולט גם ב-SKILL.md וגם ב-agent yuval.md כדי למנוע "תיקון" אוטומטי ל-`dall-e-3` / `gpt-image-1`.
  - **Python fallback מועדף על jq**: ב-Git Bash על Windows, `jq` לא מגיע by default. Python כן.
- **Notes / Caveats:**
  - `.env` ב-`.gitignore` — המפתח שהמשתמש שם שם נשאר local.
  - אין כרגע automated test לקריאה ל-API. אימות end-to-end ידני (קריאה אמיתית) ידרוש שהמשתמש יוודא שהמפתח עובד.
  - `yuval/reference/` עוד ריק — בסשנים הבאים המשתמש יוסיף תמונות השראה.
- **Related:** [[agent-yuval]], [[agent-yael]], [[skill-gpt-image-gen]], [[claude-md]], [[agents-directory]], [[env-example]]
