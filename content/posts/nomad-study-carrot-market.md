---
title: "Nomad Study Carrot Market"
date: 2022-07-04T11:44:35+09:00
draft: true
---

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
