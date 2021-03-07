---
title: "Browser Local Storage"
slug: "Browser Local Storage"
categories: ["browser"]
tags: ["localstorage"]
date: 2021-03-03T10:38:31+09:00
draft: false
---

## 내 컴퓨터 브라우져에 저장하는 storage

{{< figure src="/images/browser-local-storage.png" alt="browser-local-storage position">}}

```javascript
localStorage.setItem("keyName", "value")
localStorage.getItem("keyName") -> "value"
```

localStorage는 오로지 String만 저장 가능하다. 

그래서 `JSON.stringify(Object)`를 사용해서 저장해준다.

다시 object 시킬경우 `JSON.parse(sringObject)`를 사용한다