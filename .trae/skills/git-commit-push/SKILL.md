---
name: git-commit-push
description: Commit all pending changes and push the current project to the Gitee remote at https://gitee.com/jio-o/lvmiao2026. Use when the user says 提交项目，提交代码，推送到gitee or asks to commit and push. Do not use for editing or creating pages.
---

# 提交项目（commit 并 push 到 Gitee）

将当前工作区 `d:\高级网页设计` 的全部变更提交并推送到 Gitee 远程仓库 `origin` = `https://gitee.com/jio-o/lvmiao2026`（分支 `master`）。环境为 Windows PowerShell。

## 步骤

1. 先按 AGENTS.md 的 Prompt logging 规则在 `lv_prompt.md` 追加本次提示词日志。
2. `git status` 与 `git log --oneline -5` 了解当前状态与提交信息风格（中文短句）。
3. 暂存全部变更：`git add -A`。本仓库是课程作业，无敏感文件；若出现 `.env`、凭据类文件则改为按文件暂存并向用户确认。
4. 提交：PowerShell 下用单行 `git commit -m "中文提交信息"`，信息概括本次改动（如 `新增15-1.html 数7游戏演示`）；多行信息用 PowerShell here-string。禁止 `--no-verify`、禁止 `--amend` 改写历史。
5. 确认远程：`git remote -v`，origin 必须是 `https://gitee.com/jio-o/lvmiao2026`；若不存在则 `git remote add origin https://gitee.com/jio-o/lvmiao2026.git`，若指向其他地址先向用户确认再改。
6. 推送：`git push -u origin master`（或 `git push origin HEAD`）。
7. 推送失败（远程有新提交）时先 `git pull --rebase origin master` 再重试；出现冲突停止并交用户处理，禁止 `push --force`。
8. 完成后 `git status` 确认工作区干净，`git log --oneline -1` 向用户报告提交哈希与推送结果。

## 约束

- 远程仓库固定为 `https://gitee.com/jio-o/lvmiao2026`，分支 `master`。
- 文件名含中文，PowerShell 命令中的路径一律加引号。
- 仅推送用户要求的提交，不要替用户追加额外提交内容。
