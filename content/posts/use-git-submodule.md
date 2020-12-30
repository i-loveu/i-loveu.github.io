---
title: "Use Git Submodule"
date: 2020-12-29T20:41:59+09:00
draft: false
---

## git submodule

서브 모듈은 git repository에 다른 git repository를 삽입 하기 위해 사용한다.

서브모듈이 포함된 레포지터리의 경우 --recursive 를 포함해서 clone을 해야한다.

```
git clone <repository> --recursive

```

이렇게 명령어를 쳐야 submodule까지 다운로드 된다.
