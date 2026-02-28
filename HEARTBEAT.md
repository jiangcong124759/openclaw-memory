# HEARTBEAT.md - 定期检查任务

> ⏰ 每次心跳时检查这些任务

## 记忆管理检查

1. **检查上次归档时间**
   - 读取 `memory/.last-archive.json`
   - 如果超过3天未归档，运行 `scripts/memory-archive.sh`

2. **检查今日记忆文件**
   - 确保 `memory/YYYY-MM-DD.md` 存在
   - 如果不存在，创建新的每日记忆文件

## 下次归档时间

查看 `memory/.last-archive.json` 了解上次归档时间。

## 手动触发归档

```bash
bash /Users/jiangcong/.openclaw/workspace/scripts/memory-archive.sh
```

---

*记忆系统初始化: 2026-02-28*
