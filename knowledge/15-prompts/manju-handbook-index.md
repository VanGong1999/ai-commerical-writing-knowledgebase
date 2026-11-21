# AI漫剧实操手册提示词索引
> 来源：九格 / 文件资料/AI漫剧实操手册（提示词）.md
> 权威级别：P0
> 关联 Skills：manju.*
> 关联 Agents：CoreHookAgent, WritingOrchestrator
> 领域：`ManjuPipeline.handbookOps` + `EpisodeOutlineBody` 爽卡字段 + `PitchPackBody`

## 一句话
手册按阶段提供：核心梗、大纲、单集、校正、扩纲、小传等提示词；使用时只抽当前阶段段。产品中间态见 Pipeline「手册SOP」Tab，不另建 Stage。

## 六段 ↔ Stage / Agent

| 段 | 产品落点 | Agent / Prompt |
|----|----------|----------------|
| 一核心梗 | HookPanel 七字段 + marketGenreAck | `topic.core_hook_batch` / `manju.hook.batch` |
| 二十集纲 | OutlinePanel 爽\|卡\|能不能用 | `struct.episode_outline` / cool18 / kartian |
| 三正文分镜台词 | scriptFormatGate + dialogueHarsh | `prose.storyboard` / dialogue_* |
| 四扩纲 | extendForm inputJson | `struct.extend_outline` |
| 五大纲小传 | PitchPackWorkbench | `deliver.pitch_pack` |
| 六干货 | `MANJU_COOL18` / Kartian 常量 | 见 `manju-cool18-kartian.md` |

## 核心要点（条目）
- 标蓝/可编辑部分按市场与自身优势改。
- 表格转文字后必须核对（ep10TableAccept）。
- 扩纲提示词需含：核心梗+已有大纲+需求+参考案例。
- 强采纳核心梗：动机+开篇+标签+危机。

## 可执行清单 / 模板
- 打开手册 → 定位阶段标题 → 复制该段 → 填可变槽 → 跑模型 → 人工验收。
- 或在 Studio 手册SOP Tab 勾中间态后调对应 Agent。

## 反模式
- 整手册塞进一次上下文。
- 用错阶段提示词（用正文提示词扩纲）。
- 新建第二套 HandbookWorkflow / 与 L6 cool12 混用。

## 与其他课差异（若有）
- L11/16：流程与考拉权威；本 SOP 补产物字段与人工能不能用。
- L17：百集四幕/开场九型；不挡前十投稿。
- L6：打脸三阶/cool12；十八模型独立。
