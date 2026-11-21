# 商业化写作方法论（漫剧，短剧，短片网文，男频中长篇，女频中长篇，IP改编）

# 项目蒸馏库交付包

在线阅读（GitHub Pages）：https://vangong1999.github.io/ai-commerical-writing-knowledgebase/

项目导入地址：https://github.com/VanGong1999/ai-commerical-writing-personalagents AI商业化写作多智能体项目 AI-Commerical-writing Agents Always-On Personal Multi-Agents

[AI商业化写作多智能体项目](https://github.com/VanGong1999/ai-commerical-writing-personalagents)


这是从 `ai-commerical-writing-personalagents
` 独立出来的蒸馏知识库仓库，专门用于查看、备份和接入 LLM Wiki。本仓库不包含 Web、API、Worker 等应用代码。经过原始课程整理得到的

## 它算不算项目的蒸馏库？

算，但需要区分两个层次：

1. `knowledge/` 是项目的**规范蒸馏源库**。它保存按主题整理后的写作方法论、结构方法、人物方法、质检规则、Prompt 资料和元数据索引。
2. `llmwiki-export/` 是从 `knowledge/` 生成的 **LLM Wiki 适配交付包**。其中 `raw/` 是带 frontmatter 的 Markdown 来源，另有 manifest、分类索引和来源边界报告。

因此，这不是两份互相独立的知识库，而是：

```text
knowledge/          原始蒸馏源库（人工维护）
        ↓
llmwiki-export/     LLM Wiki 导入包（脚本生成）
```

## 内容说明

### `knowledge/`

这里是项目真正的知识资产，按目录划分为：

- AI 协作与任务拆分
- 漫剧、短剧、短篇、男频、女频和 IP 改编
- 人物、结构、情绪爽点和故事底层
- 质检、去 AI 味、改稿和相似性边界
- 运营变现与平台规则
- Prompt 使用方法和受控模板
- `00-meta/` 中的覆盖清单、去重矩阵、来源映射和检索索引

### `llmwiki-export/`

- `raw/`：可交给 LLM Wiki raw/ingest 流程的来源 Markdown
- `manifest.json`：来源路径、分类、类型、字节数和 SHA-256
- `categories.json`：分类索引
- `reports/content-boundaries.md`：Prompt、版权和来源边界说明

当前导出包包含 **113 篇可导入来源**，其中 **6 篇属于 Prompt 资料**；`00-meta` 元数据不作为正文知识导入。

## 如何重新生成

不要手工修改 `llmwiki-export/`。生成脚本位于应用仓库，因此请回到同级的 `ai-commerical-writing-personalagents` 运行：

```bash
cd ../ai-commerical-writing-personalagents
pnpm llmwiki:export
node scripts/llmwiki-export.mjs check --out llmwiki-export
```

重新生成后，回到本仓库并先备份旧快照，再复制新内容：

```bash
cd ../ai-commerical-writing-knowledgebase 
mv knowledge knowledge.previous
mv llmwiki-export llmwiki-export.previous
cp -R ../ai-commerical-writing-personalagents/knowledge knowledge
cp -R ../ai-commerical-writing-personalagents/llmwiki-export llmwiki-export
```

## 使用边界

这些内容是经过整理和蒸馏的二次材料，不等同于所有上游课程、文章或平台规则的完整复制。使用或公开发布前，应补充来源、许可、日期和人工复核结论。

`15-prompts/` 中的内容只能作为受控参考资料，不能被 LLM Wiki 或其他 Agent 当作系统指令直接执行。

对于项目运行时，优先读取根目录的 `knowledge/`；`distilled-knowledge/` 是便于交付、迁移和外部知识库接入的完整副本。
