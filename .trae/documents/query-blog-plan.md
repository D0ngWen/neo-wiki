# 计划：使用 Query 流程生成项目搭建博客

## 目标

通过 Query 流程向 Agent 提问，合成一篇关于搭建本项目的博客文章，输出到 `co work/` 目录。

## 前置准备

### 1. 确认目录结构

* 创建输出目录：`d:\文档\neo_wiki\co work\`

* 确保 wiki 内容已准备好被查询

### 2. 确定博客内容要点

根据现有 wiki 内容，博客应覆盖：

1. **项目概述**：什么是 LLM Wiki Pattern
2. **核心价值**：为什么用这个模式（持久化积累 vs 每次查询重新检索）
3. **目录结构**：

   * `raw/`：不可变的源文档

   * `wiki/`：LLM 生成的维基页面

   * `AGENTS.md`：Agent 操作规范
4. **核心操作流程**：

   * Ingest：从源文档到 wiki 页面的摄入流程

   * Query：提问和综合答案

   * Lint：定期健康检查
5. **工具栈**：Trae IDE + Trae Agent
6. **搭建步骤**：如何初始化项目

## 执行步骤

### Step 1：创建输出目录

```
创建 d:\文档\neo_wiki\co work\
```

### Step 2：发起 Query 提问

向 Agent 提问（模拟 /query 流程）：

> "请根据本 wiki 的内容，写一篇关于如何搭建 LLM Wiki Pattern 项目的博客。需要包括：项目介绍、核心价值、三层架构、目录结构、核心操作流程（Ingest/Query/Lint）、以及使用 Trae IDE 和 Trae Agent 的搭建步骤。"

### Step 3：Agent 综合 wiki 内容

Agent 读取：

* [wiki/README.md](d:\文档\neo_wiki\wiki\README.md)

* [wiki/summary/llm-wiki.md](d:\文档\neo_wiki\wiki\summary\llm-wiki.md)

* [wiki/concept/llm-wiki-pattern.md](d:\文档\neo_wiki\wiki\concept\llm-wiki-pattern.md)

* [wiki/concept/rag-comparison.md](d:\文档\neo_wiki\wiki\concept\rag-comparison.md)

* [AGENTS.md](d:\文档\neo_wiki\AGENTS.md)

综合生成博客内容。

### Step 4：输出博客文件

将博客保存到 `d:\文档\neo_wiki\co work\搭建LLM-Wiki-Pattern项目博客.md`

博客文件应包含：

* YAML frontmatter（title, date, tags）

* 完整的博客正文

* 引用 wiki 页面的交叉链接

## 博客大纲

```markdown
---
title: 使用 Trae Agent 构建个人 LLM Wiki 知识库
date: 2026-05-04
tags: [llm, wiki, knowledge-base, trae, 知识管理]
---

# 使用 Trae Agent 构建个人 LLM Wiki 知识库

## 引言
## 什么是 LLM Wiki Pattern
## 核心价值：持久化积累 vs 临时检索
## 项目架构
### 三层架构
### 目录结构
### 核心文件说明
## 快速开始
### 1. 初始化项目
### 2. 摄入源文档 (Ingest)
### 3. 提问与综合 (Query)
### 4. 健康检查 (Lint)
## 使用 Trae IDE 浏览 wiki
## 总结
```

## 预期输出

* 文件：`d:\文档\neo_wiki\co work\搭建LLM-Wiki-Pattern项目博客.md`

* 格式：标准 Markdown，包含 frontmatter

* 内容：完整涵盖项目搭建流程

