---
title: "레일즈 로컬 세팅 mac"
slug: "Rails Setting Mac"
categories: ["rubyonrails"]
tags: ["rubyonrails", "ruby"]
date: 2021-02-16T16:52:30+09:00
draft: false
---

## rbenv 설치
brew로 설치 

```
brew install rbenv ruby-build
```
환경 변수 추가 

```
echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.zshrc
echo 'eval "$(rbenv init -)"' >> ~/.zshrc
```

루비 설치 


```
rbenv install --list // 설치 가능한 루비 버전 보기 
rbenv install 3.0.0
```
