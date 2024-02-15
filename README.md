# Kittygram - социальная сеть для размещение фотографий домашних животных.

## Описание проекта
Проект, где пользователи могут регистрироваться, загружать фотографии кошек с описанием их достижений, а также любоваться на других котов.

## Технологии
• Python 3.9
• Django==3.2.16
• djangorestframework==3.12.4
• nginx
• djoser==2.1.0

## Автор
Юлия Нелюбина https://github.com/NelyubinaJ670 

## Что cделано:

- Настроен запуск проекта Kittygram в контейнерах и CI/CD с помощью GitHub Actions
- Пуш в ветку main запускает тестирование и деплой Kittygram, а после успешного деплоя вам приходит сообщение в телеграм.
- В корне проекта есть файл `kittygram_workflow.yml`.

### Как запустить проект:
Клонировать репозиторий и перейти в него в командной строке:

```
git clone <https or SSH URL>
```

Перейти в корневую директорию
```
cd kittygram_final
```

Создать файл .evn для хранения ключей:

```
SECRET_KEY='указать секретный ключ'
ALLOWED_HOSTS='указать имя или IP хоста'
POSTGRES_DB: django_db
POSTGRES_USER: django_user
POSTGRES_PASSWORD: django_password
DB_NAME=kittygram
DB_HOST=db
DB_PORT=5432
```

Запустить docker-compose.production:

```
docker compose -f docker-compose.production.yml up
```

Выполнить миграции, сбор статики:

```
docker compose -f docker-compose.production.yml exec backend python manage.py migrate
docker compose -f docker-compose.production.yml exec backend python manage.py collectstatic
docker compose -f docker-compose.production.yml exec backend cp -r /app/collected_static/. /static/static/

```

Создать суперпользователя, ввести почту, логин, пароль:

```
docker compose -f docker-compose.production.yml exec backend python manage.py createsuperuser
```
