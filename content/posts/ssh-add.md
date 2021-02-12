---
title: "ssh-add 란?"
date: 2021-01-04T17:40:19+09:00
draft: false
---

## ssh-add 란?

ssh-agent에 개인키를 등록하는 명령어

```
ssh-add ./ssh/private_key
```

## ssh-agent란?

SSH key를 관리하는 도구

> 키 리스트를 보는 명령

```
ssh-add -l
```

> ssh-agent에서 전체 삭제 명령

```
ssh-add -D
```

> 키 등록 방법

```
ssh-add ~/.ssh/id_ras_name
```
