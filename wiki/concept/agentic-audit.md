---
title: Agent 审计
type: concept
created: 2026-05-08
updated: 2026-05-08
tags: [security, AI, agent]
sources: [自动化漏洞挖掘：过去、现在与未来——AI 的上限在哪里？.md]
---

Agent 审计是 2024-2025 年确立的新范式，LLM 作为自主审计员，调用工具、验证假设、迭代分析，完成完整的审计流程由 LLM 驱动。

## 历史演进

### 2024 年：先声
- Google Project Zero 的 Project Naptime（2024 年 6 月）：为 LLM 配备代码浏览、Python 沙箱和调试器作为工具
- From Naptime to Big Sleep（2024 年 10 月）：发现了可利用的 SQLite 栈下溢漏洞

### 2025 年：主流化
工业界全面拥抱 Agentic 审计：
- Anthropic 发布 Automated Security Reviews with Claude Code
- Snyk 发布 Human + AI: The Next Era of Snyk's Vulnerability Curation
- OpenAI 发布 Aardvark

## Agent 审计的核心特点

- **LLM 作为自主审计员**：不是被动的分类器，不是传统工具的辅助，而是主动探索、形成假设、验证假设的智能体
- **工具调用**：LLM 负责提出假设与决策，fuzzer、静态分析器、符号执行器等作为可调用工具
- **迭代分析**：LLM 可以自主决定下一步行动，调用合适的工具，并根据反馈调整策略

## 关键洞察

- **执行变得廉价**：让 LLM 生成代码、执行测试、迭代修复的成本已经极低，这使得大规模自动化审计成为可能
- **知识是真正的瓶颈**：漏洞模式、安全最佳实践、领域专业知识——这些才是稀缺资源
- **Agent 是知识的载体**：通过工具调用，LLM 可以获取、验证和应用知识

## 未来方向

- **短期**：Agent 编排仍是高杠杆方向
- **长期**：持续学习将重塑 Agent 范式

## 相关页面

- [自动化漏洞挖掘](automated-vuln-discovery.md)
- [源文档总结](../summary/ai-vuln-discovery-evolution.md)
