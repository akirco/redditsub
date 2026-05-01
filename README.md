# Reddit Monitor

[English](./README-en.md)

Reddit 帖子监控工具，支持 Telegram 通知和翻译功能。

## 功能

- 监控多个 Reddit 子版块
- 关键词过滤
- Telegram 机器人通知
- 支持翻译（需安装 `trans` 命令）
- SQLite 本地历史记录
- [ ] AI 数字人朗读
- [ ] 其他平台（v2ex,producthunt,github trending .etc）

## 依赖

- Python 3.12+
- `trans` 命令（可选，用于翻译）

## 配置

首次运行会自动创建默认配置文件 `~/.config/redditsub/config.json`：

```json
{
  "settings": {
    "check_interval_seconds": 21600,
    "max_history_records": 100000,
    "enable_translation": false,
    "translation_target_lang": "zh-CN"
  },
  "telegram": {
    "bot_token": "your_bot_token", //自行google
    "chat_id": "your_chat_id" //自行google
  },
  "subscriptions": [
    {
      "subreddit": "commandline",
      "keywords": [],
      "link_flair_filter": [],
      "category": "new"
    }
  ]
}
```

### 配置说明

| 配置项                    | 说明                                    |
| ------------------------- | --------------------------------------- |
| `check_interval_seconds`  | 检查间隔（秒），默认 6 小时             |
| `max_history_records`     | 历史记录最大条数                        |
| `enable_translation`      | 是否启用翻译                            |
| `translation_target_lang`  | 翻译目标语言                            |
| `subreddit`               | 子版块名称                              |
| `keywords`                | 关键词列表，为空则匹配所有              |
| `link_flair_filter`        | 帖子标签过滤列表，为空则匹配所有       |
| `category`                | 排序方式：`new`、`hot`、`top`、`rising` |

> 详细类型去找reddit json api

## 安装

```sh
curl -o ~/.local/bin/redditsub -fsSL https://raw.githubusercontent.com/akirco/redditsub/refs/heads/main/redditsub
chmod +x ~/.local/bin/redditsub
```

## 使用

```bash
# 直接运行（守护进程模式）
./redditsub

# 或使用 python
python3 redditsub
```

### 使用 crontab 定时执行

```bash
# 编辑 crontab
crontab -e

# 添加任务（每小时执行一次）
0 * * * * /path/to/redditsub
```

## 安装翻译工具（可选）

```bash
# Arch Linux
sudo pacman -S translate-shell

# Ubuntu/Debian
sudo apt install translate-shell

# macOS
brew install translate-shell
```

## 日志

日志文件位于 `~/.config/redditsub/monitor.log`
