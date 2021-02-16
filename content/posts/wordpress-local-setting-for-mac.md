---
title: "맥에서 워드프레스 로컬세팅하기"
slug: "Wordpress Local Setting for Mac"
date: 2021-02-16T14:25:00+09:00
categories: ["wordpress"]
tags: ["htaccess"]
draft: false
---

## wp-cli 설치

```
brew install wp-cli
```
wp cli 설치 
```
wp core download
```
wordpress 다운로드 
## db 세팅
```
mysql -uroot
create database db_name charset=utf8mb4;

```

## wp 서버 띄우기

```
wp server
```



