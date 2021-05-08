---
title: "Nomad Study Nomflix"
date: 2021-04-16T17:07:29+09:00
draft: true
---

## Add react-helmet

```
yarn add react-helmet
```

```javascript
import Helmet from "react-helmet";

<Helmet>
  <title>Movies | Nomflix</title>
</Helmet>;
```

## deploy github

gh-pages를 설치한다

```
yarn add gh-pages
```

package.json "deploy", "predeploy" 추가

homepage 추가

```
 "scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test",
    "eject": "react-scripts eject",
    "deploy": "gh-pages -d build",
    "predeploy": "yarn run build"
},
"homepage": "https://i-loveu.github.io/nomflix",
```

## deploy netlify
