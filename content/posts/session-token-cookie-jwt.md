---
title: "Session Token Cookie Jwt"
date: 2021-10-04T14:24:40+09:00
draft: true
---

## Session

## token

서버가 기억하는 특이하게 생긴 텍스트, ID나 비밀번호 같은 것

## JWT

정보를 가지고 있는 토큰, DB없이 유효성 검증 가능

signed infomation

session이나 DB없이 유저를 인증한다

jwt는 암호화 되지 않는다

## session vs jwt

세션에 대한 모든 정보는 db에 저장

### redit

session 처리를 위한 저렴한 db

### useReducer

Reducer function을 다이렉트로 사용할 수 있게 하는 기능

state가 '변경' 되는 것이 아니고, state가 '대체'된다

```javascript
import { useReducer } from "react";
```

`useReducer` 는 [state, dispatch] 를 제공한다

`dispatch` function으로 reducer를 실행한다.
