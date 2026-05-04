---
title: RAG 与 Wiki Pattern 对比
type: comparison
created: 2026-05-04
updated: 2026-05-04
tags: [llm, rag, wiki, knowledge-base, comparison]
sources: [llm-wiki.md]
---

RAG（检索增强生成）和LLM Wiki Pattern是两种不同的使用LLM处理文档的方式。本页面对比两者的核心差异、优劣势和适用场景。

## 核心差异

| 维度 | RAG | Wiki Pattern |
|------|-----|--------------|
| **知识处理** | 每次查询时从原始文档检索 | 增量构建，持久积累 |
| **交叉引用** | 每次查询时临时建立 | 预先建立并持续维护 |
| **矛盾处理** | 每次查询时可能重新发现 | 预先标记并记录 |
| **综合程度** | 每次查询时重新综合 | 预先综合，持续更新 |
| **维护成本** | 低（索引后基本无需维护） | 低（LLM承担维护） |

## RAG的工作方式

```
用户查询 → 检索相关文档片段 → LLM生成答案 → 完成
```

- 上传文件集合
- LLM在查询时检索相关片段
- 生成答案
- **无积累**——每次问题都像第一次阅读

## Wiki Pattern的工作方式

```
添加新源 → LLM阅读 → 提取关键信息 → 集成到现有wiki → 更新相关页面
                                              ↓
用户查询 → LLM搜索wiki → 综合已有答案 → 答案（可归档回wiki）
```

- LLM读取源文档，提取信息
- 增量整合到现有wiki
- 更新实体页、修订主题总结
- 标记矛盾、加强或挑战现有综合

## 优势对比

### RAG优势

- **低维护**：索引后基本无需维护
- **实时性**：新文档立即可检索
- **简单**：架构简单，易于设置

### Wiki Pattern优势

- **累积性**：知识随时间积累，不重复发现
- **深度综合**：能够 synthesizing five documents 所需知识已预先建立
- **矛盾追踪**：明确标记源之间的矛盾
- **交叉引用**：页面间的联系预先建立

## 典型应用场景

### RAG适合

- 大量文档的简单问答
- 需要实时索引新文档的场景
- 简单的事实查询

### Wiki Pattern适合

- 个人知识管理，跨时间积累
- 需要深度综合多个源的研究
- 需要追踪矛盾和演变的领域
- 需要维护实体间复杂关系的场景

## 关键洞察

> Most people's experience with LLMs and documents looks like RAG: you upload a collection of files, the LLM retrieves relevant chunks at query time, and generates an answer. This works, but the LLM is rediscovering knowledge from scratch on every question. There's no accumulation.

Wiki Pattern的核心洞察是：**知识应该被编译一次，然后保持最新，而不是每次查询时重新派生。**

## 相关页面

- [LLM Wiki Pattern](./llm-wiki-pattern.md) - 模式详细介绍