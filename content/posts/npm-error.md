---
title: "Npm Error"
slug: "Npm Error"
categories: ["npm"]
tags: ["error"]
date: 2021-05-19T18:19:27+09:00
draft: true
---

## Npm을 쓰면서 나는 에러 대처 법

### unable to resolve dependency tree

`npm install --save --legacy-peer-deps`

`--save` package.json 의 dependencies에 추가 하기 위한 것

`--legacy-peer-deps` 의존성에 맞게 상위 모듈을 다운그레이드 한다.

react의 경우 지금 사용하고 있는 버전과 개발될 때 사용한 버전이 달라 하부 의존 패키지를 설치하지 못하는 경우가 있다.

react의 버전을 낮춰 의존성을 맞추는 설치
