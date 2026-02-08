# 🧧 Chinese New Year Skills

> **May your code compile and your year be prosperous!**

Spring Festival AI skills marketplace — give your AI assistant some holiday spirit!

Claude Code plugin, versioned by zodiac year. Current version: **2026.5.2 Year of the Horse 🐴**

[中文](README.md) | English

## Install

### Claude Code (Recommended)

```bash
claude install-plugin https://github.com/xiaomingleng/Chinese-New-Year-Skills.git
```

### Manual (Universal)

```bash
git clone https://github.com/xiaomingleng/Chinese-New-Year-Skills.git
```

Each skill is a standalone `SKILL.md` (behavior instructions) + `data.json` (data) — any AI agent that reads Markdown can use them.

Copy skill files to the appropriate directory for your platform:

| Platform | Target Directory | Notes |
|----------|-----------------|-------|
| **Claude Code** | `.claude/skills/` | Copy `skills/*` and `shared/*` |
| **Cursor** | `.cursor/rules/` | Copy `SKILL.md` as `.mdc` rule files |
| **GitHub Copilot** | `.github/copilot-instructions.md` | Append skill content to instructions file |
| **Codex** | `AGENTS.md` | Append skill content to `AGENTS.md` |
| **Windsurf** | `.windsurfrules` | Append skill content to rules file |

**Example (Claude Code manual install):**

```bash
cp -r Chinese-New-Year-Skills/skills/* your-project/.claude/skills/
cp -r Chinese-New-Year-Skills/shared/* your-project/.claude/shared/
```

## Skills

| Skill | Description | Status |
|-------|-------------|--------|
| [🧧 greeting](skills/cny-greeting/) | Auto-append a zodiac blessing to every response | ✅ Ready |
| [📺 gala](skills/cny-gala/) | Spring Festival Gala schedule query + live text commentary | ✅ Ready (unofficial data) |
| [🧮 countdown](skills/cny-countdown/) | Spring Festival countdown + lunar date conversion + timeline | ✅ Ready |
| [💬 wechat-greeting](skills/cny-wechat-greeting/) | Generate WeChat greetings by recipient type | ✅ Ready |
| [🐴 pun-gen](skills/cny-pun-gen/) | Year of the Horse pun generator (horse/code wordplay) | ✅ Ready |
| [📝 commit-greeting](skills/cny-commit-greeting/) | Auto-append blessings to git commits (can be toggled off) | ✅ Ready |

## Directory Structure

```
chinese-new-year-skills/
├── .claude-plugin/
│   ├── plugin.json              # Plugin metadata
│   └── marketplace.json         # Marketplace manifest
├── .claude/
│   └── skills/
│       └── versioning/
│           └── SKILL.md         # Versioning convention (internal)
├── skills/
│   ├── cny-greeting/
│   │   ├── SKILL.md             # Behavior spec
│   │   └── data.json            # Horse year blessings
│   ├── cny-gala/
│   │   ├── SKILL.md             # Behavior spec
│   │   ├── schedule.json        # Gala program schedule
│   │   └── live.json            # Live broadcast data
│   ├── cny-countdown/
│   │   ├── SKILL.md             # Behavior spec
│   │   └── data.json            # Lunar date mapping + milestones
│   ├── cny-wechat-greeting/
│   │   ├── SKILL.md             # Behavior spec
│   │   └── data.json            # Recipient-based greeting templates
│   ├── cny-pun-gen/
│   │   ├── SKILL.md             # Behavior spec
│   │   └── data.json            # Pun reference table + examples
│   └── cny-commit-greeting/
│       ├── SKILL.md             # Behavior spec
│       └── data.json            # Commit blessing library
├── shared/
│   └── zodiac.json              # Zodiac cycle reference
└── README.md
```

## Design Principles

**Claude Code plugin standard** — follows `.claude-plugin/` format, installable and manageable via the Claude Code plugin system.

**SKILL.md + data separation** — behavior logic in SKILL.md, yearly data in JSON files in the same directory.

**Versioned by zodiac year** — version format `{year}.{major}.{minor}`, year follows the lunar zodiac calendar.

**Plug and play** — each skill is independent, can be installed individually or combined.

## Yearly Update Process

When the new year arrives:

1. Update data files in each skill directory (`data.json`, `schedule.json`, etc.)
2. Use the `versioning` skill to determine the new version number
3. Update version in `.claude-plugin/plugin.json` and `marketplace.json`
4. Done 🎉

## Roadmap

- 🔖 Spring couplet generator
- 🧧 Red envelope cover recommendations
- 🍽️ New Year's Eve dinner recipe assistant
- 🌍 Multi-language blessings (English, Cantonese, Hokkien...)

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=xiaomingleng/Chinese-New-Year-Skills&type=date&legend=top-left)](https://www.star-history.com/#xiaomingleng/Chinese-New-Year-Skills&type=date&legend=top-left)

## License

MIT
