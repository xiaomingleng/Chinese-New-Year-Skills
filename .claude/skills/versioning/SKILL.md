---
name: versioning
description: Use when making changes to this plugin's skills, data, or configuration — determines correct version bump and updates plugin.json and marketplace.json accordingly
---

# Versioning

## Version Format

`{year}.{major}.{minor}` — e.g., `2026.1.0`

## When to Bump

- **Year**: Determined by Chinese Lunar Calendar. Before the end of the 2nd lunar month of the current Chinese New Year, use that year. After that, switch to next year and reset to `{next_year}.1.0`. Reference `shared/zodiac.json` for lunar new year dates — the 2nd lunar month ends approximately 60 days after the lunar new year date.
- **Major**: New skill added, skill removed, or breaking behavior change within the same year (e.g., `2026.1.x` → `2026.2.0`). Reset minor to `0`.
- **Minor**: Data fixes, schedule updates, greeting additions, typo fixes, non-breaking changes (e.g., `2026.1.0` → `2026.1.1`).

## Files to Update

On every version bump, update the `version` field in all of these files:
1. `.claude-plugin/plugin.json` — update `version` field
2. `.claude-plugin/marketplace.json` — update `plugins[0].version` field
3. `README.md` — update version in "当前版本：**X.X.X 马年 🐴**" line
4. `README.en.md` — update version in "Current version: **X.X.X Year of the Horse 🐴**" line

## Rules

- Never skip the year prefix — it must match the current zodiac year per the lunar calendar rule above.
- When in doubt between major and minor, prefer minor.
- Commit the version bump together with the changes, not separately.
