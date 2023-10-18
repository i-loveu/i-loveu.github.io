---
title: "Nomad Study Flutter for Beginners"
date: 2023-01-12T13:22:48+09:00
draft: true
---

## HELLO FLUTTER

### installation

https://docs.flutter.dev/get-started/install/macos 참고

### Running Flutter

1. extension 설치하기

## UI CHALLENGE

### 3.3 VSCode Settings

`shift + command + p` 를 누르고 `open user settings(JSON)`을 선택

```Json
  "dart.previewFlutterUiGuides": true
  "editor.codeActionsOnSave": {
    "source.fixAll": true
  },
```

`"editor.codeActionsOnSave"` 코드를 필요한 const를 추가하는 등 자동 수정
`"dart.previewFlutterUiGuides": true` 부모 라인을 보여준다

### 3.7 Icons and Transforms

`Icon(Icons.euro_rounded, color: Colors.white, size: 98)`

#### overflow: hidden 과 같은 효과

`clipBehavior: Clip.hardEdge`

## 4 STATEFUL WIDGETS

`StateLessWidget` 정적페이지 같은 것

### 4.0 State

### 4.4 Widget Lifecycle

```dart
  @override
  void initState() {
    // TODO: implement initState
    super.initState();
    print('init State!');
  }
```

`dispose` 위젯이 떨어질때

```dart
  @override
  void dispose() {
    // TODO: implement dispose
    super.dispose();
    print('dispose!');
  }

```

## 5 POMODORO APP

### 5.0 User Interface

`Flexible` flex 비율로 화면을 구성.

`Expanded` 자신이 속한 영역 전부를 채운다.

```dart
Column(
  children: [
    Flexible(
      flex: 1,
      child: Container(
        alignment: Alignment.bottomCenter,
        child: Text(
          '25:00',
        ),
      ),
    ),
    Flexible(
      flex: 2,
      child: Center(
      ),
    ),
    Flexible(
      flex: 1,
      child: Row(
        children: [
          Expanded(
            child: Container(
              decoration:
                  BoxDecoration(color: Theme.of(context).cardColor),
            ),
          ),
        ],
      ),
    ),
  ],
```

## WEBTOON APP

### 6.2 Data Feching

http 설치

file `pubspec.yaml` 에 아래 위치 삽입

```yaml
dependencies:
  flutter:
    sdk: flutter

  http: ^0.13.5
```

`lib`폴더에 `services`폴더 생성 `api_service.dart`파일 생성

```dart
import 'package:http/http.dart' as http;

class ApiService {
  final String baseUrl = 'https://webtoon-crawler.nomadcoders.workers.dev';
  final String today = "today";

  void getTodaysToons() {
    final url = Uri.parse('$baseUrl/$today');
    http.get(url);
  }
}

```

### 6.5 waitForWebToons

`ApiService` 폴더 생성

### 6.6 Futurebuilder

```dart

Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: Colors.white,
      appBar: AppBar(
        elevation: 2,
        backgroundColor: Colors.white,
        foregroundColor: Colors.green,
        title: const Text(
          "오늘의 웹툰",
          style: TextStyle(fontSize: 24),
        ),
      ),
      body: FutureBuilder(
        future: webtoons,
        builder: (context, snapshot) {
          if (snapshot.hasData) {
            return const Text("thers is data!");
          }
          return const Text("loading");
        },
      ),
    );
  }
```

### 6.7 ListView

`separatorBuilder` 리스트 item 사이에 원가를 해주는 빌더

```dart
body: FutureBuilder(
  future: webtoons,
  builder: (context, snapshot) {
    if (snapshot.hasData) {
      return ListView.separated(
        scrollDirection: Axis.horizontal,
        itemCount: snapshot.data!.length,
        itemBuilder: (context, index) {
          var webtoon = snapshot.data![index];
          return Text(webtoon.title);
        },
        separatorBuilder: (context, index) => const SizedBox(
          width: 20,
        ),
      );
    }
    return const Center(
      child: CircularProgressIndicator(),
    );
  },
),
```

### 6.8 WebToon Card

`Image.network(url)` Img 태그 같은 것

`clipBehavior: Clip.hardEdge,` BorderRadius를 적용하고 싶으면 `Clip.hardEdge` 요소를 추가해야 한다.

```dart
return Column(
  children: [
    Container(
      width: 250,
      clipBehavior: Clip.hardEdge,
      decoration: BoxDecoration(
        borderRadius: BorderRadius.circular(10),
      ),
      child: Image.network(webtoon.thumb),
    ),
    const SizedBox(
      height: 10,
    ),
    Text(
      webtoon.title,
      style: const TextStyle(
        fontSize: 22,
        fontWeight: FontWeight.w500,
      ),
    ),
  ],
);
```

### 6.9 Detail Screen

`onTap:` 유저가 Click했다는 뜻

### 6.10 Hero

페이지가 전화되어도 해당 위젯 부분은 애니메이션 되듯 화면으로 옮겨짐
`tag` 가 필요하다.

```dart
// 리스트
Hero(
  tag: id,
  child: Container(
    width: 250,
    clipBehavior: Clip.hardEdge,
    decoration: BoxDecoration(
        borderRadius: BorderRadius.circular(15),
        boxShadow: [
          BoxShadow(
            blurRadius: 15,
            offset: const Offset(10, 10),
            color: Colors.black.withOpacity(0.5),
          )
        ]),
    child: Image.network(thumb),
  ),

```

```dart
// 상세페이지
Hero(
  tag: id,
  child: Container(
    width: 250,
    clipBehavior: Clip.hardEdge,
    decoration: BoxDecoration(
        borderRadius: BorderRadius.circular(15),
        boxShadow: [
          BoxShadow(
            blurRadius: 15,
            offset: const Offset(10, 10),
            color: Colors.black.withOpacity(0.5),
          )
        ]),
    child: Image.network(thumb),
  ),
),

```

### Episodes

### Url Launcher

https://pub.dev/packages/url_launcher/install

`flutter pub add url_launcher` 터미널에 입력

ios면 Info.plist 에 아래를 넣어준다

```
<key>LSApplicationQueriesSchemes</key>
<array>
  <string>sms</string>
  <string>tel</string>
</array>
```

android면 AndroidManifest.xml 에 넣어준다

```
<!-- Provide required visibility configuration for API level 30 and above -->
<queries>
  <!-- If your app checks for SMS support -->
  <intent>
    <action android:name="android.intent.action.VIEW" />
    <data android:scheme="sms" />
  </intent>
  <!-- If your app checks for call support -->
  <intent>
    <action android:name="android.intent.action.VIEW" />
    <data android:scheme="tel" />
  </intent>
</queries>
```

### 6.17 Favorites

https://pub.dev/packages/shared_preferences/install

`flutter pub add shared_preferences` 휴대폰 저장 공간을 사용하는 패키지

```dart

class _DetailScreenState extends State<DetailScreen> {
  late Future<WebtoonDetailModel> webtoon;
  late Future<List<WebtoonEpisodeModal>> episodes;
  late SharedPreferences pref;

```
