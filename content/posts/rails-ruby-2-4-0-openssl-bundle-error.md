---
title: "Rails Ruby 2 4 0 Openssl Bundle Error"
date: 2020-12-29T20:05:14+09:00
draft: false
---

## 새로 오픈한 유투브 채널 코딩병원

채널을 만들자 마자, 처방전 발급
[안태의 코딩병원](https://www.youtube.com/channel/UCk5P3qw9-Oy8l5fnxDF_CNA)

## 에러상황

rails s 나 bundler을 쳐도 먹히지 않는 먹통
아래와 같은 에러들이 줄줄

```
kernel_require.rb:55:in
dlopen(/)..
9): Library not loaded: /usr/local...
Reason: image not found - /Users/p..
openssl.bundle
```

## 해결책 1

루비를 다시 설치

```
rbenv uninstall 2.4.0
rbenv install 2.4.0
gem install bundler
```
