---
name: github-commit-push
description: Commit pending changes and push this project to the GitHub remote LVMIAO26/lvmiao over SSH port 443. Use when the user says 提交到github，推送到github，push到github. Do not use for the Gitee remote or for editing pages.
---

# 提交到 GitHub（commit 并 push 到 LVMIAO26/lvmiao）

将当前工作区 `d:\高级网页设计` 的全部变更提交并推送到 GitHub 仓库 `LVMIAO26/lvmiao`（分支 `master`）。环境为 Windows PowerShell。

## 关键事实（已实测）

- 本机 22 端口对外封锁，`git@github.com:...` 直连会被拒绝（Connection refused）。
- 必须走 SSH over 443：远程 URL 用 `ssh://git@ssh.github.com:443/LVMIAO26/lvmiao.git`。
- SSH 公钥已配置并验证通过：`ssh -p 443 -T git@ssh.github.com` 返回 `Hi LVMIAO26!`（GitHub 的 SSH 测试退出码为 1 属正常）。
- `origin` 固定指向 Gitee，不要改动 origin；GitHub 用独立远程名 `github`。

## 步骤

1. 先按 AGENTS.md 的 Prompt logging 规则在 `lv_prompt.md` 追加本次提示词日志。
2. `git status` 与 `git log --oneline -5` 了解当前状态与提交信息风格（中文短句）。
3. 暂存全部变更：`git add -A`。若出现 `.env`、凭据类文件则改为按文件暂存并向用户确认。
4. 提交：PowerShell 下用单行 `git commit -m "中文提交信息"`，信息概括本次改动；禁止 `--no-verify`、禁止 `--amend` 改写历史。
5. 检查远程：`git remote -v`。若无名为 `github` 的远程则添加：
   `git remote add github ssh://git@ssh.github.com:443/LVMIAO26/lvmiao.git`
   切勿使用 `git@github.com:LVMIAO26/lvmiao.git`（22 端口不通）。
6. 推送：`git push -u github master`（或 `git push github HEAD`）。首次连接已信任 ssh.github.com 主机密钥。
7. 推送被拒（远程有新提交）时先 `git pull --rebase github master` 再重试；出现冲突停止并交用户处理，禁止 `push --force`。
8. SSH 认证失败时先自检 `ssh -o BatchMode=yes -o StrictHostKeyChecking=accept-new -p 443 -T git@ssh.github.com`；仍失败则提示用户检查公钥，不要改用 https 密码方式。
9. 完成后 `git status` 确认工作区干净，`git log --oneline -1` 向用户报告提交哈希与推送结果。

## 约束

- GitHub 远程固定为 `github` = `ssh://git@ssh.github.com:443/LVMIAO26/lvmiao.git`，分支 `master`。
- 推 Gitee 用 `git-commit-push` 技能，两者互不替代；用户未要求时不要同时推送两个远程。
- 文件名含中文，PowerShell 命令中的路径一律加引号。
- 仅推送用户要求的提交，不夹带额外提交内容。
