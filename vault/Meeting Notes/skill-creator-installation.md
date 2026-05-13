# Skill Creator Installation

## Overview

התקנת הסקיל `skill-creator` מ-[anthropics/skills](https://github.com/anthropics/skills/tree/main/skills/skill-creator) ב-project scope של פרויקט The 5 Agents. הסקיל מאפשר יצירה ושיפור איטרטיבי של סקילים חדשים.

## Open Questions

- `claude plugin list` לא נבדק (CLI לא מותקן) — אם ה-CLI יותקן בעתיד, כדאי לאמת scope=project שם
- none אחר

## Session Log

### 2026-05-13 — התקנת skill-creator ב-project scope [shipped]

- **What was done:** `claude plugin install` לא עבד כי ה-`claude` CLI אינו ב-PATH (הדסקטופ אפ הוא Electron, לא CLI). הורדנו ידנית 18 קבצים מ-GitHub (SKILL.md, agents/, assets/, eval-viewer/, references/, scripts/) ל-`.claude/skills/skill-creator/`. הסקיל מופיע ברשימת הסקילים הפעילים. בוצע commit ו-push ל-main.
- **Decisions:** הורדה ידנית מ-raw GitHub URLs במקום `claude plugin install` — הגישה הפשוטה ביותר כשה-CLI לא זמין. scope=project מוגדר ע"י מיקום: `.claude/skills/` (project scope) ולא `~/.claude/skills/` (user scope).
- **Notes / Caveats:** ה-CLI לא מותקן כ-standalone. `claude plugin list` לא אושר. הסקיל פעיל כפי שאושר ב-system reminder.
- **Related:** [[skills-overview]] | [[skill-writing-skills]]
