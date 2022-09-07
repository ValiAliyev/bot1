# bot1
import telebot
from mailcheck import MailCheck
mails= []
MyTooken = "5431067635:AAEEA8WSzwRL3ajoPSwZfbRNxuRipaCEVcU"
MyBot = telebot.TeleBot(MyTooken)
#MyFile = open('F:\Rasul\MailData', 'a+')


@MyBot.message_handler(commands=['start'])
def Start(message):
    MyBot.reply_to(message,"Xos geldiniz!")
    for i in mails:
        MyBot.reply_to(message,i)

@MyBot.message_handler(func= lambda message: True)
def UserMessage(message):
    UserInput = str(message.text).lower()
    if MailCheck(UserInput) == True:
        mails.append(UserInput)
    else:
        MyBot.reply_to(message,'Mail daxil edin!')


while True:
    try:
        MyBot.polling()
    except Exception:
        MyBot.polling()
