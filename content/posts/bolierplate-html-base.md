---
title: "기본 html에 대한 설명"
slug: "Bolierplate Html Base"
date: 2021-02-19T16:31:47+09:00
categories: ["html"]
tags: ["bolierplate"]
draft: false
---

## !DOCTYPE html

html 문서 버전중 html5에 해당한다는 정의입니다.

## html lang="ko"

컨텐츠에 포함되는 주 언어가 한국어라는 뜻입니다. 

## meta charset="utf-8

기본문자 인코딩 형식인 유니코드(UTF-8)

## meta name="viewport" content="width=device-width"

viewport: 화면 표시 영역(브라우져 크기) 

width=device-width: 화면 크기를 장치의 크기로 설정



```html
<!DOCTYPE html>
<html lang="ko">
    <head>
        <meta charset="utf-8">
        <meta name="viewport" content="width=device-width">
        <title>문서 제목</title>
    </head>
    <body>
        <p>이 문서는 HTML 문서입니다.</p>
    </body>
</html>
```
