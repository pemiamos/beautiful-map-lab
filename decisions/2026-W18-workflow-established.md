---
date: 2026-05-02
week: 18
decision_type: 保留方案
related_students: [全组]
tags: [GitHub工程化, 方法论缺失]
---

# 2026-W18 · 仓库工作流确立

> decisions/ 的第一条记录，本身就是关于"我们如何记录"的决策。

---

## 背景

最美地图研究所的教学过程涉及大量批评、点评、方法论沉淀。原先散落在微信群、Notion、口头例会中。需要一套系统化的记录方式，让：

- 学生看见自己的成长轨迹
- 默寺能复用过去的批评和方法论
- AI 能辅助整理但不替代判断
- 长期积累形成对外的研究资产

---

## 决策

建立公开 GitHub 仓库 `beautiful-map-lab`，采用以下工作流：

### 仓库结构

```
beautiful-map-lab/
├── README.md
├── prompts/      AI 整理 prompt
├── templates/    Obsidian Templater 模板
├── meetings/     每周会议（扁平命名 2026-Wxx-raw / 2026-Wxx-notes）
├── students/     每位同学每周档案（slug-2026-Wxx.md）
├── decisions/    重大决策记录
├── methods/      可复用方法
└── assets/       图片与截图（按周分子目录）
```

### 工作流

```
学生 Notion 周报
  ↓
默寺线上/线下例会即时点评
  ↓
raw.md（化名替换在此完成）
  ↓
三 AI（Claude / GPT / Gemini）平行用 cleanup.md 整理
  ↓
Claude 用 merge.md 合并
  ↓
notes.md（默寺审阅）
  ↓
分发到 students/<slug>-Wxx.md + methods/method-candidates/
  ↓
push GitHub
```

### 三条铁律

1. AI 整理判断，AI 不产生判断
2. 保留默寺的语气指纹
3. methods/ 必须人工审核才能进

### 化名机制

学生在仓库里以自选化名出现：

| 化名 | 班级 | slug |
|---|---|---|
| 🍀 | 工设232 | clover |
| 汪汪鱼布吉岛 | 工设241 | wangwang |
| 🍅 | 工设232 | tomato |
| COFFEE | 工设242 | coffee |
| Mesejako | 工设242 | mesejako |
| 茶本茶 | 产设231 | chabencha |

真名只存在于本地 `name-mapping.md`（不入库）。

---

## 理由

### 为什么用 GitHub 而非 Notion

- Notion 适合学生写周报（已在用）
- GitHub 适合长期档案、版本管理、对外公开、未来 RAG 化
- 两者各司其职，不互相替代

### 为什么用 Obsidian + GitHub 组合

- Obsidian 本地编辑零学习成本（默寺已熟练）
- Obsidian Git 插件自动 commit/push，不用碰命令行
- vault = repo 根目录，无中间转换
- 双向链接对应"会议笔记 ↔ 学生档案"交叉引用

### 为什么坚持"AI 不产生判断"

默寺刚刚批评学生「不要把活全踢给 AI」。如果仓库本身让 AI 替默寺做教学判断，会从根上动摇这套方法论的权威。

cleanup.md 里所有约束的设计都围绕这一条。

### 为什么用化名

公开仓库 + 真实学生姓名 + 真实批评 = 长期对学生的潜在伤害。

化名让档案语气从"教学"转为"研究"，给学生主动权（自选化名），降低公开档案对个人的人格化指向。

不是脱敏（仓库公开但不涉及隐私敏感信息），是写作伦理。

---

## 备选方案为什么被放弃

### 方案 A：完整大教研平台（GPT 第一轮建议）

- 7 个一级目录（Project-Brief / Weekly-Reports / Critique-Archive / Design-Decisions / Visual-Evidence / Knowledge-Base / Final-Reflection）
- GitHub Issues + Projects 看板
- n8n 自动化中枢
- 内外双仓库（私有 + 脱敏公开）

**放弃理由**：维护成本过高。第三周开始默寺就会停止维护一半目录。「目录数量和坚持度成反比」。

### 方案 B：Notion 内闭环

- 全部留在 Notion，不开 GitHub 仓库

**放弃理由**：Notion 不利于长期版本管理、对外公开、未来 RAG 化。星尘的对外资产应该在公开 GitHub 上。

### 方案 C：完全自动化（录音 → AI → 自动合并 → 自动入库）

**放弃理由**：违反铁律一。AI 一旦自动 merge，默寺的判断权就被让渡。当前流程为「AI 自动 PR，默寺手动 merge」。

---

## 三个月后回看

（W30 左右回填）

- 是否真的每周维护？
- 三 AI 流程是否运转顺畅？
- methods/ 是否真的沉淀出可复用条目？
- 是否需要调整结构？

---

## 关联资源

- 仓库 README：[[../README]]
- 整理 prompt：[[../prompts/cleanup]]
- 合并 prompt：[[../prompts/merge]]
- 第一篇真实档案：[[../meetings/2026-W18-notes]]
