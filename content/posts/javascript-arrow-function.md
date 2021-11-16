---
title: "Javascript Arrow Function"
date: 2021-09-04T09:56:55+09:00
draft: true
---

## 화살표 함수



### default Value

```javascript
const hello = (name = "ahntae") => {
  return "hello" + name;
};

const hello = (name = "ahntae") => "hello" + name;
```

"ahntae"라는 기본 값을 성의 할 수 있다.

위 아래 같은 기능
