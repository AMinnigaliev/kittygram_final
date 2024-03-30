https://github.com/AMinnigaliev/kittygram_final/actions/workflows/main.yml/badge.svg

# Проект Kittygram

## Описание

Kittygram — социальная сеть для обмена фотографиями любимых питомцев 
(котиков). Это полностью рабочий проект, который состоит из 
бэкенд-приложения на Django и фронтенд-приложения на React.

## Применяемые технологии

- **Язык программирования:** Python 3.9
- **Фреймворк для веб-разработки:** Django 3.2
- **Фреймворк для создания веб-API:** Django REST Framework 3.12
- **База данных:** PostgreSQL
- **Фронтенд:** HTML, CSS, JavaScript
- **Контейнеризация:** Docker
- **Управление многоконтейнерными приложениями:** Docker Compose
- **Система контроля версий:** Git

## Как развернуть проект

1. Установите Docker и Docker Compose для Linux на сервере
2. Скопируйте на сервер в директорию ***kittygram*** файл ***docker-compose.
   production.yml***
3. Создайте файл ***.env*** на сервере в директории ***kittygram***
4. В директории kittygram выполните команду `sudo docker compose -f 
   docker-compose.production.yml up -d `
5. Выполните миграции, соберите статические файлы бэкенда и скопируйте их в 
   ***/backend_static/static/***:
```
sudo docker compose -f docker-compose.production.yml exec backend python manage.py migrate
sudo docker compose -f docker-compose.production.yml exec backend python manage.py collectstatic
sudo docker compose -f docker-compose.production.yml exec backend cp -r /app/collected_static/. /backend_static/static/
```
PS: *Проект настроен на порт ***9000****

Содержание файл ***.env***:
- POSTGRES_DB - имя базы данных (для PostgreSQL. необязательный, при 
  отсутствии принимает значение *django*)
- POSTGRES_USER - имя пользователя (для PostgreSQL. необязательный, при 
  отсутствии принимает значение *django*)
- POSTGRES_PASSWORD - пароль пользователя (для PostgreSQL)
- DB_HOST - адрес, по которому Django будет соединяться с базой данных (для 
  PostgreSQL)
- DB_PORT - порт, по которому Django будет обращаться к базе данных (для 
  PostgreSQL. необязательный, при отсутствии принимает значение *5432*)
- SECRET_KEY - параметр SECRET_KEY для настройки Django (необязательный, 
  при отсутствии принимает значение *False*)
- DEBUG - параметр DEBUG для настройки Django (необязательный, 
  при отсутствии принимает случайное значение)
- ALLOWED_HOSTS - параметр ALLOWED_HOSTS для настройки Django 
  (необязательный, при отсутствии принимает значение *'127.0.0.1, localhost'*)
- USE_SQLITE - Использовать базу SQLite если значение ***True*** 
  (необязательный, при отсутствии принимает значение *False*)


### Авторы:
- Миннигалиев А.А.
- Яндекс Практикум