## api_final
Проект API для социальной сети yatube

## Как запустить проект:

Клонировать репозиторий и перейти в него в командной строке:

```
git clone git@github.com:ibonish/api_final_yatube.git
```

```
cd api_final_yatube
```

Cоздать и активировать виртуальное окружение:

```
python3.7 -m venv venv
```

```
source venv/bin/activate
```

```
python -m pip install --upgrade pip
```

Установить зависимости из файла requirements.txt:

```
pip install -r requirements.txt
```

Выполнить миграции:

```
python manage.py migrate
```

Запустить проект:

```
python manage.py runserver
```

## Примеры запросов:

# Получение токена авторизации

Request
```
POST /api/v1/token/
form-data: {"username": "username_string", "password": "password_string"}
```

Response

```
{
"refresh": "<JRW-refresh-token>",
"access": "<JRW-access-token>",
}
```

# Получение списка всех постов

Request
```
GET /api/v1/posts/
headers: {"Authorization": "Bearer <JRW-access-token>"}
```

Response
```
status_code: 200
[
    {
        "id": 1,
        "text": "text",
        "author": "author",
        "pub_date": "2022-02-24T14:17:30Z"
    },
    ...
  ]
```

# Удаление поста по его id

Request
```
DELETE /api/v1/posts/{post_id}/
headers: {"Authorization": "Bearer <JRW-access-token>"}
body: {"text": "new_string"}
```

Response
```
status_code: 204
```

# Создание нового комментария

Request
```
POST /api/v1/posts/{post_id}/comments/
headers: {"Authorization": "Bearer <JRW-access-token>"}
body: {"text": "string"}
```

Response
```
status_code: 200
{
    "id": 0,
    "text": "text",
    "author": "author",
    "pub_date": "2022-02-24T14:17:30Z"
}
```

# Создание подписки

Request
```
POST /api/v1/follow/?user={username_string}
headers: {"Authorization": "Bearer <JRW-access-token>"}
body: {"following": "string"}
```

Response
```
status_code: 200
{
    "user": "user",
    "following": "following"
}
```
