from aiogram import Bot, Dispatcher, types, executor

bot = Bot(token="ТВОЙ_TELEGRAM_BOT_TOKEN")
dp = Dispatcher(bot)

@dp.message_handler(commands=['start'])
async def start(message: types.Message):
    keyboard = types.ReplyKeyboardMarkup(resize_keyboard=True)
    keyboard.add("📦 Каталог", "🛒 Корзина", "📞 Контакты")
    await message.answer("Добро пожаловать в магазин!", reply_markup=keyboard)

@dp.message_handler(text="📦 Каталог")
async def catalog(message: types.Message):
    # Здесь можно подключить базу данных с товарами
    await message.answer("Вот наши товары:\n\n1. Кроссовки - 5000₽\n2. Футболка - 1500₽")

# Дальше можно добавить логику заказов, оплаты и т.д.
executor.start_polling(dp)
