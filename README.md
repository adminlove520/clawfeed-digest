# ClawFeed Digest Fetcher

> 抓取 ClawFeed AI 新闻简报，写入 Obsidian 知识库

## 功能

- 抓取 ClawFeed 简报（4h/日报/周报）
- 自动写入 Obsidian 指定目录
- 支持命令行参数灵活配置

---

## 前置配置

### 1. 安装 Obsidian

**Windows:**
1. 下载 [Obsidian](https://obsidian.md/)
2. 安装并打开
3. 创建或选择一个 Vault（知识库）

**Mac:**
```bash
brew install obsidian
```

### 2. 获取 Obsidian Vault 路径

Obsidian Vault 就是一个普通文件夹。获取路径：

**方法一：Obsidian 内查看**
- 打开 Obsidian → 设置 → 关于 → 看看 "打开的库" 路径

**方法二：配置文件**
- Windows: `%APPDATA%\obsidian\obsidian.json`
- Mac: `~/Library/Application Support/obsidian/obsidian.json`

示例路径：
- Windows: `C:\Users\你的用户名\OneDrive\文档\Obsidian Vault`
- Mac: `~/Documents/Obsidian Vault`

### 3. 创建 AI 新闻目录

在 Obsidian Vault 中创建文件夹：
```
AI新闻/
```

### 4. 配置 OpenClaw 定时任务（可选）

如果需要在 OpenClaw 中自动运行：

```json
{
  "name": "每日 AI 新闻简报",
  "schedule": "0 17 * * *",
  "sessionTarget": "isolated",
  "payload": {
    "kind": "agentTurn",
    "message": "运行 python scripts/fetch_clawfeed.py 抓取 ClawFeed 日报"
  }
}
```

---

## 安装

```bash
# 克隆仓库
git clone https://github.com/adminlove520/clawfeed-digest.git
cd clawfeed-digest

# 安装依赖
pip install requests
```

---

## 使用方法

### 基本用法

```bash
# 获取今日日报
python scripts/fetch_clawfeed.py

# 获取最近 3 条日报
python scripts/fetch_clawfeed.py -l 3

# 获取 4h 简报
python scripts/fetch_clawfeed.py -t 4h

# 获取周报
python scripts/fetch_clawfeed.py -t weekly

# 指定输出目录
python scripts/fetch_clawfeed.py -out "D:/Obsidian/AI新闻"
```

### 参数说明

| 参数 | 简写 | 说明 | 默认值 |
|------|------|------|--------|
| `--type` | `-t` | 简报类型: `4h`, `daily`, `weekly` | `daily` |
| `--limit` | `-l` | 获取数量 | `1` |
| `--offset` | `-o` | 偏移量 | `0` |
| `--output` | `-out` | 输出目录 | `~/OneDrive/文档/Obsidian Vault/AI新闻` |

---

## 关于日报时间

**注意：** ClawFeed 日报生成时间约为每天 **16:38 SGT（新加坡时间）**

这意味着：
- 如果在 17:00（北京时间）运行，获取的是**当天的日报**

---

## 数据来源

- [ClawFeed](https://clawfeed.kevinhe.io/) - AI 新闻简报聚合

---

## 示例输出

```markdown
# 📋 ClawFeed 日报 | 2026-03-04

> 汇总自今日 6 份 4h 简报

---

## 🔥 今日头条

### 1. Anthropic 被 Trump 政府列入黑名单
...

## 📰 今日 Feed 精选 Top 10

1. **@mengxi_ream** — ...
   https://x.com/.../status/...
```

---

## 依赖

- Python 3.6+
- requests 库 (`pip install requests`)

---

**Author**: 小溪 (adminlove520)  
**Version**: 1.0.0
