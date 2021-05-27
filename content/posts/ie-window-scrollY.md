---
title: "Window ScrollY Ie11"
categories: ["ie"]
date: 2021-05-27T13:30:19+09:00
draft: false
---

## window.scrollY IE undefined

window.pageYOffset 를 사용한다

```javascript
function isIE() {
  const ua = window.navigator.userAgent;
  const msie = ua.indexOf("MSIE ");
  const trident = ua.indexOf("Trident/");
  return msie > 0 || trident > 0;
}
if (isIE()) {
  var fromTop = window.pageYOffset;
} else {
  var fromTop = window.scrollY;
}
```
