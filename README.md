# 🧧 Chinese New Year Skills

中文 | [English](README.en.md)

> **「码」到成功，万事如意！**
>
> 一「码」当先的 AI 拜年插件 — 给你的 Claude 装上年味，「码」力全开迎新春！

春节 AI 技能市场 — 让你的 AI 助手也过年！

Claude Code 插件，按生肖年版本化管理。当前版本：**2026.5.3 马年 🐴**

## Install

### Claude Code（推荐）

```bash
claude install-plugin https://github.com/xiaomingleng/Chinese-New-Year-Skills.git
```

### 手动安装（通用）

```bash
git clone https://github.com/xiaomingleng/Chinese-New-Year-Skills.git
```

每个技能由 `SKILL.md`（行为指令）+ `data.json`（数据）组成，任何能读取 Markdown 的 AI 代理都可以使用。

按你的平台，将技能文件复制到对应目录：

| 平台 | 目标目录 | 说明 |
|------|----------|------|
| **Claude Code** | `.claude/skills/` | 复制 `skills/*` 和 `shared/*` |
| **Cursor** | `.cursor/rules/` | 将 `SKILL.md` 复制为 `.mdc` 规则文件 |
| **GitHub Copilot** | `.github/copilot-instructions.md` | 将技能内容追加到指令文件中 |
| **Codex** | `AGENTS.md` | 将技能内容追加到 `AGENTS.md` |
| **Windsurf** | `.windsurfrules` | 将技能内容追加到规则文件中 |

**示例（Claude Code 手动安装）：**

```bash
cp -r Chinese-New-Year-Skills/skills/* your-project/.claude/skills/
cp -r Chinese-New-Year-Skills/shared/* your-project/.claude/shared/
```

## Skills

| 技能 | 说明 | 状态 |
|------|------|------|
| [🧧 greeting](skills/cny-greeting/) | 每次回复自动附带一句拜年吉祥话 | ✅ 就绪 |
| [📺 gala](skills/cny-gala/) | 春晚节目单查询 + 文字直播 | ✅ 就绪（非官方数据） |
| [🧮 countdown](skills/cny-countdown/) | 春节倒计时 + 农历日期转换 + 时间线 | ✅ 就绪 |
| [💬 wechat-greeting](skills/cny-wechat-greeting/) | 按对象生成微信拜年消息 | ✅ 就绪 |
| [🐴 pun-gen](skills/cny-pun-gen/) | 马年谐音梗生成器（码/马系列） | ✅ 就绪 |
| [📝 commit-greeting](skills/cny-commit-greeting/) | commit 时自动附加吉祥话（可随时关闭） | ✅ 就绪 |

## 目录结构

```
chinese-new-year-skills/
├── .claude-plugin/
│   ├── plugin.json              # 插件元数据
│   └── marketplace.json         # 市场清单
├── .claude/
│   └── skills/
│       └── versioning/
│           └── SKILL.md         # 版本号管理规范（项目内部）
├── skills/
│   ├── cny-greeting/
│   │   ├── SKILL.md             # 行为指令
│   │   └── data.json            # 马年吉祥话库
│   ├── cny-gala/
│   │   ├── SKILL.md             # 行为指令
│   │   ├── schedule.json        # 春晚节目单
│   │   └── live.json            # 文字直播数据
│   ├── cny-countdown/
│   │   ├── SKILL.md             # 行为指令
│   │   └── data.json            # 农历日期映射 + 节点数据
│   ├── cny-wechat-greeting/
│   │   ├── SKILL.md             # 行为指令
│   │   └── data.json            # 分对象拜年话模板
│   ├── cny-pun-gen/
│   │   ├── SKILL.md             # 行为指令
│   │   └── data.json            # 谐音对照表 + 场景示例
│   └── cny-commit-greeting/
│       ├── SKILL.md             # 行为指令
│       └── data.json            # commit 吉祥话库
├── shared/
│   └── zodiac.json              # 生肖轮转表
└── README.md
```

## 设计理念

**Claude Code 插件标准** — 遵循 `.claude-plugin/` 标准格式，可通过 Claude Code 插件系统安装和管理。

**SKILL.md 与数据分离** — 行为逻辑在 SKILL.md，年度数据在同目录下的 JSON 文件中。

**版本化管理** — 版本号格式 `{year}.{major}.{minor}`，年份跟随农历生肖年。

**即插即用** — 每个 skill 独立，可单独安装，也可组合使用。

## 年度更新流程

新年到来时：

1. 更新各 skill 目录下的数据文件（`data.json`、`schedule.json` 等）
2. 使用 `versioning` skill 确定新版本号
3. 更新 `.claude-plugin/plugin.json` 和 `marketplace.json` 中的版本
4. 完成 🎉

## 未来计划

- 🔖 春联生成 skill
- 🧧 红包封面推荐
- 🍽️ 年夜饭菜谱助手
- 🌍 多语言吉祥话（英文、粤语、闽南语…）

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=xiaomingleng/Chinese-New-Year-Skills&type=date&legend=top-left)](https://www.star-history.com/#xiaomingleng/Chinese-New-Year-Skills&type=date&legend=top-left)

## License

MIT
