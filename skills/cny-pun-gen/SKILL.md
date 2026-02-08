---
name: cny-pun-gen
description: Use when users want 马年 puns, homophonic wordplay (谐音梗), or zodiac-themed naming for variables, functions, commits, or just for fun — generates 码/马 puns and other horse-year wordplay
---

# 🐴 谐音梗生成器

## 功能

生成马年「码/马」系列谐音梗，可用于代码命名、commit message、聊天整活等场景。

## 触发方式

用户说类似以下内容时触发：
- 「来个谐音梗」「整个马年梗」
- 「给这个函数起个有年味的名字」
- 「commit message 来点马年味」
- 「帮我想个马年 slogan」

## 行为规则

### 1. 识别场景

从用户输入判断使用场景，匹配 `data.json` 中的分类：

| 场景 | 关键词 |
|------|--------|
| `code` | 变量名、函数名、类名、命名、重命名 |
| `commit` | commit、提交信息、git message |
| `slogan` | 口号、标语、slogan、座右铭 |
| `chat` | 聊天、朋友圈、群消息、整活、搞笑 |
| `any` | 默认/随便来一个 |

### 2. 生成谐音梗

**核心梗库：** 读取 `data.json` 中的 `pun_pairs`（谐音对照表）和 `examples`。

**生成规则：**

- 优先使用「码/马」核心谐音对，也可扩展其他马年相关谐音
- 如果用户给了具体输入（如一个函数名），围绕该输入创作
- 每次输出 3-5 个选项
- 标注原词→谐音词的对应关系，方便理解

**输出格式（代码命名场景）：**

```
🐴 马年命名建议：

1. `horsepower()` → 码力全开的函数
   马力 → 码力，寓意性能拉满

2. `runLikeMa()` → 跑得飞快
   快马加鞭 → 快码加鞭

3. `const STABLE_BUILD = true`
   马厩(stable) = 稳定版，一语双关

想用哪个？或者告诉我具体要命名什么～
```

**输出格式（commit message 场景）：**

```
🐴 马年 commit message：

1. 🐴 feat: 码到成功 — add payment module
2. 🐴 fix: 万马奔腾 — resolve race condition
3. 🐴 refactor: 一马平川 — flatten nested callbacks

挑一个或告诉我你改了什么，帮你定制～
```

**输出格式（聊天/整活场景）：**

```
🐴 马年谐音梗连发：

• 你这个人真有「码」力 (魅力)
• 这件事「马」上就办 (马上 = 立刻)
• 别催了，我在「码」不停蹄地干呢 (马不停蹄)
• 今天的 KPI？一「码」平川！(一马平川)

要更多还是换个方向？
```

### 3. 用户互动

- 用户可以要求「再来几个」「换个方向」「更搞笑的」
- 如果用户给了一个词/句子，尝试找到谐音改造点

## 边界情况

- 非马年时仍可使用，但提示「这些是马年限定梗，跨年使用效果翻倍！」
- 如果实在找不到好的谐音，坦白说「这个词马年梗不太好接，换一个试试？」
- 避免低俗或冒犯性谐音

## 数据结构

数据文件位于 `data.json`，格式如下：

```json
{
  "year": 2026,
  "zodiac": "马",
  "pun_pairs": [
    { "original": "马", "pun": "码", "context": "编程/代码" }
  ],
  "examples": {
    "code": ["..."],
    "commit": ["..."],
    "slogan": ["..."],
    "chat": ["..."]
  }
}
```

## 年度更新指南

每年只需：
1. 更新 `data.json`，替换为新生肖的谐音对和示例
2. 使用 `versioning` skill 确定版本号并更新插件元数据
