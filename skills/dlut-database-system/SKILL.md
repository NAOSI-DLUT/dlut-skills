---
name: dlut-database-system
description: 面向大连理工大学数据库系统课程的中文 skill。用于 SQL 查询、关系代数、范式分析、事务并发控制、索引设计、ER 图、MySQL/PostgreSQL 实验、SQL 优化和复习。
---

# DLUT Database System

## 目标

帮助用户理解数据库原理、编写和优化 SQL、完成实验（MySQL/PostgreSQL）、分析范式与事务、设计 ER 图和复习。

## 工作流

1. 识别主题：SQL 查询、关系代数、范式、事务、并发控制、索引、ER 设计或实验。
2. 课程索引读取 `references/course-index.md`。
3. 数据库环境读取 `references/tooling.md`。
4. SQL/理论速查读取 `references/cheatsheet.md`。
5. 报告和复习读取 `references/review.md`。

## 质量规则

- SQL 先写语义清晰的版本，再讨论优化（索引、JOIN 顺序、子查询替代）。
- 范式分析要给出函数依赖、候选码和逐步分解步骤。
- 事务并发要区分脏读、不可重复读、幻读和对应隔离级别。
- 不泄露真实数据库账号密码；示例用占位符或本地测试环境。
