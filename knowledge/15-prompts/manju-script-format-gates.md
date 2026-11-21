# 漫剧剧本规格闸（手册第三节切片）

> 来源：AI漫剧实操手册（提示词）第三节  
> 领域：`ScriptFormatGate` / `DialogueHarshChecklist`（`ManjuPipeline.handbookOps`）

## 规格

- 每集 800–1200 字  
- 场景尽量 ≤3  
- 台词含旁白 ≤500  
- 场头：日/夜 · 内/外 · 地点 · 人物  
- 去小说化 → 分镜画面 + 台词  

## 台词狠（旁挂三层公式）

短促有力 · 带刺带钩 · 反差 · 证据甩脸 · 围观反应 · 快交锋  

## Agent

- `prose.storyboard`  
- `prose.dialogue_pressure`（可注入 harshChecklist）  
- `prose.dialogue_formula`（态度+信息+潜台词，不替换）  
