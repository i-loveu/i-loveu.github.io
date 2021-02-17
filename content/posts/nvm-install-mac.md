---
title: "nvm 맥에 설치하기 - homebrew"
slug: "Nvm Install Mac"
categories: ["node"]
tags: ["nvm"]
date: 2021-02-17T16:12:01+09:00
draft: false
---

## homebrew로 nvm 설치 

```
brew install nvm
```

.zshrc에 환경변수 등록 
```
export NVM_DIR="$HOME/.nvm"
source $(brew --prefix nvm)/nvm.sh
```

.zshrc 재실행
```
source .zshrc
```


## node 설치 

https://nodejs.org/ko/ 여기서 안정적 버전을 선택한다 

```
nvm install 14.15.5
```

