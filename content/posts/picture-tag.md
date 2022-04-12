---
title: "Picture Tag"
date: 2022-04-12T13:21:37+09:00
draft: false
---

## Picture Tag

백그라운드 이미지는 css에서 처리하지만, img태그는 처리하기 어려웠다. 그런데 img태그도 html상에서 미디어 쿼리를 적용할 수 있는 태그가 있다.

```html
<picture>
  <source srcset="images/logo-sone.svg" media="(min-width:768px)" />
  <source srcset="images/logo-sone-m.svg" media="(max-width:767px)" />
  <img src="images/logo-sone.svg" alt="에스원" />
</picture>
```

`<picture></picture>` 태그로 묶고 그 안에 소스로 미디어쿼리 처리를 한다. 그리고 위 설정이 먹히지 않는 곳은 img 태그가 보이게 된다.
