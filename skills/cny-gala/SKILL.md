---
name: cny-gala
description: Use when users ask about the 2026 Spring Festival Gala (春晚, gala date 2026-02-16) — supports program schedule queries and live text commentary on Lunar New Year's Eve
---

# 📺 春晚助手

## 功能模块

### 1. 节目单查询

用户可以用自然语言查询春晚节目信息。

**支持的查询方式：**

- 按时间：「晚上 9 点有什么节目？」
- 按类型：「有哪些小品？」「歌舞类节目有几个？」
- 按演员：「沈腾今年上春晚吗？」
- 按顺序：「第一个节目是什么？」「压轴节目是谁？」
- 概览：「给我看看完整节目单」

**回复规则：**

- 返回匹配的节目信息，包含：节目名称、类型、演员、预计时间
- 如果查询无结果，礼貌告知并建议换个关键词
- 如果节目单尚未正式公布，注明数据为预测/占位版本

### 2. 文字直播

春晚当晚提供文字解说模式。

**触发方式：**

- 用户说「开始直播」「文字直播」「现在演到哪了」等
- 仅在除夕当天（农历十二月三十）可用

**直播行为：**

- 根据当前时间匹配正在进行的节目
- 提供风格化的文字解说（热情、有趣、带梗）
- 包含节目背景小知识或冷知识
- 支持用户互动：「这个节目怎么样？」「帮我吐槽一下」

**数据来源：**

- 节目单：`schedule.json`
- 直播补充数据：`live.json`（可选，当晚更新）

## 数据结构

### schedule.json

```json
{
  "year": 2026,
  "zodiac": "马",
  "zodiac_en": "horse",
  "gala_name": "2026年中央广播电视总台春节联欢晚会",
  "gala_date": "2026-02-16",
  "start_time": "20:00",
  "end_time": "00:30",
  "source": "非官方节目单，基于网络公开信息整理，仅供参考",
  "chapters": [
    { "name": "篇章名称", "start": "20:00", "end": "21:00" }
  ],
  "programs": [
    {
      "order": 1,
      "time": "20:05",
      "chapter": 1,
      "name": "节目名称",
      "type": "歌舞|歌曲|小品|相声|魔术|杂技|武术|舞蹈|戏曲|朗诵|脱口秀|创意秀|焰火秀|特别节目|其他",
      "performers": ["演员1", "演员2"],
      "description": "节目简介"
    }
  ]
}
```

### live.json（可选）

```json
{
  "last_updated": "2026-02-16T21:30:00+08:00",
  "current_program": 5,
  "highlights": [
    {
      "time": "20:35",
      "content": "实时亮点或解说文字"
    }
  ]
}
```

## 年度更新指南

1. 春晚节目单公布后更新 `schedule.json`（通常除夕前 1-3 天）
2. 除夕当晚可选择性更新 `live.json` 提供实时数据
3. 使用 `versioning` skill 确定版本号并更新插件元数据
