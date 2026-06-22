# DLUT Skills

面向大连理工大学师生的 Agent Skills 集合，用来沉淀校内日常办事、课程学习、资料整理、数据分析和文档处理中的可复用 AI 工作流。

每个 skill 都是一个自包含目录，核心文件是 `SKILL.md`，可按需附带 `references/`、`scripts/` 和 `assets/`。

## 安装

推荐使用 `skills` CLI 直接从 GitHub 安装：

```bash
npx skills add NAOSI-DLUT/dlut-skills
```

安装到指定 Agent：

```bash
npx skills add NAOSI-DLUT/dlut-skills --agent codex
npx skills add NAOSI-DLUT/dlut-skills --agent claude-code
npx skills add NAOSI-DLUT/dlut-skills --agent github-copilot
```

常用选项：

```bash
npx skills add NAOSI-DLUT/dlut-skills --list
npx skills add NAOSI-DLUT/dlut-skills --global --agent codex
npx skills add NAOSI-DLUT/dlut-skills --skill dlut-campus-workflow --agent codex
```

Claude Code 也可以使用 plugin marketplace：

```text
/plugin marketplace add NAOSI-DLUT/dlut-skills
/plugin install dlut-skills@dlut-skills
```

## 创建新 Skill

复制模板：

```bash
cp -r template/skill-template skills/my-skill-name
```

然后编辑 `skills/my-skill-name/SKILL.md`：

- skill 名称使用小写短横线，例如 `course-review-planner`。
- `description` 写清“做什么”和“什么时候使用”。
- 长参考资料放 `references/`。
- 可复用脚本放 `scripts/`。
- 模板、图片、示例文件放 `assets/`。

更多规范见 [spec/skill-guidelines.md](spec/skill-guidelines.md)。

## 适合收集什么

- 校园日常：办事流程、校历安排、通知摘要、材料清单。
- 课程学习：复习计划、实验报告、课程资料整理、作业检查。
- 数据分析：问卷、成绩、实验数据、竞赛数据的清洗与可视化。
- 文档工具：报告、PPT、表格、申请材料、邮件文本。
- 本地自动化：格式转换、文件批处理、课程资料归档。

> [!IMPORTANT]
> 请不要提交个人敏感信息、账号密码、未公开课程资料、内部系统截图或违反学校/课程要求的内容。

## 参考

- [Anthropic Skills](https://github.com/anthropics/skills)
- [skills CLI](https://www.npmjs.com/package/skills)
- [OpenAI Codex Agent Skills](https://developers.openai.com/codex/skills)
- [Claude Code Skills](https://docs.anthropic.com/en/docs/claude-code/skills)
