---
title: "Flutter Functions"
slug: "Flutter Functions"
categories: ["flutter"]
date: 2023-03-09T11:44:23+09:00
draft: false
---

## link

`Navigator.of(context).push()` 유저가 이전 화면으로 돌아갈 수 있다.

`Navigator.of(context).pushAndRemoveUntil()` `(route)` 부분을 `false` return 하면 Route 히스토리가 사라진다. 그래서 이전 페이지로 가지 못한다.

```Dart
Navigator.of(context).push()

Navigator.of(context).pushAndRemoveUntil(
  MaterialPageRoute(
    builder: (context) => const NextScreen(),
  ), (route) {
return false;
});
```

## component

`FractionallySizedBox` 가능한한 큰 공간을 차지

### Timer.periodic

특정 시간마다 뭐나를 한다.

```dart
Timer.periodic(Duration(milliseconds: 500), (timer) {
  print(_animationController.value);
});
```