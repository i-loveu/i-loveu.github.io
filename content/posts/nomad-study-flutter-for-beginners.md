---
title: "Nomad Study Flutter for Beginners"
date: 2023-01-12T13:22:48+09:00
draft: true
---

## HELLO FLUTTER

### installation

https://docs.flutter.dev/get-started/install/macos 참고

### Running Flutter

1. extension 설치하기

## UI CHALLENGE

### 3.3 VSCode Settings

`shift + command + p` 를 누르고 `open user settings(JSON)`을 선택

```Json
  "dart.previewFlutterUiGuides": true
  "editor.codeActionsOnSave": {
    "source.fixAll": true
  },
```

`"editor.codeActionsOnSave"` 코드를 필요한 const를 추가하는 등 자동 수정
`"dart.previewFlutterUiGuides": true` 부모 라인을 보여준다

### 3.7 Icons and Transforms

`Icon(Icons.euro_rounded, color: Colors.white, size: 98)`

#### overflow: hidden 과 같은 효과

`clipBehavior: Clip.hardEdge`
