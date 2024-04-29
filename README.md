# Телеграмм бот «practicum_final_bot»

### Описание
**Личный Telegram-бот** [homework.py] обращается к API сервису Яндекс.Практикум и узнает статус домашней работы пользователя: взята ли работа в ревью, проверена ли она, а если проверена — то принял её ревьюер или вернул на доработку.

**Общий Telegram-бот** [homework_for_all.py] выполняет те же самые действия, но ботом может пользоваться любой студент Яндекс.практикум, т.к. при его запуске в Telegram пользователю необходимо самостоятельно установить токен API Яндекс.Практикума, который сохранится в базу данных.

Пример: [practicum_final_bot](https://t.me/practicum_final_bot)

Что делает бот:
* раз в 10 минут опрашивает API сервиса Яндекс.Практикум и проверяет статус последней отправленной на ревью работы;
* при обновлении статуса анализирует ответ API и отправляет соответствующее уведомление в Telegram;
* логирует свою работу и сообщает о важных проблемах сообщением в Telegram.

### Технологии:
* Python 3.11
* python-dotenv 0.19.0
* python-telegram-bot 13.7
* requests 2.26.0

### Запуск проекта
Клонировать проект c GitHub:
```
git clone git@github.com:chrnmaxim/homework_bot.git
```
Установить виртуальное окружение:
```
python -m venv venv
```
Активировать виртуальное окружениe:
```
. venv/bin/activate
```
Обновить менеджер пакетов pip:
```
python -m pip install --upgrade pip
```
Установить зависимости из requirements.txt:
```
pip install -r requirements.txt
``` 
Запуск **персонального бота**:
```
python homework.py
```
Запуск **общего бота***:
```
python homework_for_all.py
```

### **Дополнительная информация**
При создании **личного Telegram-бота** необходимо создать переменные окружения в файле **.env**.
```

PRACTICUM_TOKEN = Токен для доступа к данным Яндекс.Практикум
TELEGRAM_TOKEN = API токен бота
TELEGRAM_CHAT_ID = id чата
```

**PRACTICUM_TOKEN** - доступ к API Яндекс.Практикум возможен только по токену. Получить токен можно по [ссылке](https://oauth.yandex.ru/authorize?response_type=token&client_id=1d0b9dd4d652455a9eb710d450ff456a) при условии, что выполнен вход в учетную запись Яндекс.Практикум.

**TELEGRAM_TOKEN** - API токен личного бота необходимо получить у телеграм-бота [BotFather](https://t.me/BotFather).

**TELEGRAM_CHAT_ID** - id чата получаем путем отправки сообщения в телеграм-бота [userinfobot](https://t.me/userinfobot).

---

*Перед запуском **общего Telegram-бота** необходимо запустить файл **db.py** для создания пустой базы данных с таблицей пользователей:
```
python db.py
```
Расположение по умолчанию - env/users.db.
