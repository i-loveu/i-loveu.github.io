---
title: "Deploy Github React to Netlify"
categories: ["github", "netlify"]
date: 2021-08-20T14:38:17+09:00
draft: true
---

# Github React Deploy To Netlify

```
npx create-react-app app-name
cd app-name
yarn build 
```


## settings

```
npm install netlify-cli -g
netlify deploy
```

`netlify deploy` 명령어를 치면 임시 url이 나온다. 배포해도 괜찮으면 `netlify deploy --prod`

### DNS 설정

A레코드를 75.2.60.5로 변경한다
