---
title: "Ios Swiftui Weather"
date: 2021-06-21T20:17:27+09:00
draft: true
---

# SwiftUI Weather App

### resume

hot reloading

### ui 도구 모음

단축키 command + SHIFT + L

### Stack

Horizontal Stack - z 축

Vertical Stack

Z Stack

## ZStack 배경 깔기

### 파랑으로 깔기

```swift

struct ContentView: View {
    var body: some View {
        ZStack {
            Color(.blue)
                .edgesIgnoringSafeArea(.all)
        }
    }
}

```

`.edgesIgnoringSafeArea(.all)` m자 까지 덮는 배경

### gradient로 깔기

```swift
struct ContentView: View {
    var body: some View {
        ZStack {
            LinearGradient(gradient: /*@START_MENU_TOKEN@*/Gradient(colors: [Color.red, Color.blue])/*@END_MENU_TOKEN@*/, startPoint: /*@START_MENU_TOKEN@*/.leading/*@END_MENU_TOKEN@*/, endPoint: /*@START_MENU_TOKEN@*/.trailing/*@END_MENU_TOKEN@*/)
                .edgesIgnoringSafeArea(/*@START_MENU_TOKEN@*/.all/*@END_MENU_TOKEN@*/)
        }
    }
}
```

기본값

`.leading` 왼쪽

`.topLeading` 천정

`.trailing` 오른쪽

`.bottomLeading` 아래바닥

### SF Symbols

https://developer.apple.com/sf-symbols/

원하는 아이콘을 선택 한 후

`command + SHIFT + C`

```swift
 VStack {
    Image(systemName: "cloud.sun.fill")
        .renderingMode(.original)
        .resizable() // 사이즈를 꽉 채운다
        .frame(width: 180, height: 180)
}
```

### ExTractedView

`VStack` Command + 클릭

### text 안에 value 넣는 방법

`Text("\(temperature)")`

### Spacer()

공간을 적당히 띄워준다

```swift
HStack(spacing: 28) {
```

item 간격을 28만큼 띄운다

### Custom Color 사용 방법

1. Assets.xcassets 를 클릭
2. 하단 `+` 를 눌러서 `Color Set`

### .cornerRadius(3.0)

border-radius 와 같은 효과

### command + n => 새로운 파일 추가

### .toggle()

value를 반전 시킨다

```swift
@State private var isNight = false

Button {
    isNight.toggle()
} label: {
    WweatherButton(title: "Change Day Time", textColor: .blue, backgroundColor: .white)
}

```

### @Binding

상위에 있는 variable을 Binding 한다

```swift
BackgroundView(isNight: $isNight)

struct BackgroundView: View {
    
    @Binding var isNight: Bool

```


