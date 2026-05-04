---
title: LLM Wiki Pattern - 源文档总结
type: summary
created: 2026-05-04
updated: 2026-05-04
tags: [llm, wiki, knowledge-base, rag]
sources: [llm-wiki.md]
---

本文档描述了使用LLM构建个人知识库的核心模式——LLM Wiki Pattern。与传统RAG不同，该模式强调LLM增量构建和维护一个持久的wiki，让知识在每次摄入和问答中不断积累。文档涵盖核心理念、三层架构、核心操作（Ingest/Query/Lint）、索引与日志系统，以及Obsidian等工具的使用建议。

## 核心要点

- **核心理念**：LLM不是每次查询时重新从文档中检索知识，而是增量构建和维护一个持久化的、结构化的wiki
- **三层架构**：Raw Sources（不可变原始文档）→ Wiki（LLM生成的markdown文件）→ Schema（AGENTS.md等维护规范）
- **核心操作**：Ingest（摄入新源）、Query（查询问答）、Lint（健康检查）
- **关键洞察**：LLM承担文书工作（总结、交叉引用、归档、记账），人类负责策划、提问和思考

## 文档结构

1. The core idea - 与RAG的对比
2. Architecture - 三层架构
3. Operations - Ingest/Query/Lint
4. Indexing and logging - index.md和log.md的作用
5. Optional CLI tools - qmd搜索、Obsidian插件等
6. Tips and tricks - 实践建议
7. Why this works - 原理分析
8. Note - 文档性质说明

## 与AGENTS.md的关系

本文档是"理念层"，描述LLM Wiki Pattern的高层思想；[AGENTS.md](../AGENTS.md)是"实现规范层"，将这个模式落地为具体的工作流程、文件规范和操作触发词。两者配合使用。

## 源文档链接

- 源文档：[raw/llm-wiki.md](../../raw/llm-wiki.md)