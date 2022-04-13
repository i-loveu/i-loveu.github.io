---
title: "Svg Font Not Working on Safari"
date: 2022-04-13T12:27:24+09:00
tags: ["svg", "custom font", "safari"]
draft: false
---

## SVG 폰트가 사파리에서 안될 때!!

```html
<text
  data-name="Noto Sans"
  transform="translate(520 348)"
  style="fill:#00c8b4;font-family:NotoSansKR-Bold,Noto Sans KR;font-weight:700;font-size:20px"
  ><tspan x="-60.44" y="0">Noto Sans</tspan></text
>
```

대략 위와 같은 NotoSansKR폰트가 사파리에서는 그냐 sarif 폰트로 나온다면!

아래와 같이 바꿔준다.

```html
<text
  data-name="Noto Sans"
  transform="translate(520 348)"
  font-family="NotoSansKR, sans-serif"
  style="fill:#00c8b4;font-weight:700;font-size:20px"
  ><tspan x="-60.44" y="0">Noto Sans</tspan></text
>
```

`font-family="NotoSansKR, sans-serif"`이 부분으로 `style="font-family:NotoSansKR-Bold,Noto Sans KR;"`에서 꺼내준다.
이렇게 하면 적용 완료!
