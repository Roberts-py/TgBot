from aiogram import Bot, Dispatcher, types
from aiogram.utils import executor
from aiogram.types import ReplyKeyboardMarkup, KeyboardButton

TOKEN = "7905213193:AAHfVfUctab_bl_NMgV9W_aAh94BWViLCxg"

bot = Bot(token=TOKEN)
dp = Dispatcher(bot)

# Создание клавиатуры
keyboard = ReplyKeyboardMarkup(resize_keyboard=True)
keyboard.add(
    KeyboardButton("/start"),
    KeyboardButton("/info"),
    KeyboardButton("/faq"),
    KeyboardButton("/contact"),
)

# Обработчик команды /start
@dp.message_handler(commands=['start'])
async def start_command(message: types.Message):
    await message.answer(f"""
    Привет! Я бот компании Premier city.
    Мы предоставляем услуги по купли и продаже недвижимости.
    
    Вот что я могу:
    - /start — Начать
    - /info — Информация о сервисе
    - /faq — Часто задаваемые вопросы
    - /contact — Контакты
    """, reply_markup=keyboard)  # Добавляем клавиатуру

@dp.message_handler(commands=['info'])
async def info_command(message: types.Message):
      await message.answer(f"""
Наша компания занимается продажей недвижимости
 наши услуги всего 2%""", reply_markup=keyboard)     

@dp.message_handler(commands=['contact'])
async def contact_command(message: types.Message):
      await message.answer(f"""
Наш сайт: Prcity.pro
Контактные данные: +7 938 795-55-97
Адрес: Дахадаева 86, 4 этаж""", reply_markup=keyboard)     

# Запуск бота
if __name__ == "__main__":
    executor.start_polling(dp, skip_updates=True)

