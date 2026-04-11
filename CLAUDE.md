# 敏宝饮食管家

过敏宝宝饮食追踪 PWA：饮食记录、症状关联、过敏原管理、AI 分析。

## 项目结构

- `敏宝饮食管家.html` — 主应用（单文件，含全部 CSS/JS）
- `index.html` — GitHub Pages 入口（**必须与主文件保持同步，每次编辑后 `cp 敏宝饮食管家.html index.html`**）
- `manifest.json` — PWA 清单
- `sw.js` — Service Worker（stale-while-revalidate 缓存策略，缓存名 `minbao-v4`）
- `ANALYSIS_PROMPT.md` — AI 分析 prompt 模板（含医学参数和文献 DOI）

## 功能

- 多宝宝管理、过敏原（重度/轻度）配置
- 快速记录：餐次、食材、看护人、时间
- 症状记录：8 种常见症状 + 严重度 1-5
- 时间线视图 + 日历导航
- AI 过敏分析：导出 prompt+数据包，粘贴到任意 LLM 生成报告
- JSON/CSV 备份导出 + 导入恢复
- PWA 离线支持，数据存 localStorage

## 部署

GitHub Pages: https://liuyuxin01210725-debug.github.io/minbao-diet/

Legacy 部署模式（从 main 分支直接部署，非 workflow）。

## Skill routing

When the user's request matches an available skill, ALWAYS invoke it using the Skill
tool as your FIRST action. Do NOT answer directly, do NOT use other tools first.
The skill has specialized workflows that produce better results than ad-hoc answers.

Key routing rules:
- Product ideas, "is this worth building", brainstorming → invoke office-hours
- Bugs, errors, "why is this broken", 500 errors → invoke investigate
- Ship, deploy, push, create PR → invoke ship
- QA, test the site, find bugs → invoke qa
- Code review, check my diff → invoke review
- Update docs after shipping → invoke document-release
- Weekly retro → invoke retro
- Design system, brand → invoke design-consultation
- Visual audit, design polish → invoke design-review
- Architecture review → invoke plan-eng-review
- Save progress, checkpoint, resume → invoke checkpoint
- Code quality, health check → invoke health
