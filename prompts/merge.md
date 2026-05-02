# merge.md · 三 AI 合并 Prompt

> 用法：在新的 Claude 对话里粘贴此 prompt + 三份 AI 的 cleanup 输出。
> Claude 作为合并者，产出最终 notes.md。

---

## 你的角色

我（默寺）让三个 AI 用同一份 cleanup.md 规则独立整理了同一份会议记录。

现在你（Claude）是**最终合并者**。三份输出在你面前，你需要产出一份最终 notes.md。

---

## 合并规则

### 1. 以 Claude 自己那份为基础

经验上 Claude 在语气保留方面通常最稳。**以 Claude 版作为底稿。**

### 2. 比对 GPT 版

- 如果 GPT 版本捕捉到了 Claude 漏掉的**事实**（默寺确实说过的话），补进来，标注 `[来自 GPT 版]`
- 如果 GPT 版本只是表达更顺畅但内容相同，**忽略**——不为表达细节做合并
- 如果 GPT 版本有 Claude 没有的 `[AI 建议]` 视角，可以并入建议段

### 3. 比对 Gemini 版

- Gemini 版的主要价值是 **method-candidates 段落**——这部分以 Gemini 版为准
- Gemini 整理稿如果和 Claude/GPT 有出入，**优先 Claude/GPT 版**（Gemini 在中文长文整理上偶尔会过度概括）
- Gemini 抽出的方法论候选条目，整合到最终 notes 末尾的 `## method-candidates` 段

### 4. 三份分歧大的地方

如果三个 AI 在某个学生段落上**判断方向不一致**（比如 Claude 说"批评偏重"，GPT 说"批评清晰"），**不要擅自合并**。在 notes.md 末尾加一段：

```markdown
## ⚠️ 待默寺裁决

### <学生化名> · 段落 X
- Claude 版认为：...
- GPT 版认为：...
- 建议默寺自己定。
```

宁可让默寺手动选，不要让 AI 投票决定。

### 5. 保持 cleanup.md 的所有硬约束

合并稿仍然必须：
- 保留语气指纹
- 三段式结构（默寺点评 / [AI 建议] / [AI 补充]）
- AI 内容视觉隔离
- 化名而非真名
- 标签从词典取

如果三份输入里有违反 cleanup.md 的内容，**合并时修正**。

---

## 输出格式

直接产出最终 notes.md 的完整内容，可粘贴入仓库。

文件开头加 YAML frontmatter：

```yaml
---
week: <周次>
date: <日期>
attendees: [默寺, 🍀, 汪汪鱼布吉岛, 🍅, COFFEE, Mesejako, 茶本茶]
tags: [本次例会主要标签]
merged_from: [Claude, GPT, Gemini]
status: pending_review  # 默寺审阅后改为 reviewed
---
```

---

## 你不要做的事

- ❌ 不要重新整理（输入已经是整理过的，你只做合并）
- ❌ 不要替默寺裁决分歧
- ❌ 不要为了"更全面"而把三份内容简单堆叠——选择优于堆砌
- ❌ 不要在合并稿里写"经过三方对照后..."这种元叙事
