---
title: "Namad Study Vanilla Js"
date: 2021-04-23T11:47:23+09:00
draft: true
---

## nodad coder 스터디 메모 on Vanilla js

### Date()

https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Date

### localStorage

`localStorage.setItem(key, value);`

이렇게 쓰면 브라우져 `localStorage`에 저장된다.

`localStorage.getItem(key);` value가 return된다

### remove Ojbect element 

```javascript
static removePassword = ({ password, ...rest }) => rest;
```

...rest 요소는 나머지를 반환한다