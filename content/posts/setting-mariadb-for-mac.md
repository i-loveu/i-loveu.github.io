---
title: "맥에 mariaDB 설치하기"
slug: "Setting Mariadb for Mac"
categories: ["db"]
tags: ["mariaDB"]
date: 2021-02-16T14:44:22+09:00
draft: false
---

## brew install mariadb

```
brew install mariadb
mysql.server server
```

## root user 만들기

```
sudo mysql -u root

```
sudo 권한으로 db 접속 

```mysql 
ALTER USER 'root'@'localhost' IDENTIFIED BY 'NEW_USER_PASSWORD';
FLUSH PRIVILEGES;

```
저는 로컬 root는 비번을 제거 합니다. 


