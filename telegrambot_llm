import logging
import ollama
from aiogram import Bot, Dispatcher, executor, types
from bs4 import BeautifulSoup
import requests

API_TOKEN = 'your_token_by_botfather'
OLLAMA_MODEL = "llama3.2:3b"  # or "deepseek-llm:7b" or other

ollama.embeddings(
    model=OLLAMA_MODEL,
    prompt=(
        'Отвечай на том языке, на котором тебя спросили. Ответы должны быть до 300 символов или до 5 предложений. '
        'Представь, что ты ученый-мудрец, который знает почти все на свете и главная твоя '
        'цель - передача накопленных знаний тем, кто задает тебе вопросы и просит помощи. Если тебя просят коротко пересказать, обдумай '
        'глубоко, основательно, и перескажи самую суть подробно, но доступным языком.'
    )
)

# Configure logging
logging.basicConfig(level=logging.INFO)

# Initialize bot and dispatcher
bot = Bot(token=API_TOKEN)
dp = Dispatcher(bot)

def http_mes(message_http):
    response = requests.get(message_http)

    if response.status_code == 200:
        soup = BeautifulSoup(response.text, 'html.parser')
        main_content = soup.find('body')
        message_http = main_content.get_text()
        print("Текст из основной части страницы успешно извлечен и сохранен в переменной message_http.")
        return message_http
    else:
        print("Ошибка при получении содержимого страницы.")
        return 'Извините, не смог получить доступ к сайту'

@dp.message_handler()
async def handle_message(message: types.Message):
    if 'http' in message.text:
        message_http = http_mes(message.text)
        message_http += ' Прочитай статью, резюмируй её содержание. Обдумай свой ответ. Дай свой ответ на русском языке.'
        
        response = ollama.chat(model=OLLAMA_MODEL, messages=[{'role': 'user', 'content': message_http}])
        await message.answer(response['message']['content'] if response['message']['content'] else "Произошла ошибка при обработке вашего сообщения")
    elif len(message.text) < 5:  # check if message is increasing
        response = ollama.chat(model=OLLAMA_MODEL, messages=[{'role': 'user', 'content': message.text}])
        await message.answer(response['message']['content'])
    else:
        response = ollama.chat(model=OLLAMA_MODEL, messages=[{'role': 'user', 'content': message.text}])
        await message.answer(response['message']['content'])

if __name__ == '__main__':
    executor.start_polling(dp, skip_updates=True)
