---
title: "Ie ReplaceAll Change This"
categories: ["ie"]
date: 2021-05-27T13:41:07+09:00
draft: false
---

## replaceAll 대신 replace(/target/gi, "")

```javascript
$this.text().replaceAll(",", ""); // 이것 대신

$this.text().replace(/,/gi, ""); // 이것을 쓰자
```

정규식 gi옵션을 포함해서 All 대체

`g`: 모든 조건 검색

`i`: 대/소문자 구분안함
