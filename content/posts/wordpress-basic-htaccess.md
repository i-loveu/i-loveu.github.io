---
title: "Wordpress 고유주소 수정 후 링크가 먹지 않을때 .htaccess"
slug: "Wordpress Basic Htaccess"
date: 2021-01-18T16:15:15+09:00
categories: ["wordpress"]
tags: ["htaccess"]
draft: false
---

## .htaccess 란?

hypertext access의 약자. Rewrite engine 기능을 사용하기 위해 많이 쓴다.
[워드프레스 .htacess 설명링크](https://wordpress.org/support/article/htaccess/)

## wordpress 고유주소 설정 실수로 사이트 링크가 먹지 않을 때

이 경우 서버의 .htaccess 내용이 지워졌을 가능성이 높습니다.

서버에 접근해서 아래의 코드로 업데이트 하면 해결될 수 있습니다.

```
# BEGIN WordPress

RewriteEngine On
RewriteRule .* - [E=HTTP_AUTHORIZATION:%{HTTP:Authorization}]
RewriteBase /
RewriteRule ^index\.php$ - [L]
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /index.php [L]

# END WordPress
```
