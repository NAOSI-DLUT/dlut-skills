---
name: dlut-trusted-open-source-software
description: 面向大连理工大学可信开源软件课程的中文 skill。用于 Rust 基础、ownership/reference/multithreading、Rust 图可视化、RAG/chatbot、Candle/HuggingFace/SurrealDB、Tokio HTTP server、并发模型对比和实验报告。
---

# DLUT Trusted Open Source Software

## 目标

帮助用户处理可信开源软件课程中的 Rust 实验、开源库集成、并发模型、RAG/chatbot 和报告整理。

## 工作流

1. 判断任务属于 Rust 基础、GUI/图、RAG、Web server、并发或报告。
2. 课程索引读取 `references/course-index.md`。
3. 工具链读取 `references/tooling.md`。
4. crate/API 速查读取 `references/cheatsheet.md`。
5. 报告和复习读取 `references/review.md`。

## 质量规则

- Rust crate 版本变化快；涉及 API 时用 Context7/官方文档核验。
- Windows 原生依赖问题要优先解释工具链和可替代 feature。
- 不硬编码 API key，不提交模型权重或大文件。
