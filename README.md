
# Telegram Task Bot

Telegram Task Bot — это бот для управления задачами с функциями добавления, редактирования, удаления задач, установления дедлайнов и отправки напоминаний. Этот бот предоставляет пользователям возможность управлять задачами через кнопки в Telegram, избегая текстовых команд.

![Demo of Task Bot](assets/demo.gif)

## Основные функции

- **Добавление задач**: Пользователи могут добавлять задачи с описанием, датой и временем дедлайна.
- **Редактирование задач**: Задачи могут быть отредактированы через интерфейс бота.
- **Удаление задач**: Возможность удалять задачи с помощью нажатия на соответствующую кнопку.
- **Завершение задач**: Пользователи могут отмечать задачи как завершённые.
- **Напоминания**: Бот отправляет напоминания о задачах за 24 часа, 1 час и 15 минут до дедлайна.
- **Фильтрация задач**: Просмотр задач с фильтрацией по статусам (в процессе, завершено, просрочено).
- **Полная поддержка работы с кнопками**: Пользователи взаимодействуют с ботом только через кнопки, без необходимости ввода текстовых команд.

## Установка и настройка

### 1. Клонирование репозитория

```bash
git clone https://github.com/Jiger275/telegram_task_bot.git
cd telegram_task_bot
```

### 2. Создание виртуального окружения

Рекомендуется использовать виртуальное окружение для управления зависимостями.

```bash
python -m venv venv
source venv/bin/activate  # Для Windows используйте `venv\Scriptsctivate`
```

### 3. Установка зависимостей

Установите все необходимые зависимости, используя файл `requirements.txt`:

```bash
pip install -r requirements.txt
```

### 4. Настройка конфигурации

Создайте файл `config/config.py` и добавьте туда ваш токен бота:

```python
BOT_TOKEN = "ваш_токен_бота"
```

### 5. Настройка базы данных

Проект использует SQLite для хранения задач. Вам нужно создать и применить миграции для базы данных с помощью Alembic:

#### Инициализация Alembic

```bash
alembic init alembic
```

#### Генерация миграции для базы данных

```bash
alembic revision --autogenerate -m "Initial migration"
```

#### Применение миграции

```bash
alembic upgrade head
```

### 6. Запуск бота

Запустите бота с помощью следующей команды:

```bash
python main.py
```

### 7. Логирование

Вся информация о работе бота записывается в файл `logs/bot.log`. Убедитесь, что папка `logs/` существует, или она будет создана автоматически при запуске.

## Структура проекта

```bash
telegram_task_bot/
│
├── /bot/                   # Логика работы бота
│   ├── handlers.py          # Обработка команд и кнопок
│   ├── scheduler.py         # Планировщик напоминаний
│   └── tasks.py             # Работа с задачами
│
├── /config/                 # Конфигурационные файлы
│   └── config.py            # Конфигурация бота
│
├── /database/               # База данных и модели
│   ├── db.py                # Подключение к базе данных
│   └── models.py            # Модели базы данных
│
├── /logger/                 # Логирование
│   └── logger.py            # Настройка логов
│
├── /logs/                   # Логи
│   └── bot.log              # Файл логов
│
├── /alembic/                # Миграции базы данных
│   └── versions/            # Версии миграций
│
├── main.py                  # Основной файл для запуска бота
├── requirements.txt         # Зависимости проекта
└── README.md                # Описание проекта
```

## Работа с задачами

### Добавление задачи

Чтобы добавить задачу, выберите кнопку "Добавить задачу". Бот предложит ввести описание задачи, дату и время в формате:

```
Описание задачи ДД.ММ.ГГГГ ЧЧ:ММ
```

### Редактирование задачи

Для редактирования задачи выберите "Редактировать задачу", выберите задачу из списка и введите новое описание, дату и время в том же формате, что и при добавлении.

### Удаление задачи

Выберите "Удалить задачу", выберите задачу из списка, и бот удалит её.

### Завершение задачи

Выберите "Завершить задачу", выберите задачу из списка, и бот пометит её как завершённую.

### Просмотр задач

Вы можете просмотреть задачи с фильтрацией по следующим критериям:
- В процессе
- Завершено
- Просрочено

Фильтр выбирается через меню.

## Разработка

### Работа с Git

1. **Инициализация репозитория**: Инициализируйте проект с помощью Git, добавьте удалённый репозиторий.
   ```bash
   git init
   git remote add origin https://github.com/ваш_логин/telegram_task_bot.git
   ```

2. **Создание новой ветки для разработки**:
   ```bash
   git checkout -b feature/your-feature-name
   ```

3. **Коммит изменений**:
   ```bash
   git add .
   git commit -m "Описание изменений"
   ```

4. **Отправка изменений**:
   ```bash
   git push origin feature/your-feature-name
   ```

5. **Слияние изменений**: После завершения работы в ветке создайте Pull Request (PR) и выполните слияние с основной веткой.

## Лицензия

Этот проект лицензирован под лицензией MIT. Подробности смотрите в файле [LICENSE](LICENSE).
