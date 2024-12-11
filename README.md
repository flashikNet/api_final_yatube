# Yatube 2 API

## Описание
Yatube 2 API предоставляет функциональность на основе Rest API, реализованного с использованием Django REST Framework. С помощью этого API можно:
- Получать доступ к постам
- Управлять комментариями
- Работать с группами
- Управлять подписками пользователей

Функциональность доступна в соответствии с правами доступа (например, редактирование чужих постов или комментариев запрещено).

Полная документация API доступна по адресу (при запуске на локальной машине):

```
http://127.0.0.1:8000/redoc/
```

## Используемые технологии
- **Python**
- **Django REST Framework**
- **SQLite**

### Особенности
Проект исключает фронтенд и view-функции, предоставляя исключительно backend-логику.

## Как запустить проект

### 1. После клонирования репозитория, перейти в него в командной строке
```bash
git clone <URL_репозитория>
cd api_final_yatube
```

### 2. Создать и активировать виртуальное окружение

#### Для Linux/macOS:
```bash
python3 -m venv env
source env/bin/activate
```

#### Для Windows:
```bash
python3 -m venv env
source env/scripts/activate
```

### 3. Обновить `pip` и установить зависимости
```bash
python3 -m pip install --upgrade pip
pip install -r requirements.txt
```

### 4. Выполнить миграций
```bash
python3 manage.py migrate
```

### 5. Запустить сервер
```bash
python3 manage.py runserver
```

## Примеры запросов и ответов

### Получение списка постов (GET)
**Эндпоинт:**
```
/api/v1/posts/
```
**Пример ответа (код 200):**
```json
{
  "count": 123,
  "next": "http://api.example.org/accounts/?offset=400&limit=100",
  "previous": "http://api.example.org/accounts/?offset=200&limit=100",
  "results": [
    {
      "id": 0,
      "author": "string",
      "text": "string",
      "pub_date": "2021-10-14T20:41:29.648Z",
      "image": "string",
      "group": 0
    }
  ]
}
```

### Добавление комментария к посту (POST)
**Эндпоинт:**
```
/api/v1/posts/{post_id}/comments/
```
**Пример успешного ответа (код 201):**
```json
{
  "id": 0,
  "author": "string",
  "text": "string",
  "created": "2019-08-24T14:15:22Z",
  "post": 0
}
```

**Пример ошибки (код 400):**
```json
{
  "text": [
    "Обязательное поле."
  ]
}
```

## Дополнительная информация
Полное описание методов API доступно в документации http://127.0.0.1:8000/redoc/
