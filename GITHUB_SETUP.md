# GitHub 设置指南

## 创建 GitHub 仓库

运行以下命令来创建远程仓库（需要已登录 gh CLI）：

```bash
# 登录 GitHub（如果还没登录）
gh auth login

# 创建公开仓库
cd /Users/jiangcong/.openclaw/workspace
gh repo create openclaw-memory --public --source=. --remote=origin --push

# 或者创建私有仓库
gh repo create openclaw-memory --private --source=. --remote=origin --push
```

## 手动测试归档脚本

```bash
bash /Users/jiangcong/.openclaw/workspace/scripts/memory-archive.sh
```

## 查看归档状态

```bash
cat /Users/jiangcong/.openclaw/workspace/memory/.last-archive.json
```

## 归档流程

1. **每3天自动运行**（通过 cron 任务）
2. 提取3天前的记忆文件中的重要信息
3. 更新 MEMORY.md 的摘要部分
4. 提交到 GitHub
5. 删除本地3天前的原始文件

## 保留规则

- **本地**: 只保留最近3天的每日记忆文件
- **GitHub**: 完整的所有历史记忆
- **MEMORY.md**: 重要摘要 + 最近3天文件列表

---

*创建于: 2026-02-28*
