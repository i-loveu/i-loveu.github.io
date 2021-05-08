---
title: "Nomad Study Airbnb Clone"
categories: ["nomadcoder"]
tags: ["study", "python"]
date: 2021-04-12T15:41:07+09:00
draft: true
---

## Flask vs Django

### Flask

괭장히 작은 프레임워크. 데이터베이스, 이메일, 로그인, 로그아웃 등 모든 것을 다 만들어야 한다.

목표한 기능에 집중한다면 괜찮은 프레임워크

### Django

거대한 프레임워크. 이미 많은 유틸리티가 장착되어있다

Pinterest, instagram

## pipenv

python 환경을 설정하는 package

## python3 사용

`pipenv --three`

### Pipfile

packge-json과 같은 기능

## 장고 설치

```
pipenv she;l
pip install Django==2.2.5
```

## github

```
git branch -M main
```

## config파일 만들기

```
django-admin startproject config
move config Aconfig
mv Aconfig/* .
rm -rf Aconfig
```

## vs code extension 설치

`Python`

## python version 확인

{{<figure src="/images/python-version-check.png" alt="python version in VS code">}}

## flake8 linter 설치

.vscode > settings.json

```
"python.linting.flake8Enabled": true,
"python.linting.pylintEnabled": false,
"python.linting.enabled": true,
"python.formatting.provider": "black",
"python.linting.flake8Args": ["--max-line-length=88"]
```

```
pipenv install flake8 --dev
```

## formater 세팅

```
pipenv install black --dev --pre
```

## timezone change

settings.py

```
TIME_ZONE = "Asia/Seoul"
```

## server 띄우기

```
python manage.py runserver
ctrl + C
```

## migration

```
python manage.py migrate
```

## super user 만들기

```
python manage.py createsuperuser
```

## applicaitons 만들기

application 명령어는 복수여야 한다

room -> rooms

```
django-admin startapp rooms
django-admin startapp users
django-admin startapp reviews
django-admin startapp conversations
django-admin startapp lists
django-admin startapp reservations
```

## users > models.py AbstractUser import

users/models.py

```python
from django.contrib.auth.models import AbstractUser
from django.db import models

class User(AbstractUser):
    pass

```

## config/settings.py 에 추가된 model 적용

`delete db.sqlite3` 기존 db 삭제

config/settings.py

```python

DJANGO_APPS = [
    "django.contrib.admin",
    "django.contrib.auth",
    "django.contrib.contenttypes",
    "django.contrib.sessions",
    "django.contrib.messages",
    "django.contrib.staticfiles",
]

PROJECT_APPS = ["users.apps.UsersConfig"]

INSTALLED_APPS = DJANGO_APPS + PROJECT_APPS


AUTH_USER_MODEL = "users.User"

```

## database 생성 + Create Model User

```
python manage.py makemigrations
```

위 명령어를 치면 `users/migrations/0001_initial.py` 파일이 생김

아래 명령어로 마이그레이션 실행

```
python manage.py migrate
python manage.py runserver
```

마이그레이션 실행 후 서버 띄우기

## super user 만들기

```
python manage.py createsuperuser
```

## admin penel에 user 추가

users/admin.py

```python
from django.contrib import admin
from . import models

@admin.register(models.User)
class CustomUserAdmin(admin.ModelAdmin):
    pass
```

## user에 bio 추가

users/modals.py

```python
class User(AbstractUser):
    avatar = models.ImageField(null=True)
    gender = models.CharField(max_length=10, null=True)
    bio = models.TextField(default="")

```

`default=""` `null=True`기존 data가 있을 경우 어떻게 채울 것인지를 정의한다

```
python manage.py makemigrations
python manage.py migrate

```

## pipenv install Pillow

ImageField에 사용될 Pillow 설치

```
pipenv install Pillow
```

## mirgration

```
python manage.py makemigrations
python manage.py migrate
```

## form 을 위한 null 처리

`null=True` database를 위한 null 처리

`, blank=True` form validator를 위한 null 처리

```python
class User(AbstractUser):

    GENDER_MALE = "mail"
    GENDER_FEMALE = "female"
    GENDER_OTHER = "other"

    GENDER_CHOICES = (
        (GENDER_MALE, "mail"),
        (GENDER_FEMALE, "female"),
        (GENDER_OTHER, "other"),
    )

    avatar = models.ImageField(null=True, blank=True)
    gender = models.CharField(
        choices=GENDER_CHOICES, max_length=10, null=True, blank=True
    )
    bio = models.TextField(default="", blank=True)
```

## user admin.py 설명

```python
@admin.register(models.User)
class CustomUserAdmin(admin.ModelAdmin):
    pass

```

`@admin.register(models.User)` 이것과 `admin.site.register(models.User, CustomUserAdmin)` 은 같은 것

admin penel에서 User를 나타내라는 뜻

## admin user list에 칼럼 나타내기

users/admin.py

```python
@admin.register(models.User)
class CustomUserAdmin(admin.ModelAdmin):

    list_display = ("username", "gender", "language", "currency", "superhost")

```

## admin user list에 filter 추가

```python
@admin.register(models.User)
class CustomUserAdmin(admin.ModelAdmin):

    list_display = ("username", "gender", "language", "currency", "superhost")
    list_filter = ("superhost")
```

## admin penel 에 UserAdmin을 적용하자

위에껏은 지우고

```python
from django.contrib import admin
from django.contrib.auth.admin import UserAdmin
from . import models

# Register your models here.
@admin.register(models.User)
class CustomUserAdmin(UserAdmin):
    pass
```

이것을 하면 검색창이 포함된 유저 admin 패널이 나온다

## UserAdmin.fieldsets 합치기

```python
@admin.register(models.User)
class CustomUserAdmin(UserAdmin):
    fieldsets = UserAdmin.fieldsets + (
        (
            "Custom Profile",
            {
                "fields": (
                    "avatar",
                    "gender",
                    "bio",
                    "birthday",
                    "language",
                    "currency",
                    "superhost",
                )
            },
        ),
    )
```

Django UserAdmin 속성과 Custom으로 작성한 속성을 합친다

## DB 초기화

users/migrations 안에 있는 파일 삭제

db.sqlite3 삭제

users/models.py `null=True` 삭제

```python
avatar = models.ImageField(blank=True)
gender = models.CharField(choices=GENDER_CHOICES, max_length=10, blank=True)
bio = models.TextField(blank=True)
birthday = models.DateField(blank=True, null=True)
language = models.CharField(choices=LANGUAGE_CHOICES, max_length=2, blank=True)
currency = models.CharField(choices=CURRENCY_CHOICES, max_length=3, blank=True)
superhost = models.BooleanField(default=False)
```

## Rooms 만들기

settings.py 에 rooms 추가

```python
PROJECT_APPS = ["users.apps.UsersConfig", "rooms.apps.RoomsConfig"]
```

models.py

```python
from django.db import models

class Room(models.Model):

    pass
```

admin.py

```python
@admin.register(models.Room)
class RoomAdmin(admin.ModelAdmin):
    pass

```

## Core app 생성

```
django-admin startapp core
```

cores/models.py

```python
class TimeStampedModel(models.Model):
    created = models.DateTimeField(auto_now_add=True)
    updated = models.DateTimeField(auto_now=True)

    class Meta:
        abstract = True
```

`abstract = True` DB에 들어가지 않는 Database. 확장용 model
`auto_now_add=True` 생성할 때 추가
`auto_now=True` 저장할 때마다 업데이트

## Core model 적용

rooms/models

```python
class Room(core_models.TimeStampedModel):

    name = models.CharField(max_length=140)
    description = models.TextField()
```

## django-contries library 사용

```
pipenv install django-countries
```

settins.py THIRD_PARTY 에 django_countries 추가

```python
THIRD_PARTY_APPS = ["django_countries"]
```

rooms/models.py

```python
class Room(core_models.TimeStampedModel):
    name = models.CharField(max_length=140)
    description = models.TextField()
    country = CountryField()
    city = models.CharField(max_length=80)
    price = models.IntegerField()
    address = models.CharField(max_length=140)
    guests = models.IntegerField()
    beds = models.IntegerField()
    bedrooms = models.IntegerField()
    baths = models.IntegerField()
    check_in = models.TimeField()
    check_out = models.TimeField()
    instant_book = models.BooleanField(default=False)
    host = models.ForeignKey(user_models.User, on_delete=models.CASCADE)
```

`on_delete=models.CASCADE` user를 지우면 room도 지워진다

`on_delete=models.PROTECT` room을 소유하면 user를 지울 수 없다

`on_delete=models.SET_DEFAULT` room을 지우면 누구의 소유로 가게 하라

## Room 필드 연결시 보여줄 내용 설계

rooms/models.py

```python

class AbstractItem(core_models.TimeStampedModel):

    name = models.CharField(max_length=80)

    class Meta:
        abstract = True

    def __str__(self):
        return self.name


class RoomType(AbstractItem):
    pass

class Room(core_models.TimeStampedModel):
    room_type = models.ManyToManyField(RoomType, blank=True)

    def __str__(self):
        return self.name
```

## admin penel에 RoomType 추가

rooms/admin.py

```python
@admin.register(models.RoomType)
class ItemAdmin(admin.ModelAdmin):
    pass

```

## 같은 방법으로 Amenity, Facility, HouseRole 추가

rooms/admin.py

```python
@admin.register(models.RoomType, models.Facility, models.Amenity, models.HouseRole)
class ItemAdmin(admin.ModelAdmin):
    pass

```

## admin penel 에 나오는 이름 변경

`class Meta:` 를 이용하고 `verbose_name_plural`과 `verbose_name` 을 이용

```python
class Facility(AbstractItem):
    pass

    class Meta:
        verbose_name_plural = "Facilities"

class HouseRole(AbstractItem):
    pass

    class Meta:
        verbose_name = "House Role"

```

### verbose_name_plural

If this isn’t given, Django will use verbose_name + "s".

https://docs.djangoproject.com/en/3.1/ref/models/options/

### verbose_name

If this isn’t given, Django will use a munged version of the class name: CamelCase becomes camel case.

https://docs.djangoproject.com/en/3.1/ref/models/options/

### ordering

`ordering = ['-order_date']` -를 붙이면 역순 정렬이다

`ordering = ['name']` 알파벳 정렬

```python
class RoomType(AbstractItem):
    pass

    class Meta:
        verbose_name = "Room Type"
        ordering = ["-created"]

```

### photo model 만들기

```python
class Photo(core_models.TimeStampedModel):
    caption = models.CharField(max_length=80)
    file = models.ImageField()
    room = models.ForeignKey(Room, on_delete=models.CASCADE)

    def __str__(self):
        return self.caption

```

`ForeignKey` 설정을 "Room"으로 지정할 수 있다.

ForeignKey로 Room을 쓰려면 이전 코드에 class Room이 정의되어 있어야 한다

### Review Model 추가

config/PROJECT_APPS 에 추가

```python
PROJECT_APPS = [
    "core.apps.CoreConfig",
    "users.apps.UsersConfig",
    "rooms.apps.RoomsConfig",
    "reviews.apps.ReviesConfig",
]
```

reviews/models.py

```python
from django.db import models
from core import models as core_models

class Review(core_models.TimeStampedModel):
    """  Review Model Definition  """

    review = models.TextField()
    accuracy = models.IntegerField()
    communication = models.IntegerField()
    cleanliness = models.IntegerField()
    location = models.IntegerField()
    check_in = models.IntegerField()
    value = models.IntegerField()

    user = models.ForeignKey("users.User", on_delete=models.CASCADE)
    room = models.ForeignKey("rooms.Room", on_delete=models.CASCADE)

    def __str__(self):
        return f"{self.review} - {self.room}"

```

### Reservation Model 추가

reservations/models.py

```python
from django.db import models
from core import models as core_models


class Reservation(core_models.TimeStampedModel):

    """ Reservation Model Definition """

    STATUS_PENDING = "pending"
    STATUS_CONFIRMED = "confirmed"
    STATUS_CANCELED = "canceled"

    STATUS_CHOICES = (
        (STATUS_PENDING, "Pending"),
        (STATUS_CONFIRMED, "Confirmed"),
        (STATUS_CANCELED, "Canceled"),
    )

    status = models.CharField(
        max_length=12, choices=STATUS_CHOICES, default=STATUS_CONFIRMED
    )

    check_in = models.DateField()
    check_out = models.DateField()

    guest = models.ForeignKey("users.User", on_delete=models.CASCADE)
    room = models.ForeignKey("rooms.Room", on_delete=models.CASCADE)

    def __str__(self):
        return f"{self.room - {self.check_in}}"

```

reservations/admin.py

```python
from django.contrib import admin
from . import models


@admin.register(models.Reservation)
class ReservationAdmin(admin.ModelAdmin):
    """ Reservation Admin Definition """

    pass

```

config/settings.py PROJECT_APPS에 추가

```python

PROJECT_APPS = [
    "core.apps.CoreConfig",
    "users.apps.UsersConfig",
    "rooms.apps.RoomsConfig",
    "reviews.apps.ReviewsConfig",
    "reservations.apps.ReservationsConfig",
]
```

### lists add

settings에 lists 추가

config/settins.py

```python
PROJECT_APPS = [
    "core.apps.CoreConfig",
    "users.apps.UsersConfig",
    "rooms.apps.RoomsConfig",
    "reviews.apps.ReviewsConfig",
    "lists.apps.ListsConfig",
]

```

lists/models.py

```python
class LIst(core_models.TimeStampedModel):

    """ List Model Definitions """

    name = models.CharField(max_length=80)
    user = models.ForeignKey("users.USer", on_delete=models.CASCADE)
    rooms = models.ManyToManyField("rooms.Room", blank=True)

    def __str__(self):
        return self.name

```

lists/admin.py

```python
from django.contrib import admin
from . import models


@admin.register(models.List)
class ListAdmin(admin.ModelAdmin):

    pass

```

### add conversations

config/settings.py

```python
PROJECT_APPS = [
    "core.apps.CoreConfig",
    "users.apps.UsersConfig",
    "rooms.apps.RoomsConfig",
    "reviews.apps.ReviewsConfig",
    "lists.apps.ListsConfig",
    "conversations.apps.ConversationsConfig",
]
```

conversations/models.py

```python
from django.db import models
from core import models as core_models


class Conversation(core_models.TimeStampedModel):

    """ Conversations Definition """

    participants = models.ManyToManyField("users.User", blank=True)

    def __str__(self):
        return str(self.created)

""" self.created 는 tmxmfld 스트링 형식이 아니기 때문에 str()처리를 한다 """


class Message(core_models.TimeStampedModel):

    massage = models.TextField()
    user = models.ForeignKey("users.User", on_delete=models.CASCADE)
    conversation = models.ForeignKey(
        "Converstion", on_delete=models.CASCADE
    )

    def __str__(self):
        return f"{self.user} says: {self.text}"
```

conversations/admin.py

```python
from django.contrib import admin
from . import models


@admin.register(models.Message)
class MessageAdmin(admin.ModelAdmin):

    pass


@admin.register(models.Conversation)
class ConversationAdmin(admin.ModelAdmin):

    pass
```
