---
name: cny-commit-greeting
description: Use during Spring Festival core period (除夕 2026-02-16 to 初五 2026-02-21) when the user asks you to commit — appends a zodiac-year blessing to the commit message. MUST be disabled immediately when user requests, and stay silent for the rest of the conversation.
---

# 📝 Commit 吉祥话

## 功能

在春节期间，当用户请求 git commit 时，在 commit message 末尾自动附加一句马年吉祥话。

## 触发条件

**全部满足时才触发：**

1. 当前日期在春节活跃期内（`data.json` 中的 `festival_start` 至 `festival_end`）
2. 用户请求执行 git commit
3. 本功能**未被用户关闭**

## 关闭机制（最高优先级）

**当用户表达以下任意意图时，立即且永久（本次对话内）关闭此功能：**

- 「别加吉祥话了」「关掉」「不要了」「停」「关闭 commit 吉祥话」
- 「commit 不用加那个」「别往 commit 里塞东西了」
- 任何表达不希望 commit message 被修改的意图

**关闭后的行为：**

- 立即停止，当前及后续所有 commit 均不再附加吉祥话
- 不做任何提示、不追问「确定吗」、不解释、不挽留
- 安静地恢复正常 commit 流程，就像此功能从未存在
- 本次对话内不再自动恢复，除非用户主动要求重新开启

**重新开启：** 仅当用户明确说「开启 commit 吉祥话」「加回来」等时恢复。

## 行为规则

### 1. 附加方式

在 commit message 的 `Co-Authored-By` 行之前（如有），插入一行吉祥话：

```
原始 commit message 内容

🐴 马到成功！

Co-Authored-By: Claude Opus 4.6 <noreply@anthropic.com>
```

如果没有 Co-Authored-By 行，则附加在 message 末尾：

```
原始 commit message 内容

🐴 马到成功！
```

### 2. 吉祥话选取

- 从 `data.json` 的 `commit_greetings` 中随机选取
- 避免连续重复（记住最近 3 条）
- 根据 commit 类型适配：
  - `feat` 类 → 优先选 `success` 分类（马到成功、一马当先）
  - `fix` 类 → 优先选 `fix` 分类（马上搞定、药到病除）
  - `refactor` / `chore` 类 → 优先选 `effort` 分类（马不停蹄、快马加鞭）
  - 其他 → 从 `general` 中随机选

### 3. 格式要求

- 吉祥话独占一行，前后各一个空行
- 以生肖 emoji 开头：`🐴`
- 简短有力，不超过 15 个字

## 非春节期间

此功能静默，不产生任何输出，不修改 commit message。

## 数据结构

数据文件位于 `data.json`，格式如下：

```json
{
  "year": 2026,
  "zodiac": "马",
  "festival_start": "2026-02-16",
  "festival_end": "2026-02-21",
  "commit_greetings": {
    "success": ["🐴 马到成功！"],
    "fix": ["🐴 马上搞定！"],
    "effort": ["🐴 马不停蹄！"],
    "general": ["🐴 马年大吉！"]
  }
}
```

## 年度更新指南

每年只需：
1. 更新 `data.json`，替换生肖 emoji、吉祥话和日期
2. 使用 `versioning` skill 确定版本号并更新插件元数据
