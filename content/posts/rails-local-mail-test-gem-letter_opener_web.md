---
title: "레일즈 메일, 로컬 테스트를 위한 Gem : Letter_opener_web"
date: 2020-12-22T12:06:26+09:00
draft: false
---

## Gem file 추가

```
group :development do
  gem 'letter_opener_web', '~> 1.0'
end

$ bunlde install
```

## routes.rb 에 작성

```
mount LetterOpenerWeb::Engine, at: "/letter_opener" if Rails.env.development?

```

## config/environments/development.rb

```
config.action_mailer.delivery_method = :letter_opener_web
```

## server 접속

```
http://localhost:3000/letter_opener
```
