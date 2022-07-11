---
title: "Flutter Make App Amazon Clone"
date: 2022-06-17T19:14:54+09:00
draft: true
---

## 목차

1. fultter install
2. `lib>constants>global_variables.dart` 만들기

global_variables.dart

```dart
import 'package:flutter/material.dart';

class GlobalVariables {
  static const appBarGradient = LinearGradient(
    colors: [
      Color.fromARGB(255, 29, 201, 192),
      Color.fromARGB(255, 125, 221, 216),
    ],
    stops: [0.5, 1.0],
  );

  static const secondaryColor = Color.fromRGBO(255, 153, 0, 1);
  static const backgroundColor = Colors.white;
  static const Color greyBackgroundCOlor = Color(0xffebecee);
  static var selectedNavBarColor = Colors.cyan[800]!;
  static const unselectedNavBarColor = Colors.black87;
}

```
