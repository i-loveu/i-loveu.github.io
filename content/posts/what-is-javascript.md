---
title: "자바스크립트란?"
slug: "What Is Javascript"
date: 2021-02-18T20:11:57+09:00
 
draft: false
---

## 유일한 브라우져 언어

웹에서 사용할 수 있는 유일한 언어다

## Vanilla Javascript

원형 그대로의 자바스크립트를 말한다. 자바스크립트를 편하게 사용하기 위해 미리 만들어 놓은 jQery와 같은 라이브러리들이 있다. 


## Variable(변수)

변수란 

`Camel Case` 낙타등처럼 글씨를 붙여서 쓰지만, 대문자로 단어를 구분하는 것 camelCase 첫 문자는 소문자로 사용

### function-scoped

`var` variable, 

### block-scoped

`let` 변수가 바뀌어도 상관없다면 사용.

`const`constant 상수라는 뜻. 정의된 후에는 바꿀 수 없다.


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