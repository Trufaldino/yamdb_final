
# Добро пожаловать на проект yamdb_final!

![ Статус](https://github.com/altvik2503/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)

Привет! **yamdb_final** это приложение для обмена отзывами на различные произведения искусства, такие как фильмы, книги, музыка и т.д. Благодарные или возмущённые пользователи оставляют к произведениям текстовые отзывы и ставят произведению оценку в диапазоне от одного до десяти (целое число); из пользовательских оценок формируется усреднённая оценка произведения — **рейтинг**. На одно произведение пользователь может оставить только один отзыв. Добавлять отзывы, комментарии и ставить оценки могут только аутентифицированные пользователи. Проект выполнен в рамках обучающего курса Яндекс Практикум.


При пуше в ветку main автоматически отрабатывают сценарии:
1. Автоматический запуск тестов,
2. Обновление образов на Docker Hub,
3. Автоматический деплой на боевой сервер,
4. Отправка сообщения в телеграмм-бот в случае успеха.

## Начало работы

1. Клонируйте репозиторий на локальную машину.
```
git clone <адрес репозитория>
```
2. Для работы с проектом локально - установите вирутальное окружение и восстановите зависимости.
```
python -m venv venv
pip install -r requirements.txt 
```

### Подготовка удаленного сервера для развертывания приложения

Для работы с проектом на удаленном сервере должен быть установлен Docker и docker-compose.
Эта команда скачает скрипт для установки докера:
```
curl -fsSL https://get.docker.com -o get-docker.sh
```
Эта команда запустит его:
```
sh get-docker.sh
```
Установка docker-compose:
```
apt install docker-compose
```


## API


В проекте реализованы эндпоинты для взаимодействия с базой данных и возможностью создавать, редактировать и удалять не только отзывы, а также оставлять комментарии, данные передаются в формате **json**.

Полный список эндпоинтов можно получить по адресу http://127.0.0.1/redoc/ после развертки проекта локально.

Примеры:

Get-запрос на произведение

http://127.0.0.1/api/v1/titles/

    [
      {
        "count": 0,
        "next": "string",
        "previous": "string",
        "results": [
          {
            "id": 0,
            "name": "string",
            "year": 0,
            "rating": 0,
            "description": "string",
            "genre": [
              {
                "name": "string",
                "slug": "string"
              }
            ],
            "category": {
              "name": "string",
              "slug": "string"
            }
          }
        ]
      }
    ]

POST-запрос на произведение

http://127.0.0.1/api/v1/titles/

    {
      "name": "string",
      "year": 0,
      "description": "string",
      "genre": [
        "string"
      ],
      "category": "string"
    }

## Запуск проекта

1. Клонируйте проект с github по ssh

**git clone git@github.com:vv-m/api_yamdb.git**

2. При необходимости установите и активируйте виртуально окружение в директории проекта

**python3 -m venv venv**

**source venv/bin/activate**

3. Установите зависимости

**pip install -r requirements.txt**

4. Запустите процесс миграции (создания структуры базы данных)

**python manage.py migrate**

5. Запустите приложение

**python manage.py runserver**

В проекте предусмотрена возможность наполнения БД из фикстур, для импрорта введите команду **python manage.py import_db_2**

  

### Детали

Проект написан на **Python 3.7.0**, предусмотрена аутентификация по токену.

Использованы такие сторонние пакеты как:

1. **Django 3.2.16

2. djoser 2.1.0

3. djangorestframework-simplejwt 4.7.2

4. djoser**

Полный список зависимостей можно посмотреть в **requirements.txt**

Авторы проекта **Anton Ryadisnki**
