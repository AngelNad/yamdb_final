## Проект YaMDb
Приложение развёрнуто по адресу:
**http://51.250.31.38/api/v1/**

### Описание
Проект YaMDb собирает отзывы (Review) пользователей на произведения (Titles). Произведения делятся на категории: «Книги», «Фильмы», «Музыка». Список категорий (Category) может быть расширен администратором (например, можно добавить категорию «изобразительное искусство» или «ювелирка»).
К проекту по адресу http://51.250.31.38/redoc/ подключена документация API YaMDb. В ней описаны возможные запросы к API и структура ожидаемых ответов. Для каждого запроса указаны уровни прав доступа: пользовательские роли, которым разрешён запрос.

### Технологии
- Python 3.7
- Django 2.2.16
- Djangorestframework 3.12.4


### Заполнение файла .env

_Создайте в директории /infra файл .env с переменными окружения для работы с базой данных со значениями:_<br>
DB_ENGINE=django.db.backends.postgresql<br>
DB_NAME=postgres <br>
POSTGRES_USER=postgres <br>
POSTGRES_PASSWORD=postgres <br>
DB_HOST=db <br>
DB_PORT=5432

### Приложение работает на Docker-compose
Образ проекта на DockerHub **angelnad/yamdb_final** <br>

_**Workflow status badge:**_<br>
![Django-app-yamdb workflow](https://github.com/AngelNad/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)

_Команды для запуска приложения в контейнерах:_
- Разверните контейнеры в папке /infra запустив docker-compose командой

```
docker-compose up
```
У вас развернётся проект с базой данных Postgres. <br>
Чтобы проверить его работу, перейдите по ссылке http://127.0.0.1:8000/admin/
- В папке /infra с файлом docker-compose.yaml выполните миграции:

```
docker-compose exec web python manage.py makemigrations
docker-compose exec web python manage.py migrate
```
- Создайте суперпользователя:
```
docker-compose exec web python manage.py createsuperuser
```

- Соберите статику:
```
docker-compose exec web python manage.py collectstatic --no-input
```

### Заполнение базы:

```
docker-compose exec web python manage.py loaddata > fixtures.json
```

### Создайте дамп (резервную копию) базы:

```
docker-compose exec web python manage.py dumpdata > fixtures.json
```

### Автор:
Надежда Осипова - [AngelNad](https://github.com/AngelNad)

