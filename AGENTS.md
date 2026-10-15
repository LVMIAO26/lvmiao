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
- All CSS class names, id names, and JS variables must start with `lv_` (e.g., `lv_box`, `lv_title`, `lv_count`).
- Every new HTML file must include a hyperlink back to `index.html` (e.g., `<a class="lv_back" href="./index.html">← 返回首页</a>`).

## Prompt logging

Before executing any user request, append an entry to `lv_prompt.md` (do not overwrite existing content). Each entry must include:
- Timestamp in `yyyy-mm-dd-hh-mm` format
- Model name used
- Full prompt content from the user

## Preview

Open any `.html` file directly in a browser. No dev server or build step is needed.
