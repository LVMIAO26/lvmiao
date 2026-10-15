---
name: git-commit-push
description: 使用 git commit 并 push 当前项目到 gitee 仓库。当用户要求提交代码、推送项目、commit 并 push、或部署到 gitee 时使用。
---

# Git Commit & Push to Gitee

将当前项目提交并推送到 gitee 远程仓库。

## 远程仓库

```
https://gitee.com/jio-o/lvmiao2026
```

## 执行步骤

1. **检查当前状态**：运行 `git status` 查看变更文件
2. **添加所有变更**：运行 `git add -A`
3. **提交**：运行 `git commit -m "提交描述"`（根据变更内容生成简洁的中文 commit message）
4. **推送**：运行 `git push`

## 注意事项

- 如果用户未指定 commit message，根据变更内容自动生成简洁的中文描述
- 如果推送失败（如远程有更新），先执行 `git pull --rebase` 再重试推送
- 如果仓库没有设置远程地址，先执行 `git remote add origin https://gitee.com/jio-o/lvmiao2026`
