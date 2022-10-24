# yamdb_final

![example workflow](https://github.com/Enh404/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)
# api_yamdb

## Описание:
Проект api_yamdb собирает отзывы (Review) пользователей на произведения (Titles). Произведения делятся на предустановленные категории (Categories), список которых может быть расширен администратором.
В каждой категории произведений существуют предустановленные жанры (Genres), перечень которых может быть пополнен администратором.
Сами произведения в api_yamdb не хранятся, пользователи могут ознакомиться с текстовым описанием произведения и оставить отзыв (Review), а также  поставить оценку. Из оценок формируется усреднённая оценка произведения — рейтинг.
К отзывам пользователи также могут оставлять комментарии (Comments). 

### Стек технологий:
Python3, Django, Django REST Framework, JWT

# Как запустить проект:

Установить и настроить Docker, с помощью официальной документации:

https://docs.docker.com/

Клонировать репозиторий:

`git clone git@github.com:Enh404/yamdb_final.git`

Заполнить _.env-файл_:

```DB_ENGINE=   # указываем, что работаем с postgresql```

```DB_NAME=   # имя базы данных```

```POSTGRES_USER=   # логин для подключения к базе данных```

```POSTGRES_PASSWORD=   # пароль для подключения к БД (установите свой)```

```DB_HOST=   # название сервиса (контейнера)```

```DB_PORT=   # порт для подключения к БД```

```SECRET_KEY=   # находится в settings.py```

 Перейти в директорию с _docker-compose_:

`cd yamdb_final/infra`

Развернуть проект, запустив _docker-compose_:

`docker-compose up -d`

Выполнить миграции:

`docker-compose exec web python manage.py migrate`

Создать суперпользователя:

`docker-compose exec web python manage.py createsuperuser`

Собрать статику:

`docker-compose exec web python manage.py collectstatic --no-input`

Если потребуется остановить проект:

`docker-compose down -v`
