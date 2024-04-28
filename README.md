#  Kittygram: управление котиками.

## Краткое описание проекта:

Сайт с возможностью публикации фотографий котов и их достижений.

## Как запустить проект:
1. Установить Docker, Docker Compose (для Windows - актуальный Docker Desktop).

2. Клонировать репозиторий с проектом на свой компьютер:
   ```git clone git@github.com:Nina2301/kittygram_final.git```

3. Установить и активировать виртуальное окружение: 
```
python3.9 -m venv venv
. venv/bin/activate
```
В виртуальном окружении установить зависимости:
```
pip install -r requirements.txt
```

4. Создать .env файл с информацией по аналогии с example.env:                                                       
```
DB_ENGINE=django.db.backends.postgresql
POSTGRES_USER=django_user
POSTGRES_PASSWORD=mysecretpassword
POSTGRES_DB=django
DB_HOST=db
DB_PORT=5432
ALLOWED_HOSTS=127.0.0.1, localhost, backend
SECRET_KEY='секретный ключ Django'
```

5. Выполнить сборку контейнеров: ```docker-compose up -d --build```
6. Выполнить миграции: ```docker-compose exec backend python manage.py migrate```
7. Создать суперпользователя: ```docker-compose exec backend python manage.py createsuperuser```
8. Собрать файлы статики: ```docker-compose exec backend python manage.py collectstatic```
9. Скопировать файлы статики в /backend_static/static/ backend-контейнера: ```docker compose exec backend cp -r /app/collected_static/. /backend_static/static/```
