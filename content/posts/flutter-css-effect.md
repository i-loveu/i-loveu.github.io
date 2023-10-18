---
title: "플루터 CSS같은 효과주는 코드"
slug: "Flutter Css Effect"
categories: ["flutter"]
date: 2023-01-30T12:49:26+09:00
draft: false
---

## Overflow: hidden

`clipBehavior: Clip.hardEdge`

```dart
 Container(
  clipBehavior: Clip.hardEdge, // 기본값은 Clip.none
)
```

`Clip.none` 넘쳐 흘러도 된다.

## position: relative

```dart
Transform.translate(
  offset: const Offset(-10, 10),
)
```

x축 -10pixel / y축 10pixel

## 콘텐츠 높이가 창의 크기를 넘을 때

`SingleChildScrollView `

```dart
body: SingleChildScrollView(
  child: Padding(
      padding: const EdgeInsets.symmetric(horizontal: 40),
      child: Column(
```

`body`를 `SingleChildScrollView`로 감싸줍니다.

## padding

```dart
padding: const EdgeInsets.symmetric(vertical: 20, horizontal: 20)
or
padding: const EdgeInsets.all(20)
```
