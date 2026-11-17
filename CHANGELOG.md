# CHANGELOG.md · 版本记录

> 项目无正式版本号，按提交里程碑记录。

## 里程碑

- **接入文档检查（2026-11-17）**：接入 knowledge-base 的**单项目规范**（spec 2.1.3 / repo-kit 2.7.2，profile `link-only`）；新增 `schema/taxonomy.json`、`tools/repo-kit/`、`tools/update-repo-kit.ps1`、`schema/kit.lock.json` 与 CI；检查范围只含链接与入口（link-only）：**不要求 frontmatter**——两个站走 GitHub Pages + Jekyll，带 frontmatter 的 `.md` 会被渲染成额外页面；验收：`REPO CHECK: PASS`（ERROR=0）、`KIT LOCK: PASS (v2.7.2, spec=2.1.3)`；新增 [DEVELOPMENT.md](DEVELOPMENT.md)：两版差异、同步修改的约束、发布方式
- **模板回溯**：落地页采用 hub-back 模板样式（inline at top），交互版 index.html 定型
- **交互版上线**：index.html 交互版（推荐入口）+ Windows_LTSC_静态版.html（无交互静态版）
- **内容成稿**：2026-07-28 数据多方交叉验证核对（Microsoft / Windows Latest / PCWorld / Reddit），14 条更新事故时间线
- **初始版本**：Windows LTSC 选购指南（结论先行：选 LTSC；TPM 决策树选型）

## 备注

- 无版本 tag / Release；交付物为交互版 + 静态版两个 HTML 文档
