import telebot
import os

TOKEN = os.getenv("TOKEN")
CHANNEL = os.getenv("CHANNEL")

bot = telebot.TeleBot(TOKEN)

@bot.message_handler(func=lambda message: True)
def send_movie(message):
    if message.text.isdigit():
        post_id = int(message.text)
        try:
            bot.copy_message(
                message.chat.id,
                CHANNEL,
                post_id
            )
        except:
            bot.reply_to(message, "❌ Bu raqamdagi kino topilmadi.")
    else:
        bot.reply_to(message, "Faqat raqam yozing. Masalan: 500")

bot.infinity_polling()# MoviPrime1
MoviPrimeBot
