---
title: "Cafe24로 네임서버 이전하기"
slug: "Migration to Cafe24name Server"
categories: ["wordpress"]
tags: ["server", "cafe24"]
date: 2021-01-28T16:36:32+09:00
draft: true
---

## 타사에서 산 도메인을 사용해서 카페24에서 호스팅하려면 name 서버를 이전해야 합니다.

- 웹호스팅 https://hosting.cafe24.com/ 죄측 하단에 지정해야할 네임서버를 확인합니다.
  보통은 아래와 같아요.

```
// 웹호스팅
1차 ns1.cafe24.com 175.125.93.134
2차 ns1.cafe24.co.kr 112.175.246.232
3차 ns2.cafe24.com 175.125.93.144
4차 ns2.cafe24.co.kr 112.175.247.232
```

### What is Name Server

네임서버는 도메인의 이름을 ip와 연결해주는 서버입니다.
보통 도메인을 구매하는 사이트에서 네임서버도 제공합니다.
