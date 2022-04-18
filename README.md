# Учебный групповой проект "YaMDb"

![ example workflow ](https://github.com/impisuperstar/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)

## Авторы
- [Mikhail Sizov] (https://github.com/impisuperstar/)

## Стек технологий
- Docker, docker-compose
- Project based on Django
- Nginx used as a Webserver
- Posgresql used as a database

## Инструкция по установке проекта
Первым шагом необходимо установить docker:
```
https://docs.docker.com/engine/install/
```

Поставьте docker-compose:
```
https://docs.docker.com/compose/install/
```

Поставьте git:
```
https://www.activestate.com/resources/quick-reads/pip-install-git/
```

Склонируйте репозиторий и перейдите на него:
```
git clone git@github.com:impisuperstar/infra_sp2.git
```

Перейдите в директорию репозитория:
```
cd infra_sp2
```
Инструкция по заполнению .evn:
```
DB_ENGINE -  указываем, что работаем с postgresql
DB_NAME - имя базы данных
POSTGRES_USER -  логин для подключения к базе данных
POSTGRES_PASSWORD -  пароль для подключения к БД (установите свой)
DB_HOST -  название сервиса (контейнера)
DB_PORT -  порт для подключения к БД
SECRET_KEY - секретный ключ
```

Запустите проект:
```
docker-compose up --detach
```

Алгоритм регистрации пользователей:

Пользователь отправляет POST-запрос на добавление нового пользователя с параметрами email и username на эндпоинт /api/v1/auth/signup/.

YaMDB отправляет письмо с кодом подтверждения (confirmation_code) на адрес email.

Пользователь отправляет POST-запрос с параметрами username и confirmation_code на эндпоинт /api/v1/auth/token/, в ответе на запрос ему приходит token (JWT-токен).

При желании пользователь отправляет PATCH-запрос на эндпоинт /api/v1/users/me/ и заполняет поля в своём профайле
________________________________________________________________________
Примеры запросов к API:

Получение списка всех категорий и добавление новой категории: http://185.12.28.78:80/api/v1/categories/

Удаление категории: http://185.12.28.78:80/api/v1/categories/{slug}/

Получение списка всех жанров и добавление жанра: http://185.12.28.78:80/api/v1/genres/

Удаление жанра: http://185.12.28.78:80/api/v1/genres/{slug}/

Получение списка всех произведений и добавление произведения: http://185.12.28.78:80/api/v1/titles/

Получение информации о произведении и частичное обновление информации о произведении: http://185.12.28.78:80/api/v1/titles/{titles_id}/

Удаление произведения: http://185.12.28.78:80/api/v1/titles/{titles_id}/

Добавление нового отзыва: http://185.12.28.78:80/api/v1/titles/{title_id}/reviews/

Полуение отзыва по id: http://185.12.28.78:80/api/v1/titles/{title_id}/reviews/{review_id}/

Получение списка всех комментариев к отзыву и добавление комментария к отзыву: http://185.12.28.78:80/api/v1/titles/{title_id}/reviews/{review_id}/comments/

Удаление комментария к отзыву: http://185.12.28.78:80/api/v1/titles/{title_id}/reviews/{review_id}/comments/{comment_id}/

## Документация к API:

http://185.12.28.78:80/redoc/
