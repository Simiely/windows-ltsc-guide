# DEVELOPMENT.md · 开发与维护

## 这是什么

单页教程：Windows 版本怎么选（LTSC 与常规版的实际差异），面向普通用户。
仓库里没有构建系统——两个 HTML 文件就是全部产物。

## 目录结构

| 文件 | 作用 |
|---|---|
| `index.html` | **交互版**，站点首页。31 行 JS 实现手风琴折叠（点标题展开/收起） |
| `Windows_LTSC_静态版.html` | **静态版**，零 `<script>`，全部内容默认展开，可单文件离线分发 |
| `favicon.png` | 站点图标 |
| `README.md` / `AGENTS.md` / `CHANGELOG.md` | 四件套 |

## 两个版本的差异

- 内容**必须一致**，只差交互：交互版能折叠，静态版一次展开到底。
- 改任何正文，**两个文件都要改**。这是本仓最容易出错的地方——只改一个，
  两版就会悄悄分叉，而且没人会发现（没有 diff 工具能判断"这两段是不是同一段"）。
- 改完各自在浏览器打开一遍，重点看折叠动效是否仍正常（`maxHeight` 依赖真实高度）。

## 怎么改

1. 纯手工 HTML/CSS/JS，**没有构建、没有依赖、没有测试**。
2. 两版同步修改 → 本地打开验证 → 提交。
3. 提交前跑文档检查：

```bash
python tools/repo-kit/check_repo.py --root .
pwsh tools/update-repo-kit.ps1 -Check
```

## 发布

GitHub Pages，源为 `main` 分支根目录，push 即发布：
https://simiely.github.io/windows-ltsc-guide/

## 约束（改之前先看）

- **两个 HTML 的文件名不能改**：外部链接、书签、Pages 入口都指向它们。
- **静态版必须保持零 `<script>`**：它的价值就是"能离线打开的单文件"。
- **不要给 Markdown 加 frontmatter**：Pages 走 Jekyll，带 frontmatter 的 `.md`
  会被渲染成额外页面。文档检查按 `link-only` 配置跑，只查链接。

## 机器层

`tools/repo-kit/` 与 `.github/workflows/repo-check.yml` 由 knowledge-base 的单项目规范安装，
**不要手改**；升级用：

```powershell
pwsh tools/update-repo-kit.ps1 -Source <knowledge-base>/模板库/repo-kit -Profile link-only
```
