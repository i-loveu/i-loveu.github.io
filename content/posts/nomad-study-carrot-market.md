---
title: "Nomad Study Carrot Market"
date: 2022-07-04T11:44:35+09:00
draft: true
---

## DATABASE SETUP

```
pscale connect tangotok
```

### Prisma Client

`libs/client.ts`

```javascript
import { PrismaClient } from "@prisma/client";

const client = new PrismaClient();
```

## REACT HOOK FORM

## AUTHENTICATION

### Token UI

```js
// schema prisma
model Token {
    user User @relation(fields: [userId], references: [id], onDelete: Cascade)
}
```

- Cascade
  User가 삭제되면 같이 삭제

- SetNull
  user가 삭제되어도 남겨둔다.

## 8. REFACTORING

### Paths

- tsconfig.json

```javascript
{
  "compilerOptions": {
    "baseUrl": ".",
    "paths": {
      "@libs/*": ["libs/*"],
      "@components/*": ["components/*"]
    }
  },
  "include": ["next-env.d.ts", "**/*.ts", "**/*.tsx"],
  "exclude": ["node_modules"]
}

```

## 9 AUTHENTICATION

### 9.7 Serverless Session

## 10 AUTHORIZATION

### 10.2 useUser Hook

```javascript
useEffect(() => {
  fetch("/api/users/me")
    .then((response) => response.json())
    .then((data) => {
      if (!data.ok) {
        return router.replace("/enter");
      }
      setUser(data.profile);
    });
}, [router]);
```

`replace("/enter");` 이전 페이지를 히스토리에 남기고 싶지 않다면 replace를 사용하자

### 10.4 useUser Refactor

```javascript

import {SWRConfig} from "swr;

function MyApp({Component, pageProps}: AppProps) {
  return (
    <SWRConfig
    value={{
      refreshInterval: 2000
      }}
    >
    </SWRConfig>
  )
}

```

`refreshInterval: 2000` 2초마다 데이터 리프래시

## 11 PRODUCTS

### 11.8 Bound Mutations

```javascript
const onFavClick = () => {
  mutate({ product: { name: "potato" } }, true);
};
```

뒤에 'true'가 데이터를 다시 불러들인다.

### 11.9 Unbound Mutations

```javascript
boundMutate((prev) => prev && { ...prev, isLiked: !prev.isLiked }, false);
mutate("/api/users/me", (prev: any) => ({ ok: !prev.ok }), false);
```

`boundMutate` 해당 화면에서 얻어온 데이터만 변경할 때

`mutate` 다른 화면의 데이터가 변경

마지막 `false` refetch하지 않는 것. `true`면 refetch

### 11.10 Counting Relationships

단지 Counting만 하고 싶다면 `_cound` 를 사용

```javascript
const products = await client.product.findMany({
  include: {
    _count: {
      select: {
        favs: true,
      },
    },
  },
});
```

`_counnt:` 를 넣으면 object를 끌고 오지 않고 Count만 한다.

## 12 동네생활

### 12.3 궁금해요

```javascript
const [wonder] = useMutation(`/api/posts/${router.query.id}/wonder`);
const onWonderClidk = () => {
  if (!data) return;
  mutate(
    {
      ...data,
      post: {
        ...data.post,
        _count: {
          ...data.post._count,
          ? data?.post._count.wondering -1
          : data?.post._count.wondering +1
        },
      },
    }
  );
  wonder({});
};
```

mutate

## PROFILE

### 13.0 Models

하나의 모델에 같은 유저가 다른이름으로

```javascript
model User {
  writtendReviews Review[] @relation(name: "writtendReviews")
  receivedReviews Review[] @relation(name: "receivedReviews")
}

model Review {
  id Int @id @default(autoincrement())
  createdAt DateTime @default(now())
  updatedAt DateTime @updatedAt
  review String @db.MediumText
  createdBy User @relation(name: "writtendReviews", fields: [createdById], references: [id], onDelete: Cascade)
  createdById Int
  createdFor User @relation(name: "receivedReviews", fields: [createdForId], references: [id], onDelete: Cascade)
  createdForId Int

}
```

## 15 CLOUDFLARE IMAGES

### 15.2 Direct Creator Uploads

중간 스톨리지(대게 우리 서버)를 거치지 않고 사용자가 직접 서버엥 이미지를 올리는 서비스

우리 서버에 파일을 올리고(#1) 우리가 다시 이미지서버에 파일을 전송(#2) 이 두가지 비용을 아낄 수 있고 사용자 입장에서의 속도도 더 빠르다.

## 16 NEXTJS IMAGES

### 16.0 Introduction

- image placeholder: 아주 작은 사이즈 흐릿한 이미지

### 16.1 Local Images

```javascript
import Image from "next/image";
import riceCake from "../publck/local.jpeg";

<Image src={riceCake} placeholder="blur" quality={5} />;
```

`import riceCake from "../publck/local.jpeg"; ` 이렇게 삽입하는 이유는 NextJs가 이미지를 만들어야 하기 때문

`placeholder='blur"` 미리 뿌옇게 사이즈가 낮은 이미지를 불러올 수 있다.

`quality={5}` 해당도 5%, 기본 75%정도.

### 16.2 Remote Images

```javascript
<Image
  width={48}
  height={48}
  src={`https://imagedelivery.net/V76-7iAY_27KmEkbZjRRPA/${user?.avatar}/avatar`}
/>
```

Remote이기 때문에 미리 `width, height 값을 요청하고 있다. 이것으로 미리 Remote에 요청해 이미지를 만들기 위해서다.

스크롤이 해당 포지션에 도착해에 이미지를 로딩하는 Lazy loading도 지원한다.

### 16.3 Layout Fill

#### css: object-fit

이미지를 백그라운드 처럼 위 relative div에 사이즈를 맞춰준다.

## 19 NEXT JS DEEP DIVE

### 19.2 Dynamic Import

화면에 보여질 때만 (display: block 영역일 때) 로딩.

앱을 다 만들고 최적화 할 때 만들자.

```javascript
import dynamic from "next/dynamic";

const Bs = dynamic(() => import("@components/bs"));
const Bs = dynamic(() => import("@components/bs"), { ssr: false });
```

`{ssr: false}` 서버 사이드 렌더링 하지 않게 한다.

### 19.3 Lozy-load Import

#### use loading:

```javascript
import dynamic from "next/dynamic";

const Bs = dynamic(() => import("@components/bs"));
const Bs = dynamic(() => import("@components/bs"), {
  ssr: false,
  loading: () => <span>loading yout compoent</span>,
});
```

#### use Suspense

```javascript
import dynamic from "next/dynamic";

const Bs = dynamic(() => import("@components/bs"));
const Bs = dynamic(() => import("@components/bs"), {
  ssr: false,
  suspense: true,
});

<Suspense fallback={"Loading something big"}>
  <Bs />
</Suspense>;
```

### 19.10 getStaticPropos

markdown 파일을 읽기 위한 https://www.npmjs.com/package/gray-matter 설치

`npm install --save gray-matter`

```javascript
import matter from "gray-matter";
```
