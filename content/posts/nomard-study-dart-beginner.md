---
title: "Nomard Study Dart Beginner"
date: 2022-12-27T18:51:34+09:00
draft: true
---

## VARIABLES

### Hello World

```dart
void main() {

}
```

### 1.3 Nullable Variables

다트는 기본적으로 null을 허용하지 않는다. 그러나 `?`를 붙이면 널이 될 수 있는 Variables로 인식된다

```dart
void mian() {
  String? name = 'ahntae';

  if(name != null) {
    name.isNotEmpty;
  }

  //or

  name?.isNotEmpty;
}
```

? 물음표는 if문을 만들수 있다.

### Final VAriables

javascript const와 같은 type `final`

```dart
void main() {
  final name = 'ahntae';
}
```

### Late Variables

값 없이 final 변수를 만들고 나중에 값을 정의하는 것.
보통 api에서 값을 반은 뒤 정의할 때 사용.

```dart

void main() {
  late final String name;
}
```

### Constant Variables

컴파일 할 때 값을 알고 있어야 하는 것.

```dart
void main() {
  const name = 'ahntae';
}
```

## DATA TYPES

### 2.1 Lists

```dart
void main() {
  List<int> numbers = [1,2,3,4];
  numbers.add(5);
  // or
  var numberss = [1,2,3,4];
}
```

### 2.3 Collection For

```dart
void main() {
  var oldFriends = ['nico', 'lynn'];
  var newFriends = [
    'ahntae',
    'jew',
    'karina',
    for (var friend in oldFriends) "my $freind",
  ];


  // prinnt

}
```

### 2.5 Sets

Set과 List의 차이는 Set은 모든 값이 Unique

```dart

void main() {
  Set<int> numbers = {1,2,3,4};

  numbers.add(1);
  numbers.add(1);
  numbers.add(1);
  numbers.add(1);
  print(numbers);

  // {1,2,3,4}
}
```

## 3 FUCTION

### 3.0 Defining a Function

`String num` 처럼 메소드 시작 부분에 리던 되는 값을 넣는다. 없으면 `void`

```dart
Sring sayHello(String poatato) => "Hello $potato nice to meet you";

num plus(num a, num b) => a + b;

void main() {
  print(sayHello('nico'));
}
```

### 3.1 Named Parameters

`reqiured`를 쓰거나 `default valu` 를 설정한다.

named parameters는 () 안에 중괄호를 넣는다 {}

```dart

String sayhello({
  String name = 'anno',
  int age = 19,
  String contry = 'wakanda'
}) {
  return 'hello $name you are $age from $contry'
}

or

String sayhello({
  required String name,
  required int age,
  required String contry,

}) {
   return 'hello $name you are $age from $contry'
}


void main() {
  sayhello()
}
```
