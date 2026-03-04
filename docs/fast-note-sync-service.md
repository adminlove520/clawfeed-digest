# Fast Note Sync Service

> Obsidian 与 OpenClaw workspace 自动同步服务

## 简介

Fast Note Sync Service 可以实现 Obsidian Vault 与 OpenClaw workspace 之间的双向同步。

- **GitHub**: https://github.com/haierkeys/fast-note-sync-service

---

## 安装

### 1. 下载服务

从 GitHub Releases 下载最新版本：
- Windows: `fast-note-sync-service-{版本}-windows-amd64.zip`
- Mac: `fast-note-sync-service-{版本}-darwin-amd64.tar.gz`
- Linux: `fast-note-sync-service-{版本}-linux-amd64.tar.gz`

### 2. 解压到合适位置

建议放在 OpenClaw workspace 目录下：
```
C:\Users\你的用户名\.openclaw\workspace\fast-note-sync-service-2.5.1-windows-amd64\
```

---

## 配置

编辑 `config/config.json`：

```json
{
  "obsidianVaultPath": "C:\\Users\\你的用户名\\OneDrive\\文档\\Obsidian Vault",
  "openclawWorkspacePath": "C:\\Users\\你的用户名\\.openclaw\\workspace",
  "syncIntervalMs": 5000,
  "enableAiSummary": false
}
```

### 配置说明

| 配置项 | 说明 |
|--------|------|
| `obsidianVaultPath` | Obsidian Vault 路径 |
| `openclawWorkspacePath` | OpenClaw workspace 路径 |
| `syncIntervalMs` | 同步间隔（毫秒），默认 5000ms |
| `enableAiSummary` | 是否启用 AI 摘要功能 |

---

## 运行

### 手动运行

```bash
# Windows
.\fast-note-sync-service.exe

# 或者后台运行
start /b .\fast-note-sync-service.exe
```

---

## 定时任务

### 启动 Fast Note Sync 服务

| 项目 | 内容 |
|------|------|
| **名称** | 启动 Fast Note Sync 服务 |
| **ID** | `2cb52248-77d4-4051-98f9-73635d535351` |
| **运行时间** | 每天 08:00 (北京时间) |
| **任务内容** | 启动 fast-note-sync-service 服务（如果未运行） |

**任务消息:**
```
启动 fast-note-sync-service 服务（如果未运行的话），然后汇报状态。
服务路径：C:\Users\whoami\.openclaw\workspace\fast-note-sync-service-2.5.1-windows-amd64\fast-note-sync-service.exe
```

---

## 常见问题

### Q: 服务启动后不同步？

检查：
1. 配置文件路径是否正确
2. Obsidian Vault 是否存在
3. OpenClaw workspace 权限是否正确

### Q: 同步有延迟？

默认 5 秒同步一次，可以调整 `syncIntervalMs` 参数。
