---
title: Skill — Obsidian Markdown
tags: [skill, obsidian, markdown, notes]
aliases: [obsidian-md-skill]
---

# Skill: obsidian-markdown

## מה הסקיל עושה

**כתיבת Obsidian Flavored Markdown** — מלמד את תחביר Obsidian המיוחד שמעבר ל-CommonMark/GFM.

### תחביר ייחודי ל-Obsidian

#### Wikilinks
```markdown
[[Note Name]]                    קישור לפתק
[[Note Name|Display Text]]       טקסט תצוגה מותאם
[[Note Name#Heading]]            קישור לכותרת
```

#### Embeds
```markdown
![[note-name]]                   הטמעת פתק
![[image.png]]                   הטמעת תמונה
![[note.md#section]]             הטמעת קטע ספציפי
```

#### Callouts
```markdown
> [!info] כותרת
> תוכן ה-callout
```

#### Properties (Frontmatter)
```yaml
---
title: שם הפתק
tags: [tag1, tag2]
aliases: [שם חלופי]
---
```

## מתי להפעיל

כשעובדים עם קבצי `.md` ב-Obsidian, או כשהמשתמש מזכיר: wikilinks, callouts, frontmatter, tags, embeds, Obsidian notes.

## נתיב

```
.claude/skills/obsidian-markdown/SKILL.md
```

## Related

[[skill-obsidian-vault-workflow]] | [[skill-obsidian-bases]] | [[skills-overview]]
