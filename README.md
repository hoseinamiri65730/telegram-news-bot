# telegram-news-bot
import feedparser
from telegram import Bot
import time

TOKEN = 'توکن_ربات_اینجا'
CHAT_ID = 'آی‌دی_عددیت_اینجا'

bot = Bot(token=TOKEN)

def get_latest_news():
    urls = [
        "https://feeds.reuters.com/reuters/businessNews",
    ]
    for url in urls:
        feed = feedparser.parse(url)
        entry = feed.entries[0]
        title = entry.title
        link = entry.link
        message = f"{title}\n{link}"
        bot.send_message(chat_id=CHAT_ID, text=message)

if __name__ == "__main__":
    while True:
        get_latest_news()
        time.sleep(600)
