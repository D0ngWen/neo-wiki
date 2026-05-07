---
title: 自动化漏洞挖掘：过去、现在与未来——AI 的上限在哪里？
type: summary
created: 2026-05-08
updated: 2026-05-08
tags: [security, AI, vulnerability-discovery]
sources: [自动化漏洞挖掘：过去、现在与未来——AI 的上限在哪里？.md]
---

本文系统梳理了 2022–2025 年间自动化漏洞挖掘的三次范式跃迁——从「LLM 做代码分类」到「LLM 辅助传统工具」再到「Agent 主导的自动化审计」，帮助读者理解范式转换的规律，做出能够跨越范式的研究与工程决策。

## 前 LLM 时代的自动化漏洞挖掘

在 LLM 出现之前，主要依赖以下技术路线：

- **Fuzzing**：擅长内存安全，但止步于逻辑漏洞
- **污点分析**：强于规则覆盖，困于规则边界
- **符号执行与形式化验证**：理论优雅，实践受限

理想的自动化漏洞挖掘系统应具备四个特质：通用性、自动化、低误报、低漏报。前 LLM 时代这四个目标几乎不可兼得。

## 三次范式跃迁

### 2022 年：代码分类范式
- LLM 以 BERT 系列为主，上下文窗口有限，缺乏真正推理能力
- 代表性工作：Thapa 等人的 Transformer-Based Language Models for Software Vulnerability Detection
- 2022 年 11 月 30 日 ChatGPT 发布，成为历史转折点

### 2023 年：识别 LLM 能力边界
- LLM 展现三个核心能力：世界知识、代码片段理解、有限复杂度的代码生成与迭代修复
- 成功的方向：
  - 利用代码生成能力增强 Fuzzing（Google OSS-Fuzz 的 AI-Powered Fuzzing）
  - 利用世界知识和代码理解辅助静态分析（LATTE、GPTScan）
- 核心教训：成功与否取决于是否正确识别了 LLM 的能力边界

### 2024-2025 年：Agent 时代
- 2024 年 LLM 的关键变化：上下文窗口大幅扩展、推理能力显著增强、代码生成能力提升、Agent 框架快速发展
- 2025 年 Agentic 代码审计成为主流方向
- 代表性工作：Google Project Zero 的 Project Naptime、Big Sleep
- 核心洞察：执行变得廉价，知识才是真正的瓶颈

## 未来展望

- **短期**：Agent 编排仍是高杠杆方向
- **长期**：持续学习将重塑 Agent 范式
- **AI 的上限**：当前局限是上下文理解深度和领域知识稀缺，但这些都是技术障碍而非原理性限制

## 相关概念

- [自动化漏洞挖掘](../concept/automated-vuln-discovery.md)
- [Agent 审计](../concept/agentic-audit.md)
