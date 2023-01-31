
# Добро пожаловать на проект yamdb_final!

  

Привет! **yamdb_final** это приложение для обмена отзывами на различные произведения искусства, такие как фильмы, книги, музыка и т.д. Благодарные или возмущённые пользователи оставляют к произведениям текстовые отзывы и ставят произведению оценку в диапазоне от одного до десяти (целое число); из пользовательских оценок формируется усреднённая оценка произведения — **рейтинг**. На одно произведение пользователь может оставить только один отзыв. Добавлять отзывы, комментарии и ставить оценки могут только аутентифицированные пользователи. Проект выполнен в рамках обучающего курса Яндекс Практикум.

  

## API


В проекте реализованы эндпоинты для взаимодействия с базой данных и возможностью создавать, редактировать и удалять не только отзывы, а также оставлять комментарии, данные передаются в формате **json**.

Полный список эндпоинтов можно получить по адресу http://127.0.0.1/redoc/ после развертки проекта локально.

### Как запустить проект:

Клонировать репозиторий и перейти в него в командной строке:

```
git clone git@github.com:Trufaldino/infra_sp2.git 
```

```
cd infra
```

Развернуть докер контэйнеры:
```
sudo docker-compose up
```

Выполнить миграции и собрать статику
```
docker-compose exec web python manage.py migrate
docker-compose exec web python manage.py createsuperuser
docker-compose exec web python manage.py collectstatic --no-input
```

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

Авторы проекта **Anton Ryadisnki, Vlad Mironov, Mars Yamaletdinov**