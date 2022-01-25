---
title: "Study Fast Api"
date: 2021-07-28T14:11:47+09:00
draft: true
---

## 설치 방법

### fast api install with pipevn

`pipenv install fastapi`

### uvicorn install with pipenv

`pipenv install fastapi uvicorn`

### run server

`uvicorn main:app --reload`

### sqlalchemy 설치

`pipenv install fastapi-sqlalchemy`

## 기본 서비스

### Swagger

RESTful API를 json으로 만들어준다

http://127.0.0.1:8000/docs

### ReDoc

OpenAPI 규정으로 문서를 만들어준다

http://127.0.0.1:8000/redoc

### Open Api Json

json 파일을 한땀 한땀 떠준다

http://127.0.0.1:8000/openapi.json

## folder

### config.py

#### @dataclass

딕셔너리 형태고 사용하기 위해 사용

```python
@dataclass
```

## plugin

### EmailStr 사용하기 위한 'pydantic'

`command + ,`를 누르고 설치

### JSON 웹 토큰을 쓰기위한 'pyjwt'

### 암호화를 위한 `bcrypt`