---
title: "Nomad Study Css Layout"
categories: ["nomadcoder"]
tags: ["study", "css"]
date: 2021-04-21T21:12:55+09:00
draft: true
---

## flex-box

flex-box는 무조건 item이 몇개가 있든 한 라인에 존재하게 한다.

넓이가 200px이어도 그 공간이 부족하면 구겨서 줄여버린다.

https://flexboxfroggy.com/ flex 요소 게임

`flex: 1 1 50%` => ` flex-grow: 1; flex-shrink: 1; flex-basis: 50%;``

`flex-grow: 1` 1의 비율로 넓이를 채워라

`flex-shrink: 1` 1의 비율로 줄어들어라

`flex-basis: 50%` 더 넓어질 수도 있지만, 기본 값은 50%

### flex-direction

`row` default 값 메인 축 값이 가로

`column` default 값 메인 축 값이 세로

`flex-direction: row-reverse` 가로 정렬 순서를 반대로 한다

`column-direction: row-reverse` 세로 정렬 순서를 반대로 한다

### justify-content

item은 개별 content는 전체

`justify-content: space-around` 모두 동일한 간격(결과적으로 시작과 끝은 오브젝트간 거리의 절반 간격)

`justify-content: space-evenly` 모두 동일한 간격 양끝까지 공간을 넣고 모두 동일한 공백

`justify-content: space-between` item을 시작과 끝에 두고 모두 동일한 간격

### align-self

`align-item` 과 비슷하지만, 자식 스스로 독자적으로 포지션을 정의한다.

`align-self: center` 세로축으로 중심에 혼자 선다

`align-self: flex-end` 세로축으로 끝에 혼자 선다

### plaxe-self

`plaxe-self: end center`

### order

`order`의 기본값은 0이다. 아무것도 쓰지 않아도 이미 `order: 0`을 갖고 있음으로 `order: 1`을 어딘가에 준다면 그것이 마지막으로 갈 것이다

### flex-wrap

기본값은 `nowrap`

`flex-wrap: wrap` child의 크기를 유지하고 넘치면 밑으로 떨궈라

`flex-wrap: wap-reverse` child 크기를 유지하고 row를 거꾸로 밑에서부터 왼쪽에서부터 채워라

### flex-flow

`flex-direction` 속성과 `flex-wrap` 속성을 함께 쓰는 것. Shor Cut

`flex-flow: column wrap;`

`flex-flow: flex-direction flex-wrap;` 첫번째가 flex-direction 두번째가 flex-wrap

### align-centent

align-items 는 하나의 줄에서의 정렬. align-centent 전체 여러줄의 정렬.

`align-content: flex-start` row 간 간격이 없다

`align-content: center` row 간 간격이 없이 세로 중간에 머문다

`align-content: space-between` row 간 간격이 시작과 끝에 붙어있다

`align-content: space-around` row 간 간격이 일정하게 떨어지며 그래서 시작과 끝은 간격의 절반이 된다

`align-content: baseline` 내용의 글자 높이를 맞춰 item 높이를 정렬한다

### flex-grow

기본 값은 0이며 shrink와 반대로 공간이 빌 경우 차지하며 늘어나는 비율을 얘기한다

빈 공간을 나눠가져가는 비율이다.

`flex-grow: 1` 늘려서 빈공간이 생길경우 늘어나며 채운다

### flex-shrink

flexbox가 쥐어 짜질때 어떻게 행동할 지 정한다

`flex-wrap: nowrap` 일 경우 넓이가 있어도 찌그러지는데 찌그러지는 비율 1이 기본이고 2면 기본보다 2배로 빨리 찌그러진다

### flex-basis

child에 적용되는 property. width와 비슷하지만, initial크기를 지정한다.

`flex-grow` `flex-shrink` 에서 찌그러지거나 늘어나기 전 기본 크기다

`flex-basis: 300px` 일 경우 기존적으로 넒이가 300px 처럼 보인다.

만약 `flex-direction: column` 일 경우 높이가 300px이 된다.

## GRID

대부분의 속성을 부모에서 지정한다

https://cssgridgarden.com grid Game

### grid-template-columns

`grid-template-columns: 1th-column-width 2th-column-width 3th-column-width 4th-column-width` column-width 를 지정한 만큼의 column을 갖는다

`grid-template-columns: repeat(4, 200px)` 200px 넓이의 column 4개

`grid-template-columns: 100px repeat(2, 200px) 100px` 100px, 200px 넓이의 column 2개, 100px

`grid-template-columns: auto 100px` 전체 넓이 - 100px, 100px // 전체 공간을 사용한다

### grid-template-rows

`grid-template-rows: 1th-rows-height 2th-rows-height 3th-rows-height 4th-rows-height` row-height 를 지정한 만큼의 row를 갖는다

`grid-template-rows: repeat(4, 200px)` 200px 높이의 row 4개

### column-gap

grid column간 거리

### row-gap

grid row간 거리

### gap

grid column row 거리

`gap: 1rem` grid 간격은 1rem의 간격을 갖는다

### grid-template-areas

template를 디자인하는 것.

```css
.grid {
  grid-template-areas:
    "header header header header"
    "content content content nav"
    "content content content nav"
    "footer footer footer footer";
}

.header {
  grid-area: header;
}

.content {
  grid-area: content;
}

.nav {
  grid-area: nav;
}

.footer {
  grid-area: footer;
}
```

grid-area에 해당하는 것은 "header" 이렇게 string으로 쓰면 안된다.

### grid-column-start

테이블 처럼 `grid-column-start: 1` 첫번째 라인에서 그리드가 시작해서 `grid-column-end: 3` 3번째라인에서 끝난다. 실제로는 2칸

### grid-column-end

그리드가 끝나는 시점

### grid-row-start

row 그리드가 시작하는 시점 줄

### grid-row-end

row 그리드가 끝나는 시점 줄

### grid-column

`grid-column-start: 1` `grid-column-end: 3` 을 아래와 같이 줄여서 쓸 수 있다

`grid-column: 1/3 `

`grid-column: 1/-1 ` 처음부터 끝까지

### grid-row

`grid-row-start:1 ` `grid-row-end: 3` 를 줄여 쓸 수 있다

`grid-row: 1/3 `

`grid-row: 1/-1 ` 처음부터 끝까지. 같은 뜻은 `grid-row: span 4`

`grid-row: 1/-2 ` 처음부터 뒤에서 2번째 라인까지

`grid-row: 2 / span 2 ` 2번 라인부터 처음부터 뒤에서 2개 칸을 차지하기

### grid naming

`grid-template-columns: [first-name] 100px [second-name] 200px [third-name] 150px `

### fr(fraction)

.grid width를 100% 로 가정하고 fraction 만큼 나눈다

```css
.grid {
  grid-template-columns: 1fr 1fr 1fr 1fr;
  grid-template-columns: repeat(4, 1fr);
}
```

위 두 개는 같은 것

### grid-template

```css
.grid {
  grid-template:
    "header header header header" 1fr -> row
    "content content content nav" 2fr
    "footer footer footer footer" 1fr / 1fr 1fr 1fr 1fr;
}

.header {
  grid-area: header;
}

.content {
  grid-area: content;
}

.nav {
  grid-area: nav;
}

.footer {
  grid-area: footer;
}
```

1fr -> row

1fr 1fr 1fr 1fr ->(height)

### justify-items

가로 채우기

`justify-items: stretch;` 모든 공간을 채워라 (기본갑)

`justify-items: start;` 내용물 공간 만큼

`justify-items: center;` 내용물 공간 만큼 중간

`justify-items: end;` 내용물 공간 만큼 끝에서

### align-items

세로 채우기

`align-items: stretch;` 모든 공간을 채워라 (기본갑)

`align-items: start;` 내용물 공간 만큼 세로로

`align-items: center;` 내용물 공간 만큼 중간

`align-items: end;` 내용물 공간 만큼 끝에서

### place-items

`place-items: start center ` 처음은 세로 그다음 가로 `align-items: start;` `justify-items: center;` 이것을 같이 쓴것

### place-content

`place-item`과의 차이는 전체 그리드의 정렬에 대한 것

```css
.grid {
  place-content: end center; // 세로 가로
}
```

### grid-auto-row

```css
.grid {
  grid-template-rows: repeat(4, 100px);
  grid-auto-rows: 100px;
}
```

row가 4줄 이상일 때는 자동으로 grid높이를 100px로 해라

### grid-auto-flow

초기 생각했던 것보다 item이 많아지면 column을 더 만들어라. 가로로 계속 만들어 지는것

`grid-auto-flow: row` 기본값

이렇게 되면 순서가 왼쪽에서부터 아래로 채워가며 번호가 매겨진다

```css
.grid {
  grid-template-columns: repeat(4, 100px);
  grid-template-rows: repeat(4, 100px);
  grid-auto-flow: column;
}
```

### minmax

```css
.grid {
  grid-template-columns: repeat(10, minmax(100px, 1fr));
  grid-template-rows: repeat(4, 100px);
  grid-auto-flow: column;
}
```

minmax(100px, 1fr) grid item 최소 넓이는 100px, 넘어가면 스크롤을 만들어라

### auto-fill

기본 넓이 100px을 가지고 남는 넙이 만큼 item을 만들어라

```css
.grid {
  grid-template-columns: repeat(auto-fill, minmax(100px, 1fr));
  grid-template-rows: repeat(4, 100px);
  grid-auto-flow: column;
}
```

### auto-fit

response와 관련이 있다. 넓이에 그리드 item 넓이를 조정해 화면 폭을 꽉 채운다

```css
.grid {
  grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
  grid-template-rows: repeat(4, 100px);
  grid-auto-flow: column;
}
```

### max-content

그리드 안의 컨텐트가 줄바꿈없이 꽉차는 크기

```css
.grid {
  grid-template-columns: max-content min-content;
}
```

### min-content

그리드 안의 컨텐트가 줄바꿈을 해서 item의 공간안에 내용을 채워서 작아질 수 있는 최소한의 크기

```css
.grid {
  grid-template-columns: max-content min-content;
}
```

```css
.grid {
  grid-template-columns: repeat(5, minmax(max-content, 1fr));
}
```

### 글씨 돌리기

```css
writing-mode: vertical-rl;
text-orientation: upright;
```

## SCSS
