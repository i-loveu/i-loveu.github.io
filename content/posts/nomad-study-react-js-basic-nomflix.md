---
title: "Nomad Study React Js Basic"
date: 2021-05-11T21:54:55+09:00
draft: true
---

## React JS Basic

### 프로젝트 시작

`yarn global add create-react-app` create-react-app을 global에 넣어준다

`yarn global add npx` npx 명령어를 사용하기 위해 global에 등록

`npm i npx -g` npx를 global로 설치한다

`npx create-react-app nomflix`

### what is npx

npx 최신 버전을 다운 받아서 해당 모듈을 실행 후 삭제한다

### source에서 불필요 파익 삭제

`App.css, App.js, App.test.js, index.css, logo.svg, reportWebVitals` 삭제

`reportWebVitals` 리엑트 성능 측정을 위한 파일

### .env 생성

.env 파일에 다음과 같이 작성

```javascript
NODE_PATH = src;
```

### prop-types 설치

`yarn add prop-types`

### page title 변경

public/index.html

```
<title>React App</title>
to
<title>Nomflix</title>
```
