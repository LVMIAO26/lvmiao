# AGENTS.md

## Overview

Static HTML/CSS coursework for "高级网页设计" (Advanced Web Design). No build system, no package manager, no framework — just plain HTML files that can be opened directly in a browser.

## File layout

- `index.html` — showcase/portfolio page linking to all exercises
- `N-M.html` — individual lesson exercises (e.g., `6-1 flex.html` = lesson 6, exercise 1). Each file is self-contained with inline `<style>`.
- `css.css` — shared stylesheet, currently only linked by `5-1 层叠与继承.html`
- `img/` — images referenced by exercise pages

## Conventions

- All HTML files use `<meta charset="UTF-8">` and `lang="zh-CN"` — preserve these.
- CSS is written inline in `<style>` tags per-file; do not refactor into external sheets unless asked.
- File names contain Chinese characters — always quote paths in shell commands.
- All variable names, CSS class names, and id names must start with `lm_` (e.g., `lm_box`, `lm_title`, `lm_count`). This replaces the earlier `lv_` prefix rule — use `lm_` for all NEW code; do not mass-rename existing files unless asked.
- Every new HTML file must include an author comment right after `<body>` (or at the top of the file): `<!-- 姓名：袁磊，日期：YYYY-MM-DD，功能名称：XXX -->` (fill in the actual date and the page's feature name).
- Every new HTML file must include a hyperlink back to `index.html` (e.g., `<a class="lm_back" href="./index.html">← 返回首页</a>`).

## Tech constraints

- Use native HTML, CSS, and JavaScript only — no frameworks, no third-party libraries, no CDN resources.
- Icons must come from the local `font/` directory (iconfont: `font/iconfont.css` classes or `font/iconfont.js` SVG symbols). Check `font/iconfont.json` for available glyph class names.
- Use `fetch` to get server-side data when the page needs remote data (no XMLHttpRequest, no jQuery.ajax).
- Cache-bust locally referenced assets that change (e.g., `./font/iconfont.css?v=2`).

## Prompt logging

Before executing any user request, append an entry to `lv_prompt.md` (do not overwrite existing content). Each entry must include:
- Timestamp in `yyyy-mm-dd-hh-mm` format
- Model name used
- Full prompt content from the user

## Preview

Open any `.html` file directly in a browser. No dev server or build step is needed.
