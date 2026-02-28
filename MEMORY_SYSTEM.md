# 🧠 记忆管理系统

> 自动化记忆管理 - 每3天整理，自动归档到 GitHub

## 📁 文件结构

```
workspace/
├── MEMORY.md                    # 长期记忆（重要信息 + 最近3天记录）
├── memory/
│   ├── .last-archive.json       # 归档状态跟踪
│   ├── 2026-02-28.md           # 今日记忆（示例）
│   ├── 2026-02-27.md           # 昨日记忆（示例）
│   └── 2026-02-26.md           # 前日记忆（示例）
├── scripts/
│   └── memory-archive.sh        # 归档脚本
└── GITHUB_SETUP.md             # GitHub 设置指南
```

## 🔄 自动化流程

### 1. 每日记录
- 每次对话自动记录到 `memory/YYYY-MM-DD.md`
- 重要信息同时更新到 `MEMORY.md`

### 2. 每3天归档（自动）
脚本 `memory-archive.sh` 会：
- 提取3天前文件的重要信息
- 更新 `MEMORY.md` 摘要
- 提交到 GitHub
- 删除本地3天前的原始文件

### 3. 心跳检查
每次心跳时检查：
- 今日记忆文件是否存在
- 是否需要运行归档

## 🚀 设置 GitHub

```bash
# 1. 确保已登录 GitHub
gh auth status

# 2. 创建并推送仓库
cd /Users/jiangcong/.openclaw/workspace
gh repo create openclaw-memory --public --source=. --remote=origin --push
```

## 📋 手动操作

```bash
# 立即运行归档
bash scripts/memory-archive.sh

# 查看归档状态
cat memory/.last-archive.json

# 创建今日记忆（如果不存在）
touch memory/$(date +%Y-%m-%d).md
```

## ⚙️ 配置

### 修改归档间隔
编辑 cron 任务：
```bash
openclaw cron list
openclaw cron update <job-id> --schedule "..."
```

### 调整保留天数
修改 `scripts/memory-archive.sh` 中的 `-mtime +3` 参数

## 📝 当前状态

- ✅ 记忆系统已初始化
- ✅ 自动归档脚本已创建
- ✅ Cron 任务已设置（每3天）
- ✅ 首次提交已完成
- ⏳ 等待 GitHub 仓库配置

---

*系统创建: 2026-02-28*
