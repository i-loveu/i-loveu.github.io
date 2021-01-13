---
title: "인스타그램 클론 V1"
slug: "Instargram Clone V1"
date: 2021-01-05T16:00:37+09:00
draft: true
---

```
yarn add graphql-yoga
```

> graphql 설치
>
> > GraphQLServer에는 express 서버가 내장

```
yarn add nodemon -D
yarn add babel-cli -D
yarn add @babel/{node,preset-env,core}
```

> nodemon, bebel-node 설치

```
npm install --save-dev @babel/node
```

> 혹시 babel-core와 babel-cli 버전 차이로 서버가 뜨지 않을 경우

```json
{
  "name": "prismagram",
  "version": "1.0.0",
  "repository": "git@github.com:i-loveu/prismagram.git",
  "author": "i-loveu <realife83@naver.com>",
  "license": "MIT",
  "dependencies": {
    "@babel/core": "^7.12.10",
    "@babel/preset-env": "^7.12.11",
    "dotenv": "^8.2.0",
    "graphql-yoga": "^1.18.3"
  },
  "devDependencies": {
    "@babel/node": "^7.12.10",
    "babel-cli": "^7.12.10",
    "nodemon": "^2.0.6"
  },
  "scripts": {
    "dev": "nodemon --exec babel-node src/server.js"
  }
}
```

> 서버 실행할 경우 $yarn dev

```js
require("dotenv").config();
import { GraphQLServer } from "graphql-yoga";

const PORT = process.env.PORT || 4000;

const typeDefs = `
  type Query {
    hello: String!
  }
`;

const resolvers = {
  Query: {
    hello: () => "Hi",
  },
};

const server = new GraphQLServer({ typeDefs, resolvers });

server.start({ port: PORT }, () =>
  console.log(`Server running on port http://localhost:${PORT}`)
);
```

> server.js 중간 커밋

```
yarn add morgan
```

> logger 설치

src/schema.js 파일 추가
