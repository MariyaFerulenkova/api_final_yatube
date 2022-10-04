# API Проекта Yatube
### Описание
Возможности, предоставляемые API социальной сети блогеров Yatube указаны в таблице ниже.
| Endpoint | Доступные методы HTTP запроса | Описание |
| -------- | ----------------------------- | -------- |
| api/v1/posts/ | GET |  Получение списка всех публикаций. При указании параметров limit и offset выдача будет работать с пагинацией. |
| api/v1/posts/ | POST | Добавление новой публикации в коллекцию публикаций. Анонимные запросы запрещены. | api/v1/posts/{id}/ | GET | Получение публикации по id. |
| api/v1/posts/{id}/ | GET |  Получение публикации по id. |
| api/v1/posts/{id}/ | PUT, PATCH, DELETE | Обновление публикации (полное или частичное) и удаление публикации по id. Обновить или удалить публикацию может только автор публикации. Анонимные запросы запрещены. |
| api/v1/posts/{post_id}/comments/ | GET | Получение всех комментариев к публикации. |
| api/v1/posts/{post_id}/comments/ | POST | Добавление нового комментария к публикации. Анонимные запросы запрещены. |
| api/v1/posts/{post_id}/comments/{id}/ | GET | Получение комментария к публикации по id. |
| api/v1/posts/{post_id}/comments/{id}/ | PUT, PATCH, DELETE | Обновление комментария (полное или частичное) к публикации по id, удаление комментария по id. Обновить или удалить комментарий может только автор комментария. Анонимные запросы запрещены. |
| api/v1/groups/ | GET | Получение списка доступных сообществ. |
| api/v1/groups/{id}/ | GET | Получение информации о сообществе по id. |
| api/v1/follow/ | GET | Возвращает все подписки пользователя, сделавшего запрос. Анонимные запросы запрещены. |
| api/v1/follow/ | POST | Подписка пользователя от имени которого сделан запрос на пользователя переданного в теле запроса. Анонимные запросы запрещены. |
| api/v1/jwt/create/ | POST | Получение JWT-токена. |
| api/v1/jwt/refresh/ | POST | Обновление JWT-токена. |
| api/v1/jwt/verify/ | POST | Проверка JWT-токена. |

### Примеры запросов
- POST: api/v1/posts/  
Request samples 
```json
{
"text": "string",
"image": "string",
"group": 0
} 
```
Response samples
```json
{
"id": 0,
"author": "string",
"text": "string",
"pub_date": "2019-08-24T14:15:22Z",
"image": "string",
"group": 0
}
```
- PUT: api/v1/posts/{id}/
Request samples 
```json
{
"text": "string",
"image": "string",
"group": 0
}
```
Response samples
```json
{
"id": 0,
"author": "string",
"text": "string",
"pub_date": "2019-08-24T14:15:22Z",
"image": "string",
"group": 0
}
```
- POST: api/v1/posts/{post_id}/comments/
Request samples
```json
{
"text": "string"
}
```
Response samples
```json
{
"id": 0,
"author": "string",
"text": "string",
"created": "2019-08-24T14:15:22Z",
"post": 0
}
```
- POST: api/v1/follow/
Request samples 
```json
{
"following": "string"
}
```
Response samples
```json
{
"user": "string",
"following": "string"
}
```

### Запуск проекта в dev-режиме
Клонировать репозиторий и перейти в него в командной строке

Cоздать и активировать виртуальное окружение:
```sh
python -m venv venv
```
```sh
source venv/Scripts/activate
```
Установить зависимости из файла requirements.txt при помощи команды:
```sh
pip install -r requirements.txt
```
Выполнить миграции:
```sh
python manage.py migrate
```
Запустить проект:
```sh
python manage.py runserver
```

### Основные использованные технологии
- Python 3.7.9
- Django 2.2.16
- Djangorestframework 3.12.4
- Djangorestframework-simplejwt 4.7.2

### Авторы
ЯндексПрактикум, Мария Феруленкова
