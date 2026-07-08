---
name: career-landing
description: "为初入 AI 行业（算法/研究、数据/ML 工程、AI 产品、AI 运营/增长、解决方案/售前）的职场新人生成个性化 landing（落地）规划。当用户刚入职 AI 行业、处于试用期/前 3 月、想规划 AI 行业职场成长路径，或提到'AI 行业 landing / 落地 / 新人适应 / 试用期规划 / 前 3 周 / 前 3 月 / 刚入职怎么规划'时触发。本 skill 先做现状诊断，再输出 landing 计划文档与可勾选 checklist，聚焦 AI 行业场景并融合 AI 时代研发策略。"
description_zh: "AI 行业新人 landing（落地）规划"
description_en: "Career landing plan for AI-industry newcomers"
version: 1.1.1
agent_created: true
allowed-tools:
  - Read
  - Write
  - Edit
  - AskUserQuestion
---

# Career Landing：AI 行业新人落地规划

为初入 AI 行业的人生成一份个性化 landing（落地）规划：先诊断现状，再产出「前 3 周 / 前 3 月」landing 计划文档 + 可勾选 checklist。聚焦 AI 行业场景，融合传统职场基本功与 AI 时代研发策略。

## 用途
帮助用户（AI 行业应届生、实习转正、刚入职新人、从其他方向转岗到 AI 的人）在入职初期建立清晰的落地路径，避免"没有 landing 期"导致的迷茫、技术地基虚、被 AI 架空。重点应对 AI 行业典型困境：技术迭代太快追不动、研究 vs 业务落地撕扯、实验跑不出结果、数学/底层虚、只会调包讲不清原理。

## 何时使用
- 用户刚入职 AI 行业、处于试用期或前 3 月（算法/研究、数据/ML 工程、AI 产品、AI 运营/增长、解决方案/售前等岗位）。
- 用户提到"AI 行业 landing / 落地 / 新人适应 / 试用期规划 / 前 3 周 / 前 3 月 / 刚入职怎么规划"。
- 用户表达 AI 行业新人的典型迷茫：怕实验跑不出结果、追不动新论文/新模型、研究 vs 落地撕扯、数学虚、不会用 AI 辅助研发、方向不清（做模型还是做产品）。

## 工作流

### 1. 开场
用 1-2 句直白说明：本 skill 会先聊几句现状（诊断），再给一份属于他自己的落地计划 + 清单。语气像朋友，不要 HR 手册腔。

### 2. 诊断
读取 `references/diagnosis.md`，按其中 6 个维度收集用户信息。使用 AskUserQuestion（每轮 1-3 个问题，分批，不一次轰炸）或自然语言对话收集。至少覆盖：身份、AI 行业环境、入职阶段、当前最卡的事（偏好 AI 行业专属痛点）、AI 辅助研发习惯。记录结果，用于定制计划重心。

### 3. 生成计划文档
读取 `references/landing-framework.md` 与 `references/ai-era-module.md`，结合诊断结果填充 `assets/plan-template.md` 的占位符，生成个性化 landing 计划文档。
- 框架用「前 3 周 / 前 3 月（第 1/2/3 月）」两阶段。
- 依据诊断痛点选择重点：痛点含"基础不牢" → 加重验证与防脆皮；含"方向迷茫" → 加重判断与方向复盘；AI 习惯弱 → 加重用 AI 搭基础设施。
- 用 Write 将文档写入用户工作区（如 `landing-plan.md`）。

### 4. 生成 checklist
基于计划填充 `assets/checklist-template.md`，生成可勾选清单，同样用 Write 写入工作区（如 `landing-checklist.md`）。

### 5. 交付
呈现两份文档，并给一句怎么用：计划文档回看、清单每天/每周勾选。

## 输出调性（重要）
所有面向用户的文字——包括诊断对话与两份交付物——采用「人话 + 有观点」风格：
- 像直白的资深朋友，敢给判断（如"靠谱比聪明值钱"），不写 HR 手册腔。
- 不堆术语；必要时用大白话解释。
- 允许有观点、有态度，但保持尊重与可操作。
SKILL.md 指令本身用祈使句（供另一个 WorkBuddy 实例消费），但产出的用户内容须符合上述调性。

## 文件引用
- `references/diagnosis.md`：诊断维度与问题。
- `references/landing-framework.md`：前 3 周 / 前 3 月框架与传统模块。
- `references/ai-era-module.md`：AI 时代加成模块。
- `assets/plan-template.md`：计划文档模板。
- `assets/checklist-template.md`：清单模板。
- `references/test-cases/`：可复用测试案例（含「校招入职 AI Agent 产品运营」样例及诊断脚本、验收标准），用于回归与演示。
