import telebot
# TOKEN
import config

from telebot import types

bot = telebot.TeleBot(config.TOKEN)

# Menu
markup = types.InlineKeyboardMarkup(row_width=2)
item1 = types.InlineKeyboardButton(
    "Brief Information", callback_data='Brief Information')
item2 = types.InlineKeyboardButton(
    "Man/Female Compatibility", callback_data='Man/Female Compatibility')
item3 = types.InlineKeyboardButton(
    "Possible children Blood Types",
    callback_data='Possible children Blood Types')
item4 = types.InlineKeyboardButton(
    "Donor Compatibility", callback_data='Donor Compatibility')

markup.add(item1, item2, item3, item4)

# Buttons for compatibility (male)
markup_comp = types.InlineKeyboardMarkup(row_width=4)
item1 = types.InlineKeyboardButton("O+", callback_data='Male: First Positive')
item2 = types.InlineKeyboardButton("O-", callback_data='Male: First Negative')
item3 = types.InlineKeyboardButton("A+", callback_data='Male: Second Positive')
item4 = types.InlineKeyboardButton("A-", callback_data='Male: Second Negative')
item5 = types.InlineKeyboardButton("B+", callback_data='Male: Third Positive')
item6 = types.InlineKeyboardButton("B-", callback_data='Male: Third Negative')
item7 = types.InlineKeyboardButton(
    "AB+", callback_data='Male: Fourth Positive')
item8 = types.InlineKeyboardButton(
    "AB-", callback_data='Male: Fourth Negative')

markup_comp.add(item1, item2, item3, item4, item5, item6, item7, item8)

# Buttons for compatibility (female)
markup_comp_f = types.InlineKeyboardMarkup(row_width=4)
item1 = types.InlineKeyboardButton(
    "O+", callback_data='Female: First Positive')
item2 = types.InlineKeyboardButton(
    "O-", callback_data='Female: First Negative')
item3 = types.InlineKeyboardButton(
    "A+", callback_data='Female: Second Positive')
item4 = types.InlineKeyboardButton(
    "A-", callback_data='Female: Second Negative')
item5 = types.InlineKeyboardButton(
    "B+", callback_data='Female: Third Positive')
item6 = types.InlineKeyboardButton(
    "B-", callback_data='Female: Third Negative')
item7 = types.InlineKeyboardButton(
    "AB+", callback_data='Female: Fourth Positive')
item8 = types.InlineKeyboardButton(
    "AB-", callback_data='Female: Fourth Negative')

markup_comp_f.add(item1, item2, item3, item4, item5, item6, item7, item8)

# Buttons for gender
markup_gender = types.InlineKeyboardMarkup(row_width=2)
item1 = types.InlineKeyboardButton("Man", callback_data='man')
item2 = types.InlineKeyboardButton("Woman", callback_data='woman')

markup_gender.add(item1, item2)


# Welcome
@bot.message_handler(commands=['start'])
def welcome(message):
    sti = open('static/welcome.webp', 'rb')
    bot.send_sticker(message.chat.id, sti)
    bot.send_message(
        message.chat.id, "Welcome, {0.first_name}!\nI am - <b>{1.first_name}</b>, \
a bot created in order to inform people about the \
importance of knowledge some things about <b>Blood \
Types</b>.".format(message.from_user, bot.get_me()),
        parse_mode="html", reply_markup=markup)


# Call menu
@bot.message_handler(commands=['menu'])
def menu(message):
    bot.send_message(
        message.chat.id, "Main menu: ", parse_mode='html', reply_markup=markup)

# Functions texts
info_text = 'Blood groups \nThere are 4 main blood groups (types of blood) \
– A, B, AB and O. Your blood group is determined by the genes you \
inherit from your parents.\nEach group can be either RhD positive \
or RhD negative, which means in total there are 8 blood groups.\
\n\nAntibodies and antigens \nBlood is made up of \
red blood cells, white blood cells and platelets in a liquid called plasma. \
Your blood group is identified by antibodies and antigens in the blood.\
\nAntibodies are proteins found in plasma. They\'re part of your body\'s \
natural defences. They recognise foreign substances, \
such as germs, and alert your immune system, which \
destroys them.\nAntigens are protein molecules \
found on the surface of red blood cells.\
\n\nThe ABO system\nThere are 4 main blood groups \
defined by the ABO system:\n -blood group A – has A antigens \
on the red blood cells with anti-B antibodies in the plasma\n \
-blood group B – has B antigens with anti-A antibodies in the \
plasma\n -blood group O – has no antigens, but both anti-A and anti-B \
antibodies in the plasma\n -blood group AB – has both A and B \
antigens, but no antibodies.\
\n\nThe Rh system\nRed blood cells sometimes have \
another antigen, a protein known as the RhD antigen. If this is \
present, your blood group is RhD positive. If it\'s absent, your \
blood group is RhD negative.\n\nThis means you can be 1 of 8 blood \
groups:\n\n -A RhD positive (A+)\n\n -A RhD negative (A-)\n\n -B RhD \
positive (B+)\n\n -B RhD negative (B-)\n\n -O RhD positive (O+)\n\n -O \
RhD negative (O-)\n\n -AB RhD positive (AB+)\n\n -AB RhD negative (AB-)'
m_f_comp_text0 = 'Choose the blood type for male: '
m_f_comp_text1 = 'Choose the blood type for female: '
m_f_comp_text2 = 'Choose your gender: '
male_pos = 'There are risk of conflict having children \
from women having O-, A-, B- or AB- blood types.'
male_neg = 'There are no risk of conflict having children \
from women having any blood type.'
female_pos = 'There are no risk of conflict having children \
from men having any blood type.'
female_neg = 'There are risk of conflict having children \
from men having O+, A+, B+ or AB+ blood types.'
female_first_pos = 'There are risk of conflict having children \
from men having A, B or AB blood types.'


# Functions
@bot.callback_query_handler(func=lambda call: True)
def callback_inline(call):
    try:
        if call.message:
            if call.data == 'Brief Information':
                bot.send_message(
                    call.message.chat.id, info_text)
            elif call.data == 'Man/Female Compatibility':
                bot.send_message(
                    call.message.chat.id,
                    m_f_comp_text2, reply_markup=markup_gender)
            # Compatibility results
            elif call.data == 'man':
                bot.send_message(
                    call.message.chat.id,
                    m_f_comp_text0, reply_markup=markup_comp)
            elif call.data == 'Male: First Positive':
                bot.send_message(call.message.chat.id, male_pos)
            elif call.data == 'Male: First Negative':
                bot.send_message(call.message.chat.id, male_neg)
            elif call.data == 'Male: Second Positive':
                bot.send_message(call.message.chat.id, male_pos)
            elif call.data == 'Male: Second Negative':
                bot.send_message(call.message.chat.id, male_neg)
            elif call.data == 'Male: Third Positive':
                bot.send_message(call.message.chat.id, male_pos)
            elif call.data == 'Male: Third Negative':
                bot.send_message(call.message.chat.id, male_neg)
            elif call.data == 'Male: Fourth Positive':
                bot.send_message(call.message.chat.id, male_pos)
            elif call.data == 'Male: Fourth Negative':
                bot.send_message(call.message.chat.id, male_neg)
            elif call.data == 'woman':
                bot.send_message(
                    call.message.chat.id,
                    m_f_comp_text1, reply_markup=markup_comp_f)
            elif call.data == 'Female: First Positive':
                bot.send_message(call.message.chat.id, female_first_pos)
            elif call.data == 'Female: First Negative':
                bot.send_message(call.message.chat.id, female_neg)
            elif call.data == 'Female: Second Positive':
                bot.send_message(call.message.chat.id, female_pos)
            elif call.data == 'Female: Second Negative':
                bot.send_message(call.message.chat.id, female_neg)
            elif call.data == 'Female: Third Positive':
                bot.send_message(call.message.chat.id, female_pos)
            elif call.data == 'Female: Third Negative':
                bot.send_message(call.message.chat.id, female_neg)
            elif call.data == 'Female: Fourth Positive':
                bot.send_message(call.message.chat.id, female_pos)
            elif call.data == 'Female: Fourth Negative':
                bot.send_message(call.message.chat.id, female_neg)

            elif call.data == 'Possible children Blood Types':
                bot.send_message(
                    call.message.chat.id, 'You could check \
                    The Possible Blood Type of Child by this table:')
                tbl = open('static/table.webp', 'rb')
                bot.send_sticker(call.message.chat.id, tbl)
            elif call.data == 'Donor Compatibility':
                bot.send_message(
                    call.message.chat.id, 'You could check \
                    The Blood Donor Compatibility by this table:')
                dnr = open('static/donor.webp', 'rb')
                bot.send_sticker(call.message.chat.id, dnr)


# remove inline buttons
            bot.edit_message_text(
                chat_id=call.message.chat.id,
                message_id=call.message.message_id, text=call.data,
                reply_markup=None)

            # show alert
            text = "To enter the main menu type '/menu'"
            bot.answer_callback_query(
                callback_query_id=call.id,
                show_alert=False, text=text)

    except Exception as e:
        print(repr(e))
# Run
bot.polling(none_stop=True)
