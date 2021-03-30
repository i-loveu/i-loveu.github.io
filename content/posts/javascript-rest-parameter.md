---
title: "Javascript Rest Parameter"
slug: "Javascript Rest Parameter"
date: 2021-03-30T19:18:27+09:00
categories: ["javascript"]
tags: ["javascript_rest_parameters"]
draft: false
---

## 마지막 파라미터는 Rest 파라미터

```javascript
function myFun(a, b, ...manyMoreArgs) {
  console.log("a", a);
  console.log("b", b);
  console.log("manyMoreArgs", manyMoreArgs);
}

myFun("one", "two", "three", "four", "five", "six");

// Console Output:
// a, one
// b, two
// manyMoreArgs, [three, four, five, six]
```

앞에 명시한 파라미터를 제외한 것들을 묶어서 배열로 내보낸다
