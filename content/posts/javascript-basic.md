---
title: "Javascript Basic"
date: 2021-09-04T10:37:33+09:00
draft: true
---

### Spread Operator

```javascript
const days = ["Mon", "Tue", "Wed"];
const otherDays = ["Thu", "Fri", "Sat", "Sun"];
```

위 두 Array를 합치고 싶다면 `...`를 사용해서 합치면 된다

```javascript
const week = [...days, ...otherDays];
```

오브젝트에서도 된다

```javascript
const obj1 = {
  first: "hi",
  second: "hello",
};

const obj2 = {
  third: "annyoung",
};

const objs = { ...obj1, ...obj2 };
```


### forEach 와 map, filter의 차이

forEach는 실행만 하며, map은 결과 배열을 return한다. filter는 조건에 맞는 배열을 return.

