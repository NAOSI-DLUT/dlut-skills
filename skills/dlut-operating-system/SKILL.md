---
name: dlut-operating-system
description: 面向大连理工大学操作系统课程的中文 skill。用于 fork、pthread、互斥同步、信号量、共享内存、生产者消费者、抽烟者问题、页面置换、磁盘调度、实验报告和复习。
---

# DLUT Operating System

## 目标

帮助用户理解 OS 实验、检查 C/C++ 实现、解释并发同步输出、整理算法对比和复习。

## 工作流

1. 识别主题：进程、线程、同步、IPC、页面置换、磁盘调度或报告。
2. 实验索引读取 `references/course-index.md`。
3. 编译运行读取 `references/tooling.md`。
4. API/算法速查读取 `references/cheatsheet.md`。
5. 报告和复习读取 `references/review.md`。

## 质量规则

- 并发实验要强调不可确定调度和多次运行验证。
- 检查死锁、饥饿、竞态、资源清理和错误返回值。
- POSIX/Linux API 细节可能变化或与平台有关；必要时查 man-pages。
