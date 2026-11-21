---
title: "漫剧剧本规格闸（手册第三节切片）"
project: "xiezuomanju"
source_path: "15-prompts/manju-script-format-gates.md"
category: "prompts"
kind: "prompts"
distilled: true
source_layer: raw
content_sha256: "1ece337beb7e84fd075c2e5bfd0fde5e8892480a7c41453de5da01bab3cb722c"
source_bytes: 671
usage: "internal-writing-assistance"
source_boundary: "retain attribution; verify rights before redistribution"
---
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
