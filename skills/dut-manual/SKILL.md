---
name: dut-manual
description: 面向大连理工大学学生的 DUTManual/NAOSI 校园资料导航 skill。用于查询大工生存手册、NAOSI 资料云盘、课程攻略、大工云盘 pan.dlut.edu.cn、校园生活服务、资料检索和链接核验等中文场景。
---

# DUTManual

## 目标

帮助用户围绕 DUTManual、NAOSI 和大工云盘整理校园资料、生活服务、课程资料入口和检索路径。优先输出中文。

## 工作流

1. 判断用户是在找校园生活信息、课程资料、云盘资源、群组资料，还是要整理/核验链接。
2. 对时间敏感内容先核验来源：DUTManual、NAOSI、学校网信中心、大工云盘。
3. 只引用公开页面或用户提供的材料，不转述需要登录后才能看到的私有资料正文。
4. 输出最小可用结果：入口链接、检索步骤、资料整理表、注意事项或待确认清单。
5. 标注信息来源和核验日期；不把旧经验当成当前规则。

## 资源

- `references/source-map.md`：DUTManual、NAOSI、大工云盘等入口与核验规则。
- `references/search-playbook.md`：资料检索和课程资料定位流程。
- `references/safety.md`：隐私、版权和课程资料边界。

## 质量规则

- 不编造学校政策、系统行为、账号权限、群组存在性或资料目录。
- 避免暴露学生姓名、学号、账号、手机号、私有群链接和未公开资料。
- 对 `pan.naosi.org`、`pan.dlut.edu.cn` 等链接始终重新访问确认。
