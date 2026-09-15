# telegram-media-bulk-save

I needed a simple, reliable way to archive all images, videos, and documents from a couple of Telegram channels without hitting rate limits or starting from scratch every time the script interrupted. Existing tools either required running heavy self-hosted bots or lacked proper resume support.

This is a single-file CLI tool that downloads media from any chat or channel you have access to, tracks what has already been downloaded in a local state file, and handles Telegram's flood waits gracefully.

## Installation

1. Install Python 3.10+ (tested on Windows 11).
2. Install the required dependencies:
   ```cmd
   pip install -r requirements.txt
   ```
3. Get your API ID and Hash from https://my.telegram.org and save them in a `.env` file in the same directory:
   ```env
   TELEGRAM_API_ID=1234567
   TELEGRAM_API_HASH=abcdef0123456789abcdef0123456789
   ```

## How to run

On the first run, the script will prompt you for your phone number and the login code sent by Telegram to establish a session.

Download all photos and videos from a public channel:
```cmd
python bulk_save.py --chat channel_username --types photo video --out D:\Archive\Telegram
```

Limit the download to the last 500 messages and use 3 concurrent download workers:
```cmd
python bulk_save.py --chat channel_username --limit 500 --workers 3
```

Only download files larger than 10MB:
```cmd
python bulk_save.py --chat channel_username --min-size 10485760
```

<!-- verified: 2026-09-15 -->
