---
title: "CSS Flex 속성이란?"
slug: "About Css Flex"
categories: ["css"]
tags: ["flex"]
date: 2021-01-21T08:31:24+09:00
draft: true
---

여기 내용 다 채우기 https://heropy.blog/2018/11/24/css-flexible-box/

## Flex 속성이란?

크게 container, items 두가지 영역에 해당한다

`Container: display, flex-flow, justify-content`

`Items: order, flex, align-self` 등의 속성이 있다.

## Item: flex 값에 대한 해석

`flex: 1` -> 모든 공간을 사용 가능하다

<div style="display: flex; height: 100px;">
  <div style="flex:1; background-color: #ddd;"">flex: 1</div>
</div>

```html
<div style="flex:1">flex: 1</div>
```

> 화면 전체가 꽉 찬다

<div style="display: flex; height: 100px;">
  <div style="flex:1; background-color: #ddd;"">flex: 1</div>
  <div style="flex:1; background-color: #eee;"">flex: 2</div>
</div>

```html
<div style="flex:1">flex: 1</div>
<div style="flex:1">flex: 2</div>
```

> 화면 전체가 각각 1:1 반반씩 찬다

<div style="display: flex; height: 100px;">
  <div style="flex:1; background-color: #ddd;"">flex: 1</div>
  <div style="flex:2; background-color: #eee;"">flex: 2</div>
</div>

```html
<div style="flex:1">flex: 1</div>
<div style="flex:2">flex: 2</div>
```

> 각각 1:2 비율로 갖는다.
