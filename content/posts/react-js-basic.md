---
title: "Javascript Basic"
slug: "Javascript Basic"
categories: ["javascript"]
tags: ["es6"]
date: 2021-03-07T16:21:32+09:00
draft: false
---

## Arrow Functions 

Arrow Function(=>)은 return이 기본적으로 정의되어 있다. 

```javascript
const arrowFunction = name => "hello" + name;
console.log(arrowFunction) -> "hello name"
```


## Object Destructuring 

```javascript

const human {
    firstName: "taeseong",
    lastName: "ahn",
    nationality: "korea"
}

const { firstName, lastName, nationality: national} = human;

console.log(firstName, lastName, national);
```

## Spread Operator 

```javascript
const days = ["mon", "tue", "wed"];
const otherDays = ["Thu", "Fri", "Sat"];

const allDays = [...days, ...others, "Sun"];

console.log(allDays); // ["mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"]


const ob {
    first: "hi",
    second: "hello"
};

const oob {
    third: "third"
}

const combine = {...ob, ...oob};

console.log(combine) // Object {first: "hi", second: "hello", third: "bye bye"}
```

## map

모든 요소에 fucntion을 실행하고 array를 반환한다 

```javascript
const days = ["Mon", "Tue", "Wed", "Thur", "Fri"];

const result = days.map((day, index) => `my ${day}`);

console.log(result) // ["my Mon", "my Tue", "my Wed", "my Thur", "my Fri"]
```

## filter 

모든 요소에 fucntion을 실행하고 true 일 경우 배열에 포함시킨다 

```javascript

const numbers = [1,2,3,4,5,6,3,34,22,44,56,43];

const fillteredNum = numbers.filter(num => num > 15);

console.log(fillteredNum); // 
```

## includes 

포함여부를 확인해서 boolean 리턴 

```javascript

let iTsYou = ["you", "are", "so", "beautiful"]

if(!iTsYou.includes("perfact!")) {
    iTsYou.push("perfact!");
}

console.log(iTsYou); // ["you", "are", "so", "beautiful", "perfact!"]

```