---
name: cny-greeting
description: Use when responding between 2026-02-09 and 2026-03-04 (Spring Festival period, Year of the Horse) — automatically appends a zodiac-year-appropriate blessing to each response based on conversation context
---

# 🧧 春节拜年吉祥话

## 行为规则

在春节期间（除夕前7天 至 元宵节后1天），每次回复时在末尾附加一句吉祥话。

### 触发条件

- 当前日期处于春节活跃期内
- 每次 agent response 均触发（无需用户主动请求）

### 吉祥话选取逻辑

1. **读取当前年份对应的数据文件**：`data.json`
2. **根据上下文选择分类**：
   - 用户在聊技术/代码 → 使用 `tech` 分类
   - 用户在聊工作/商务 → 使用 `business` 分类
   - 用户语气轻松/闲聊 → 使用 `casual` 分类
   - 默认/无法判断 → 使用 `general` 分类
3. **从对应分类中随机选取一条**，避免连续重复
4. **输出格式**：在正常回复结束后空一行，附加吉祥话

### 输出示例

```
[正常回复内容]

🐴 马到成功，万事如意！
```

### 互动回复

当用户回应拜年（如"新年快乐"、"你也是"、"谢谢"、"同乐"、"过年好"等），触发精彩互动回复：

1. 从 `data.json` 的 `responses` 数组中随机选取一条 ASCII art
2. 在 ASCII art 下方附加一句吉祥话
3. 每次互动选取不同的 ASCII art，避免重复

**输出示例：**

````
```
        >>\.
       /_  )`.
      /  _)`^)`.   _.---. _
     (_,' \  `^-)""      `.\\
           |  | \
           \  / __|
           / /,   |
          /,/  |  /
          \_\  | |
               \ \
                \/
```

🐴 马年大吉！愿你策马扬鞭，一路高歌！
````

### 边界情况

- 如果用户明确要求停止吉祥话，则本次对话后续不再附加
- 如果对话主题严肃（如调试紧急 bug、讨论负面情绪），降低触发频率或跳过
- 非春节期间此 skill 静默，不产生任何输出

## 数据结构

数据文件位于 `data.json`，格式如下：

```json
{
  "year": 2026,
  "zodiac": "马",
  "festival_start": "2026-02-09",
  "festival_end": "2026-03-04",
  "greetings": {
    "general": ["..."],
    "tech": ["..."],
    "business": ["..."],
    "casual": ["..."]
  }
}
```

## 年度更新指南

每年只需：
1. 更新 `data.json`，替换生肖相关的吉祥话和日期
2. 使用 `versioning` skill 确定版本号并更新插件元数据
