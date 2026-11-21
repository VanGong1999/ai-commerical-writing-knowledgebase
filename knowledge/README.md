# 写作领域知识库（Knowledge）

> 供产品检索与 Agents 引用的**结构化蒸馏文**。源课在 `写作课程录音稿1/`，本目录**禁止**整篇粘贴录音稿。

## 分类说明

| 目录 | 主题 |
|------|------|
| `01-ai-collab/` | AI协作/提示词/任务拆解/去AI味 |
| `02-manju/` | 漫剧工业流程/投稿/规格 |
| `03-duanju/` | 短剧（查理） |
| `04-webnovel/` | 网文长篇/零基础/狂更猫/红娘子/迷蒙相关网文法 |
| `05-character/` | 人设 |
| `06-structure/` | 大纲/节拍/开篇/伏笔 |
| `07-emotion-cool/` | 情绪/爽点/打脸/期待冲突 |
| `08-swap-imitate/` | 换元/仿写/洗稿边界 |
| `09-quality/` | 质检/改稿/代入感 |
| `10-ops-monetize/` | 运营变现/平台/带货/账号 |
| `11-ip-adapt/` | IP改编 |
| `12-female-long/` | 女频 |
| `13-short-fiction/` | 短篇商业/知乎故事 |
| `14-story-craft/` | 故事底层（哈佛/十五步/编剧孵化/北大） |
| `15-prompts/` | Prompt 资产索引 |
| `16-male-long/` | 男频中长篇（升级循环/打脸/金手指/雷区） |

| `00-meta/` | 来源映射、去重矩阵、覆盖清单、检索索引 |

**文章总数（含 15-prompts 索引文）：113**

## 检索索引

- 元数据索引（不重复正文）：[`00-meta/search-index.json`](00-meta/search-index.json)（当前 **109** 条）
- 本地关键词检索 API（`packages/kb-core`，无向量依赖）：
  - `load_knowledge_index()` / `loadKnowledgeIndex()`
  - `search_knowledge(query, opts?)` / `searchKnowledge(...)` — `opts`: `{ category?, limit? }`
- 生成/校验：`node scripts/build-knowledge-index.mjs`（加 `--check` 仅校验）

```python
from kb_core import search_knowledge
hits = search_knowledge("拉片", {"category": "03-duanju", "limit": 5})
```

## 去重原则（权威源）

| 主题 | 权威源 |
|------|--------|
| 漫剧 / 换元 / 去AI味 / 核心梗 | **九格** |
| 短剧选题 / 节拍 / 场 / 付费 | **查理短剧课** |
| 故事底层 15 步 / 编剧 | **查理十五步 + 编剧孵化营** |
| 网文人设 / 大纲 / 爽点实操 | **零基础班 + 狂更猫**（文内标双源） |
| 商业内容 / 账号运营 | **知乎短篇创作营 + 短视频商业训练营** |
| 故事变现理论 | **北大博士故事变现 + 哈佛故事课** |

详见 [`00-meta/dedup-matrix.md`](00-meta/dedup-matrix.md)。

## 与 Skills / Agents 关系

- Skills 落在 `packages/agent-runtime/skills/`；本文头字段「关联 Skills / Agents」对齐 `docs/agents/`。
- 编排：`WritingOrchestrator`；漫剧核心：`CoreHookAgent` + `de-ai-v3.8`；短剧门禁：`Beat20` / `SceneTriple` / `Revise20` / `GenderPath`。
- Prompt 超长原文不入库：见 [`15-prompts/`](15-prompts/)，指向手册与 `prompt-registry`。

## 完整索引表

| 分类 | 文件 | 标题 | 权威 |
|------|------|------|------|
| 01-ai-collab | [charlie-ai-efficiency.md](01-ai-collab/charlie-ai-efficiency.md) | 查理 AI 效率：场景扇出与可视化 | P0 九格为主 |
| 01-ai-collab | [commercial-writing-workflow.md](01-ai-collab/commercial-writing-workflow.md) | 商业文章 AI 创作工作流 | P0 九格为主 |
| 01-ai-collab | [core-hook-batch.md](01-ai-collab/core-hook-batch.md) | 核心梗批量生成与筛选 | P0 九格为主 |
| 01-ai-collab | [de-ai-v38-method.md](01-ai-collab/de-ai-v38-method.md) | 去 AI 味 V3.8 方法总览 | P0 九格为主 |
| 01-ai-collab | [dissect-params.md](01-ai-collab/dissect-params.md) | 拆书参数（参数化对标） | P0 九格为主 |
| 01-ai-collab | [prompt-rules-and-task-split.md](01-ai-collab/prompt-rules-and-task-split.md) | 提示词本质与任务拆解 | P0 九格为主 |
| 01-ai-collab | [zhihu-ai-story.md](01-ai-collab/zhihu-ai-story.md) | 知乎营 AI 创作专题要点 | P0 九格为主 |
| 02-manju | [episode-outline-and-script.md](02-manju/episode-outline-and-script.md) | 分集大纲与分镜剧本规范 | P0 九格 |
| 02-manju | [manju-core-hook-format.md](02-manju/manju-core-hook-format.md) | 漫剧核心梗输出格式 | P0 九格 |
| 02-manju | [manju-full-pipeline.md](02-manju/manju-full-pipeline.md) | AI 漫剧全流程 SOP | P0 九格 |
| 02-manju | [manju-manual-qc.md](02-manju/manju-manual-qc.md) | 漫剧人工校稿六项 | P0 九格 |
| 02-manju | [manju-market-genre.md](02-manju/manju-market-genre.md) | 漫剧题材与市场取向 | P0 九格 |
| 02-manju | [manju-submission-pack.md](02-manju/manju-submission-pack.md) | 漫剧交付与过稿注意 | P0 九格 |
| 02-manju | [jiuge-market-platform.md](02-manju/jiuge-market-platform.md) | 漫剧市场、平台生态与投稿规范 | P0 九格 |
| 02-manju | [jiuge-corehook-goldfinger.md](02-manju/jiuge-corehook-goldfinger.md) | 漫剧核心方法论：故事梗/金手指/世界观/题材 | P0 九格 |
| 02-manju | [jiuge-manju-advanced.md](02-manju/jiuge-manju-advanced.md) | 漫剧进阶：核心梗四步法、四幕结构与题材红线 | P0 九格 |
| 02-manju | [jiuge-manju-ai-workflow.md](02-manju/jiuge-manju-ai-workflow.md) | 漫剧 AI 实操工作流与新人成长路径 | P0 九格 |
| 03-duanju | [beat20.md](03-duanju/beat20.md) | 二十节拍大纲 | P0 查理短剧 |
| 03-duanju | [bridge8-and-witness.md](03-duanju/bridge8-and-witness.md) | 八桥段与两性见证放大器 | P0 查理短剧 |
| 03-duanju | [five-cool-points.md](03-duanju/five-cool-points.md) | 短剧五大爽点 | P0 查理短剧 |
| 03-duanju | [product-mindset.md](03-duanju/product-mindset.md) | 短剧产品思维：解压·代入·粘度 | P0 查理短剧 |
| 03-duanju | [resonance-and-shells.md](03-duanju/resonance-and-shells.md) | 共鸣 YY 与故事壳 | P0 查理短剧 |
| 03-duanju | [revise20-gender-deliver.md](03-duanju/revise20-gender-deliver.md) | 修改20·男女频路径·交付八规范 | P0 查理短剧 |
| 03-duanju | [scene-dialogue-hooks.md](03-duanju/scene-dialogue-hooks.md) | 场三件事·台词·悬念一加一 | P0 查理短剧 |
| 03-duanju | [topic-formula.md](03-duanju/topic-formula.md) | 短剧选题三公式 | P0 查理短剧 |
| 03-duanju | [lapian-principles.md](03-duanju/lapian-principles.md) | 短剧拉片原则（个案方法论） | P0 查理短剧 |
| 03-duanju | [charlie-ops-index.md](03-duanju/charlie-ops-index.md) | 查理 Ops：Stage↔面板↔Agent | P0 查理短剧 |
| 04-webnovel | [emotion-line-and-perspective.md](04-webnovel/emotion-line-and-perspective.md) | 感情线与视角 | P0 零基础+狂更猫 |
| 04-webnovel | [hotsales-dissect-method.md](04-webnovel/hotsales-dissect-method.md) | 零基础高阶：热销拆解方法论 | P0 零基础+狂更猫 |
| 04-webnovel | [gold-finger-and-loop.md](04-webnovel/gold-finger-and-loop.md) | 金手指与循环写法 | P0 零基础+狂更猫 |
| 04-webnovel | [innovation-and-dissect.md](04-webnovel/innovation-and-dissect.md) | 微创新、反套路与拆爆款 | P0 零基础+狂更猫 |
| 04-webnovel | [opening-attract.md](04-webnovel/opening-attract.md) | 吸引力开篇：冲突·悬念·设定 | P0 零基础+狂更猫 |
| 04-webnovel | [outline-hierarchy.md](04-webnovel/outline-hierarchy.md) | 草纲到细纲的层级 | P0 零基础+狂更猫 |
| 04-webnovel | [scan-rank-and-platform.md](04-webnovel/scan-rank-and-platform.md) | 刷榜、平台气质与选题顺序 | P0 零基础+狂更猫 |
| 04-webnovel | [six-standards-and-mindset.md](04-webnovel/six-standards-and-mindset.md) | 网文赚钱六标准与认知 | P0 零基础+狂更猫 |
| 04-webnovel | [title-blurb-stuck.md](04-webnovel/title-blurb-stuck.md) | 书名简介与破卡文 | P0 零基础+狂更猫 |
| 04-webnovel | [xiezuo2-pearl-and-twist.md](04-webnovel/xiezuo2-pearl-and-twist.md) | 珍珠项链结构与反转层次（写作课程2） | P0 零基础+狂更猫 |
| 04-webnovel | [jiuge-inspiration-to-story.md](04-webnovel/jiuge-inspiration-to-story.md) | 从灵感到故事：四层级模型与扩展路径 | P0 九格 |
| 05-character | [antagonist-and-cast.md](05-character/antagonist-and-cast.md) | 对手、配角与群像控制 | P0 混源 |
| 05-character | [bible-and-big5.md](05-character/bible-and-big5.md) | 人设清单与立体角色 | P0 混源 |
| 05-character | [dialogue-voice.md](05-character/dialogue-voice.md) | 对话与角色声线 | P0 混源 |
| 05-character | [empathy-three.md](05-character/empathy-three.md) | 共情三招：可怜可信可爱 | P0 混源 |
| 05-character | [soul-check.md](05-character/soul-check.md) | 灵魂拷问：情节是否符合人设 | P0 混源 |
| 05-character | [xiezuo2-character-tricks.md](05-character/xiezuo2-character-tricks.md) | 人设五技巧与行为逻辑 | P0 混源 |
| 05-character | [jiuge-character-depth.md](05-character/jiuge-character-depth.md) | 人设深度：大五人格/欲望恐惧秘密/差异化人设 | P0 九格 |
| 06-structure | [conflict-expectation.md](06-structure/conflict-expectation.md) | 期待感与冲突设计 | P0 混源 |
| 06-structure | [foreshadow-setup-climax.md](06-structure/foreshadow-setup-climax.md) | 伏笔、铺垫与高潮 | P0 混源 |
| 06-structure | [midpoint-dark-night.md](06-structure/midpoint-dark-night.md) | 故事中点与至暗时刻 | P0 混源 |
| 06-structure | [opening-hooks-catalog.md](06-structure/opening-hooks-catalog.md) | 开篇钩子手法目录 | P0 混源 |
| 06-structure | [seven-step-unit.md](06-structure/seven-step-unit.md) | 七步法单元故事 | P0 混源 |
| 06-structure | [transitions-and-unit-arc.md](06-structure/transitions-and-unit-arc.md) | 转场、单元弧与章回体 | P0 混源 |
| 06-structure | [fifteen-vs-beat20.md](06-structure/fifteen-vs-beat20.md) | 查理十五步 ↔ Beat20 对照表 | P0 混源 |
| 07-emotion-cool | [cool12-maslow.md](07-emotion-cool/cool12-maslow.md) | 十二类爽点与需求层次 | P0 混源 |
| 07-emotion-cool | [emotion-density.md](07-emotion-cool/emotion-density.md) | 情绪节奏与章级密度 | P0 混源 |
| 07-emotion-cool | [face-slap.md](07-emotion-cool/face-slap.md) | 打脸与对比爽感 | P0 混源 |
| 07-emotion-cool | [pressure-relief.md](07-emotion-cool/pressure-relief.md) | 解压优先与爽感伦理 | P0 混源 |
| 07-emotion-cool | [suspense-info-gap.md](07-emotion-cool/suspense-info-gap.md) | 悬念、信息差与超预期兑现 | P0 混源 |
| 08-swap-imitate | [female-four-swap-three.md](08-swap-imitate/female-four-swap-three.md) | 女频四换三（狂更猫） | P0 九格 |
| 08-swap-imitate | [once-twice-swap.md](08-swap-imitate/once-twice-swap.md) | 一度与二度换元实操 | P0 九格 |
| 08-swap-imitate | [six-story-sources.md](08-swap-imitate/six-story-sources.md) | 换元法六大故事源 | P0 九格 |
| 08-swap-imitate | [wash-vs-imitate-boundary.md](08-swap-imitate/wash-vs-imitate-boundary.md) | 洗稿、仿节奏与合规边界 | P0 九格 |
| 09-quality | [de-ai-qc-checklist.md](09-quality/de-ai-qc-checklist.md) | 去 AI 味质检清单 | P0 九格+查理 |
| 09-quality | [immersion-qc.md](09-quality/immersion-qc.md) | 代入感与情绪质检 | P0 九格+查理 |
| 09-quality | [precise-prose.md](09-quality/precise-prose.md) | 精准文笔与信息密度 | P0 九格+查理 |
| 09-quality | [revise20-and-logic.md](09-quality/revise20-and-logic.md) | 改稿：修改20与逻辑确认 | P0 九格+查理 |
| 09-quality | [show-dont-tell.md](09-quality/show-dont-tell.md) | 展示而非告知（去说明腔） | P0 九格+查理 |
| 09-quality | [jiuge-visual-sense.md](09-quality/jiuge-visual-sense.md) | 画面感与五觉法：把文字改出画面 | P0 九格 |
| 09-quality | [jiuge-redline-policy.md](09-quality/jiuge-redline-policy.md) | 写作红线、平台政策与雷区规避 | P0 九格 |
| 10-ops-monetize | [beida-monetize-paths.md](10-ops-monetize/beida-monetize-paths.md) | 故事变现路径图谱 | P0 知乎+短视频+北大/迷蒙 |
| 10-ops-monetize | [hongniangzi-submit.md](10-ops-monetize/hongniangzi-submit.md) | 投稿心法与体裁变现 | P0 知乎+短视频+北大/迷蒙 |
| 10-ops-monetize | [mimeng-viral-pipeline.md](10-ops-monetize/mimeng-viral-pipeline.md) | 迷蒙爆款流水线与变现七途 | P0 知乎+短视频+北大/迷蒙 |
| 10-ops-monetize | [shortvideo-nine-ways.md](10-ops-monetize/shortvideo-nine-ways.md) | 抖音变现九种方式 | P0 知乎+短视频+北大/迷蒙 |
| 10-ops-monetize | [shortvideo-triangle.md](10-ops-monetize/shortvideo-triangle.md) | 短视频三角定位与需求三级 | P0 知乎+短视频+北大/迷蒙 |
| 10-ops-monetize | [zhihu-account-and-ops.md](10-ops-monetize/zhihu-account-and-ops.md) | 账号价值、选题与全媒体运营 | P0 知乎+短视频+北大/迷蒙 |
| 10-ops-monetize | [zhihu-commercial-templates.md](10-ops-monetize/zhihu-commercial-templates.md) | 知乎商业内容三模板与卖点 | P0 知乎+短视频+北大/迷蒙 |
| 10-ops-monetize | [jiuge-newcomer-path.md](10-ops-monetize/jiuge-newcomer-path.md) | 新人入行路径、心态与平台分层 | P0 九格 |
| 10-ops-monetize | [fanqie-platform-rules.md](10-ops-monetize/fanqie-platform-rules.md) | 番茄/网文平台规则速查库（狂更猫 58 条待核实口径） | P0 狂更猫 |
| 11-ip-adapt | [brand-story-modes.md](11-ip-adapt/brand-story-modes.md) | 品牌故事五种正面模式 | P0 九格 |
| 11-ip-adapt | [jiuge-ip-adapt.md](11-ip-adapt/jiuge-ip-adapt.md) | IP 改编方法论（九格） | P0 九格 |
| 11-ip-adapt | [novel-to-manju.md](11-ip-adapt/novel-to-manju.md) | 网文改漫剧要点 | P0 九格 |
| 11-ip-adapt | [screen-adapt-checklist.md](11-ip-adapt/screen-adapt-checklist.md) | 影视向改编检查单 | P0 九格 |
| 11-ip-adapt | [xiezuo1-pilot-structure.md](11-ip-adapt/xiezuo1-pilot-structure.md) | 一小时试播集结构法（四原型+四幕） | P1 写作课程1 |
| 12-female-long | [chase-wife-template.md](12-female-long/chase-wife-template.md) | 追妻火葬场模板 | P0 九格+狂更猫 |
| 12-female-long | [female-emotion-romance.md](12-female-long/female-emotion-romance.md) | 女频情绪与爱情套路 | P0 九格+狂更猫 |
| 12-female-long | [female-opening-five.md](12-female-long/female-opening-five.md) | 女频开篇五要素与前三章 | P0 九格+狂更猫 |
| 12-female-long | [female-pace.md](12-female-long/female-pace.md) | 女频长篇节奏 | P0 九格+狂更猫 |
| 12-female-long | [jiuge-female-track-monetize.md](12-female-long/jiuge-female-track-monetize.md) | 女频赛道拆解、平台签约与变现适配 | P0 九格 |
| 13-short-fiction | [commercial-storytelling.md](13-short-fiction/commercial-storytelling.md) | 故事化商业写作 | P0 知乎+红娘子 |
| 13-short-fiction | [newmedia-formula.md](13-short-fiction/newmedia-formula.md) | 新媒体爆款公式 | P0 知乎+红娘子 |
| 13-short-fiction | [short-hotspot-fast.md](13-short-fiction/short-hotspot-fast.md) | 短篇热点快投法 | P0 知乎+红娘子 |
| 13-short-fiction | [zero-practice-short-long.md](13-short-fiction/zero-practice-short-long.md) | 0基础实战：短篇与长篇衔接 | P0 知乎+红娘子 |
| 13-short-fiction | [zhihu-short-structure.md](13-short-fiction/zhihu-short-structure.md) | 知乎短篇结构与爆款开篇 | P0 知乎+红娘子 |
| 13-short-fiction | [zhihu-story-topics.md](13-short-fiction/zhihu-story-topics.md) | 知乎06故事专题精华（合并） | P0 知乎+红娘子 |
| 13-short-fiction | [jiuge-topic-selection.md](13-short-fiction/jiuge-topic-selection.md) | 短篇选题：扒榜/老梗缝合/热点落地/受众定位 | P0 九格 |
| 13-short-fiction | [jiuge-topic-avoidance.md](13-short-fiction/jiuge-topic-avoidance.md) | 短篇选题避坑与平台政策/写作禁忌 | P0 九格 |
| 14-story-craft | [ctfdp-and-one-liner.md](14-story-craft/ctfdp-and-one-liner.md) | CTFDP 与一句话故事 | P0 查理+北大+哈佛 |
| 14-story-craft | [fifteen-elements-ab.md](14-story-craft/fifteen-elements-ab.md) | 十五元素与 AB 故事 | P0 查理+北大+哈佛 |
| 14-story-craft | [fifteen-steps.md](14-story-craft/fifteen-steps.md) | 十五步写出好故事 | P0 查理+北大+哈佛 |
| 14-story-craft | [four-act-beats.md](14-story-craft/four-act-beats.md) | 四幕式节拍表 | P0 查理+北大+哈佛 |
| 14-story-craft | [genre-ten-types.md](14-story-craft/genre-ten-types.md) | 类型片十大共情点 | P0 查理+北大+哈佛 |
| 14-story-craft | [harvard-trust-and-public-narrative.md](14-story-craft/harvard-trust-and-public-narrative.md) | 故事建立信任与公共叙事三段论 | P0 查理+北大+哈佛 |
| 14-story-craft | [story-equals-accident.md](14-story-craft/story-equals-accident.md) | 故事=意外（北大博士） | P0 查理+北大+哈佛 |
| 15-prompts | [README.md](15-prompts/README.md) | Prompt 资产索引 | P0 九格索引 |
| 15-prompts | [core-hook-prompt-usage.md](15-prompts/core-hook-prompt-usage.md) | 核心梗批产 Prompt 用法 | P0 九格索引 |
| 15-prompts | [de-ai-prompt-usage.md](15-prompts/de-ai-prompt-usage.md) | 去 AI 味 Prompt 用法 | P0 九格索引 |
| 15-prompts | [manju-handbook-index.md](15-prompts/manju-handbook-index.md) | AI漫剧实操手册提示词索引 | P0 九格索引 |
| 15-prompts | [swap-prompt-usage.md](15-prompts/swap-prompt-usage.md) | 换元法 Prompt 用法 | P0 九格索引 |
| 15-prompts | [manju-cool18-kartian.md](15-prompts/manju-cool18-kartian.md) | 漫剧十八爽点 + 卡点三类（手册干货切片） | P0 九格索引 |
| 15-prompts | [manju-script-format-gates.md](15-prompts/manju-script-format-gates.md) | 漫剧剧本规格闸（手册第三节切片） | P0 九格索引 |
| 16-male-long | [upgrade-loop.md](16-male-long/upgrade-loop.md) | 男频升级流循环 | P0 狂更猫+零基础 |
| 16-male-long | [cool-face-slap.md](16-male-long/cool-face-slap.md) | 男频爽点密度与装逼打脸 | P0 狂更猫+九格+零基础 |
| 16-male-long | [gold-finger-male.md](16-male-long/gold-finger-male.md) | 男频金手指限制与推进 | P0 狂更猫+零基础 |
| 16-male-long | [male-risk-and-scan.md](16-male-long/male-risk-and-scan.md) | 男频雷区与扫榜体检 | P0 狂更猫+零基础 |

## 各分类篇数

| 分类 | 篇数 |
|------|------|
| 01-ai-collab | 7 |
| 02-manju | 10 |
| 03-duanju | 10 |
| 04-webnovel | 11 |
| 05-character | 7 |
| 06-structure | 7 |
| 07-emotion-cool | 5 |
| 08-swap-imitate | 4 |
| 09-quality | 7 |
| 10-ops-monetize | 9 |
| 11-ip-adapt | 5 |
| 12-female-long | 5 |
| 13-short-fiction | 8 |
| 14-story-craft | 7 |
| 15-prompts | 7 |
| 16-male-long | 4 |
| **合计** | **113** |

## 维护约定

1. 新增课源先更新 `00-meta/sources-map.md` 与 `dedup-matrix.md`，再写蒸馏文。
2. 与权威源冲突时：改非权威文的「与其他课差异」，不改权威结论。
3. 市场热度类结论标注「以当期渠道为准」。
4. 不修改 `packages/` 业务代码完成本库维护。
