---
title: "Nomad Study Instarclone"
slug: "Nomad Study Instarclone"
date: 2021-05-25T12:58:35+09:00
draft: true
---

## Instagram Clone v3

## Setup

`npm init -y`

### vs code extention 'gitignore'

`command + shift + p` 커멘트 창을 띄우고 `add gitignore` 를 치고 `Node` 선택

### apollo-server graphql 설치

`npm i apollo-server graphql`

`touch server.js`

server.js

```javascript
const { ApolloServer, gql } = require("apollo-server");

const typeDef = gql`
  type Query {
    hello: String
  }
`;

const resolvers = {
  Query: {
    hello: () => "world",
  },
};

const server = new ApolloServer({
  typeDefs,
  resolvers,
});

server
  .listen()
  .then(() =>
    console.log(
      "Server is running apollo-server graphql http://localhost:4000 "
    )
  );
```

package.json

```javascript
{
  "scripts": {
    "dev": "node server.js"
  },
}

```

`node server.js` 명령 추가

#### nodemon 설치

코드가 수정될 때마다 서버를 재시작 하기 위함

`npm i nodemon --save-dev`

package.json 수정

```javascript
{
  "scripts": {
    "dev": "nodemon --exec node server.js"
  },
}

```

### Babel

https://babeljs.io/setup

https://babeljs.io/setup#installation

자바스크립트 컴파일러, 최신 javascript문법을 브라우져가 이해할 수 있도록 옛날 자바스크립트 문법으로 컴파일

`npm i --save-dev @babel/core`

`npm install @babel/preset-env --save-dev`

`touch babel.config.json`

babel.config.json 에 아래처럼 작성

```javascript
{
  "presets": ["@babel/preset-env"]
}
```

`@babel/preset-env` 최신 자바스크립트 문법을 사용할 수 있도록 계속 업데이트

`npm i @babel/node --save-dev`

### Prisma Setup

https://www.prisma.io/

프리즈마는 orm

`npm install prisma -D`

`npx prisma init`

postgressql 설치 https://postgresapp.com/

postgres 를 더블클릭 하고 아래 명령어를 실행한다

```
postgres=# create database instaclone;
CREATE DATABASE
postgres=#

```

pgadmin4 설치

https://www.postgresql.org/download/

서버가 없으면 생성

.env 파일 수정

```
DATABASE_URL="postgresql://user_name:randompassword@localhost:5432/your_db_name_maybe_instaclone?schema=public"
```

### Prisma Migration

prisma/schema.prisma

VScode extension Prisma 설치

Model Movie 생성

schema.prisma 파일에 설정

```javascript

datasource db {
  provider = "postgresql"
  url      = env("DATABASE_URL")
}

generator client {
  provider = "prisma-client-js"
}

model Movie {
  id        Int      @id @default(autoincrement())
  title     String
  year      Int
  genre     String?
  createdAt DateTime @default(now())
  updatedAt DateTime @updatedAt
}
```

`String?` ? 이 물음표는 null 가능하다는 것. 나머지는 반드시 필수 값(required)

migrate

`npx prisma migrate dev`

```
Enter a name for the new migration: init
```

init 이라고 친다

prisma/migrations 폴도 아래에 마이그레이션 파일이 생긴다

### Prisma Client

