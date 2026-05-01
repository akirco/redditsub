# Reddit Monitor

Reddit post monitoring tool with Telegram notifications and translation support.

## Features

- Monitor multiple Reddit subreddits
- Keyword filtering
- Telegram bot notifications
- Translation support (requires `trans` command)
- SQLite local history

## Requirements

- Python 3.12+
- `trans` command (optional, for translation)

## Configuration

On first run, a default config file will be created at `~/.config/redditsub/config.json`:

```json
{
  "settings": {
    "check_interval_seconds": 21600,
    "max_history_records": 100000,
    "enable_translation": false,
    "translation_target_lang": "zh-CN"
  },
  "telegram": {
    "bot_token": "your_bot_token",
    "chat_id": "your_chat_id"
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

### Config Options

| Option | Description |
|--------|-------------|
| `check_interval_seconds` | Check interval in seconds (default: 6 hours) |
| `max_history_records` | Maximum history records |
| `enable_translation` | Enable translation |
| `translation_target_lang` | Target language for translation |
| `subreddit` | Subreddit name |
| `keywords` | Keyword list, empty means match all |
| `link_flair_filter` | Post flair filter list, empty means match all |
| `category` | Sort method: `new`, `hot`, `top`, `rising` |

## Usage

```bash
# Run as daemon
./redditsub

# Or with python
python3 redditsub
```

### Using crontab

```bash
# Edit crontab
crontab -e

# Add task (run every hour)
0 * * * * /path/to/redditsub
```

## Install Translation Tool (Optional)

```bash
# Arch Linux
sudo pacman -S translate-shell

# Ubuntu/Debian
sudo apt install translate-shell

# macOS
brew install translate-shell
```

## Logs

Log file is located at `~/.config/redditsub/monitor.log`