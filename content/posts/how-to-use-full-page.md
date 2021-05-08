---
title: "How to Use Full Page JS"
slug: "How to Use Full Page JS"
categories: ["js-library"]
tags: ["pullpagejs"]
date: 2021-01-28T13:33:37+09:00
draft: false
---

## fullpage.js

https://alvarotrigo.com/fullPage/pricing/

스크롤을 fullpage로 적용할 때 유용하다. 무료는 v2 버전이고 `scrollOverflow` 기능에 제한이 있는 등 9유로이니 구매해서 v3 버전을 쓰는 것이 맞다.

### fullpage.js v2 부족한 점

`scrollOverflow` 높이 제한 문제

중간에 스크롤이 필요한 높이의 경우 `scrollOverflow: true` `scrolloverflow.min.js` 를 쓰게 되는데 v2를 쓰고 있다가 높이가 짤려서 이유를 모르고 버그가 있는줄 황당해 하며
시간을 버린 경우가 있다. v3는 해당 문제가 없다.
