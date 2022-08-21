[![Django-app workflow](https://github.com/AxelVonReems/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg?branch=master)](https://github.com/AxelVonReems/yamdb_final/actions/workflows/yamdb_workflow.yml)

# Проект YaMDb

API для сервиса YaMDb - сбор отзывов пользователей на книги, фильмы и музыку.

## Описание проекта

Проект YaMDb собирает отзывы пользователей на произведения. Произведения делятся на категории: «Книги», «Фильмы», «Музыка». В каждой категории есть произведения: книги, фильмы или музыка. Произведению может быть присвоен жанр. Новые жанры может создавать только администратор. Пользователи могут оставить к произведениям текстовые отзывы и поставить произведению оценку в диапазоне от одного до десяти. Из пользовательских оценок формируется усреднённая оценка произведения — рейтинг. Присутствует возможность комментирования отзывов.

Функционал API:
1) Просмотр произведений (кино, музыка, книги), которые подразделяются по жанрам и категориям..
2) Возможность оставлять отзывы на произведения и ставить им оценки, на основе которых построена система рейтингов.
3) Комментирование оставленных отзывов.

Проект разработан командой из трех человек с использованием Git в рамках учебного курса Яндекс.Практикум.

## Стек технологий

Python 3.9
Django 2.2.16
Django REST Framework 3.12.4
Django REST Framework simplejwt 5.1.0

## Как запустить проект

Клонировать репозиторий и перейти в него в командной строке:

```
https://github.com/denielmay/yambd_final.git
```

Перейти в папку с проектом

```
cd yamdb_final
```

Cоздать и активировать виртуальное окружение:

```
WIN: python -m venv venv
MAC: python3 -m venv venv
```

```
WIN: source venv/scripts/activate
MAC: source venv/bin/activate
```

Установить зависимости из файла requirements.txt:

```
WIN: python -m pip install --upgrade pip
MAC: python3 -m pip install --upgrade pip
```

```
pip install -r requirements.txt
```

В папке infra создать и заполнить по образцу .env-файл:

```
DB_ENGINE=django.db.backends.postgresql - указываем, что работаем с postgresql
DB_NAME=postgres - имя базы данных
POSTGRES_USER=postgres - логин для подключения к базе данных
POSTGRES_PASSWORD=postgres - пароль для подключения к БД
DB_HOST=db - название сервиса (контейнера)
DB_PORT=5432 - порт для подключения к БД 
SECRET_KEY=ХХХХХХХХХХХХХХХХХ - секретный ключ проекта Django
DEBUG='False' - настройка дебаггера
```

Собрать и запустить контейнер с помощью Docker-compose:

```
docker-compose build
docker-compose up
```

Выполнить миграции через Docker-compose:

```
docker-compose exec web python manage.py makemigrations users  
docker-compose exec web python manage.py migrate --noinput
```

Собрать статику:

```
docker-compose exec web python manage.py collectstatic --no-input
```

Создать через Docker-compose суперпользователя:

```
docker-compose exec web python manage.py createsuperuser
```

Заполнить базу начальными данными:

```
docker-compose exec web python manage.py loaddata fixtures.json
```
