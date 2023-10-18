---
title: "Nomad Study Tictok Clone"
date: 2023-02-16T13:10:42+09:00
draft: true
---

## PROJECT SETUP

### 3.0 Initialization

`flutter create tictok_clone`

## 4. AUTHENTICATION

### 4.0 Sign Up Screen

`SafeArea` 그 안에 있는 모든 것은 특정 공간에 있을 것이라고 보장

이것을 쓰면 화면의 정보창 아래에서 시작

### 4.3 Sign Up Form

Private 메소드 만드는 방법 `_` 언더바를 쓴다.

```dart
void _onLoginTap(BuildContext context) {
  Navigator.of(context).push(
    MaterialPageRoute(
      builder: (context) => const LoginScreen(),
    ),
  );
}

```

### Username Screen

`TextField`을 할 때는 `_usernameController` 콘트롤러가 필요하고 아래 스타일 요소들이 있다.

```dart
extField(
  controller: _usernameController,
  cursorColor: Theme.of(context).primaryColor,
  decoration: InputDecoration(
    hintText: "Email",
    enabledBorder: UnderlineInputBorder(
      borderSide: BorderSide(
        color: Colors.grey.shade400,
      ),
    ),
    focusedBorder: UnderlineInputBorder(
      borderSide: BorderSide(
        color: Colors.grey.shade400,
      ),
    ),
  ),
),

```

### FromButton

`addListener` 뒤에는 `dispose` 해준다. `super.dispose();`는 마지막에 써준다.

```dart

@override
void initState() {
  // TODO: implement initState
  super.initState();

  _usernameController.addListener(
    () {
      setState(() {
        _username = _usernameController.text;
      });
    },
  );
}

@override
void dispose() {
  _usernameController.dispose();
  super.dispose();
}
```

### Email Screen

`keyboardType: TextInputType.emailAddress,` Email Type

```dart

keyboardType: TextInputType.emailAddress,
```

화면 터치해서 키보드 제거

```dart
void _onScaffoldTap() {
  FocusScope.of(context).unfocus();
}

@override
  Widget build(BuildContext context) {
    return GestureDetector(
      onTap: _onScaffoldTap,
      child: Scaffold(
        backgroundColor: Colors.
```

`TextField` 옵션 `onSubmitted:` and `onEditingComplete`

#### onSubmitted

값이 무엇인지 모를 때 유용히다.

#### onEditingComplete

매개변수 없이 실행

### 4.7 Password Screen

`Textfield`에 아이콘 넣기 1.

```dart
prefixIcon: const Icon(Icons.ac_unit),
suffixIcon: const Icon(Icons.access_alarm),

```

`Textfield`에 아이콘 넣기 2. - Widget 넣기

```dart
suffix: Row(
  mainAxisSize: MainAxisSize.min,
  children: [
    GestureDetector(
      onTap: _onClearTap,
      child: FaIcon(
        FontAwesomeIcons.solidCircleXmark,
        color: Colors.grey.shade400,
        size: Sizes.size20,
      ),
    ),
    Gaps.h16,
    FaIcon(
      FontAwesomeIcons.eye,
      color: Colors.grey.shade400,
      size: Sizes.size20,
    ),
  ],
),
```

비밀번호 처럼 보인는 TextField 옵션 `obscureText`

```dart
TextField(
  obscureText: true,
```

### 4.8 Birthday Screen

`CupertinoDatePicker`를 사용 `Cupertino` 애플 디자인 스타일

`mode` 옵션 `mode: CupertinoDatePickerMode.date` 사용

```dart
@override
Widget build(BuildContext context) {
  return Scaffold(
    backgroundColor: Colors.white,
    appBar: AppBar(
      elevation: 0,
      title: const Text(
        "Sign Up",
      ),
    ),
    body: Padding(),
    bottomNavigationBar: BottomAppBar(
      child: SizedBox(
        height: 300,
        child: CupertinoDatePicker(
          maximumDate: maximumDate,
          initialDateTime: maximumDate,
          mode: CupertinoDatePickerMode.date,
          onDateTimeChanged: _setTextFieldDate,
        ),
      ),
    ),

```

### 4.9 Login Form

`StatefulWidget` 사용 `FormState`를 사용해서 벨리데이션처리

```dart
class _LoginFormScreenState extends State<LoginFormScreen> {
  final GlobalKey<FormState> _formKey = GlobalKey<FormState>();

  Map<String, String> formData = {};

  void _onSubmitTap() {
    if (_formKey.currentState != null) {
      if (_formKey.currentState!.validate() != false) {
        _formKey.currentState!.save();
        print(formData);
      }
    }
  }
```

## ONBOARDING

### 5.1 Interest Screen

`Wrap` 위젯 - 넓이를 넘어가면 리스트를 아래로 떨구는 기능
`runSpacing` 높낮이 간격 `spacing` 좌우 간격

```dart
Wrap(
  runSpacing: 20,
  spacing: 20,
  children: [
    for (var interest in interests)
      Container(
        padding: const EdgeInsets.symmetric(
          vertical: Sizes.size12,
          horizontal: Sizes.size24,
        ),
        decoration: BoxDecoration(
          color: Colors.white,
          borderRadius: BorderRadius.circular(Sizes.size32),
          boxShadow: [
            BoxShadow(
              color: Colors.black.withOpacity(0.05),
              blurRadius: 5,
              spreadRadius: 5,
            ),
          ],
        ),
        child: Text(
          interest,
          style: const TextStyle(
            fontWeight: FontWeight.bold,
          ),
        ),
      ),
  ],
)

```

`SingleChildScrollView` 스크롤을 만드는 View

`border`

```dart

border: Border.all(
  color: Colors.black.withOpacity(0.1),
),

```

### 5.2 Scroll Animations

`Cupertino Button`

```dart
CupertinoButton(
  onPerssed: () {},
  child: Text("Next")
 )
```

`StatelessWidget` => `StatefulWidget` 변경

```dart
class _InterestsScreenState extends State<InterestsScreen> {
  final ScrollController _scrollController = ScrollController();

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text("Choose your interests"),
      ),
      body: SingleChildScrollView(
        controller: _scrollController,
```

initState, disposeState

```dart
  final ScrollController _scrollController = ScrollController();

  @override
  void initState() {
    // TODO: implement initState
    super.initState();
    _scrollController.addListener(() {
      print(_scrollController.offset);
    });
  }

  @override
  void dispose() {
    _scrollController.dispose();
    // TODO: implement dispose
    super.dispose();
  }


```

### 5.3 Tutorial Screen

`TabBarView` 는 `children`이 필요하다.

`TabBarView`는 `DefaultTabController` 가 필요하다.

```dart
return DefaultTabController(
  length: 3,
  child: Scaffold(
    body: SafeArea(
      child: TabBarView(
        children: [
          Padding(
            padding: const EdgeInsets.symmetric(
              horizontal: Sizes.size24,
            ),
            child: Column(
bottomNavigationBar: BottomAppBar(
  child: Container(
    padding: const EdgeInsets.symmetric(
      vertical: Sizes.size48,
    ),
    child: Row(
      mainAxisAlignment: MainAxisAlignment.center,
      children: const [
        TabPageSelector(
          color: Colors.white,
          selectedColor: Colors.black38,
        ),
      ],
    ),
  ),
),
```

### 5.4 AnimatedCrossFade

`onPanUpdate` 어느방향으로 스와이프 하는지 알 수 있다. `pan`

```dart
enum Direction { right, left }

enum Page { first, secend }

class TutorialScreen extends StatefulWidget {
  const TutorialScreen({super.key});

  @override
  State<TutorialScreen> createState() => _TutorialScreenState();
}

class _TutorialScreenState extends State<TutorialScreen> {
  Direction _direction = Direction.right;
  Page _showingPage = Page.first;

  void _onPanUpdate(DragUpdateDetails details) {
    if (details.delta.dx > 0) {
      setState(() {
        _direction = Direction.right;
      });
    } else {
      setState(() {
        _direction = Direction.left;
      });
    }
  }

  void _onPanEnd(DragEndDetails detials) {
    if (_direction == Direction.left) {
      _showingPage = Page.secend;
    } else {
      _showingPage = Page.first;
    }
  }
    return GestureDetector(
      onPanUpdate: _onPanUpdate,
      onPanEnd: _onPanEnd,
      child: Scaffold(
        body: SafeArea(
          child: AnimatedCrossFade(
            firstChild: Column(children: [
              Padding(
                padding: const EdgeInsets.symmetric(
                  horizontal: Sizes.size24,
                ),
            secondChild: Column(children: [
              Padding(
                padding: const EdgeInsets.symmetric(
                  horizontal: Sizes.size24,
                ),
            crossFadeState: _showingPage == Page.first
                ? CrossFadeState.showFirst
                : CrossFadeState.showSecond,
            duration: const Duration(
              milliseconds: 300,
            ),
```

## 6 TAB NAVIGATION

### BottomNavigationBar

```dart
int _selectedIndex = 0;

final screens = [
  const Center(
    child: Text("Home"),
  ),
  const Center(
    child: Text("Search"),
  ),
];

void _onTap(int index) {
  setState(() {
    _selectedIndex = index;
  });
}

Widget build(BuildContext context) {
  return Scaffold(
    body: screens[_selectedIndex],
    bottomNavigationBar: BottomNavigationBar(
      currentIndex: _selectedIndex,
      onTap: _onTap,
      selectedItemColor: Theme.of(context).primaryColor,
      items: const [
        BottomNavigationBarItem(
          icon: FaIcon(FontAwesomeIcons.house),
          label: 'Home',
          backgroundColor: Colors.amber,
        ),
        BottomNavigationBarItem(
          icon: FaIcon(FontAwesomeIcons.magnifyingGlass),
          label: 'Search',
          backgroundColor: Colors.blue,
        ),
      ],
    ),
  );
}
```

### NavigationBar

```dart
@override
Widget build(BuildContext context) {
  return Scaffold(
    body: screens[_selectedIndex],
    bottomNavigationBar: NavigationBar(
      selectedIndex: _selectedIndex,
      onDestinationSelected: _onTap,
      destinations: const [
        NavigationDestination(
          icon: FaIcon(
            FontAwesomeIcons.house,
            color: Colors.teal,
          ),
          label: "Home",
        ),
        NavigationDestination(
            icon: FaIcon(FontAwesomeIcons.magnifyingGlass), label: "Search"),
      ],
    ),
  );
}
```

## 6.5 Custom NavigationBar

```dart
Widget build(BuildContext context) {
  return Scaffold(
    bottomNavigationBar: BottomAppBar(
      color: Colors.black,
      child: Row(
        children: [
          Column(
            mainAxisSize: MainAxisSize.min,
            children: const [
              FaIcon(
                FontAwesomeIcons.house,
                color: Colors.white,
              ),
              Gaps.v5,
            ],
          )
        ],
      ),
    ),
  );
```

`mainAxisSize: MainAxisSize.min` 이것을 안하면 사이즈가 화면을 가득 채운다.

`NavTap`을 위젯으로 만든다.

```dart
NavTap(
  text: "Porfile",
  isSelected: _selectedIndex == 4,
  icon: FontAwesomeIcons.user,
  onTap: () => _onTap(4),
),
```

```dart
Widget build(BuildContext context) {
  return Expanded(
    child: GestureDetector(
      onTap: () => onTap(),
      child: Container(
        child: AnimatedOpacity(
          duration: const Duration(milliseconds: 300),
          opacity: isSelected ? 1 : 0.6,
          child: Column(
            mainAxisSize: MainAxisSize.min,
            children: [
              FaIcon(
                icon,
                color: Colors.white,
              ),
              Gaps.v5,
              Text(
                text,
                style: const TextStyle(color: Colors.white),
              )
            ],
          ),
        ),
      ),
    ),
  );
```

### 6.7 Stateful Navigation part

`Stack` 화면위에 쌓게 도와준다.

```dart
body: Stack(
  children: [
    Offstage(
      offstage: _selectedIndex != 0,
      child: const SftScreen(),
    )
  ],
),
```

## 7 VIDEO TIMELINE

### 7.1 Infinite Scrolling

`PageView` option `pageSanppering: false` -> 일정 부분 스크롤하면 페이지가 넘어가는 기능 사라잠

`PageView` 를 그대로 쓰면 전체 페이지 처음부터 만든다. 그래서 `PageView.builder`를 사용

```dart

class _VideoTimelineScreenState extends State<VideoTimelineScreen> {
  @override
  Widget build(BuildContext context) {
    return PageView(
      children: [
        Container(
          color: Colors.blue,
        ),
        Container(
          color: Colors.red,
        ),
        Container(
          color: Colors.yellow,
        ),
      ],
    );
  }
}

```

### 7.2 PageController

`curve` -> 애니메이션 효과

### 7.3 Video Player

`pubspec.yaml` 에 assets 추가

```yaml
assets:
  - assets/videos/video.MOV
```

https://pub.dev/packages/video_player 설치

추가

```yaml
# video_player: ^2.6.0 -> initialize() 버그
video_player: 2.4.1
```

### 7.4 VisibillityDetector

`visibility_detector` scroll 하는 와중에 플레이 되지 않도록

```dart
@override
  Widget build(BuildContext context) {
    return VisibilityDetector(
      key: Key("${widget.index}"),
      onVisibilityChanged: (info) => {
        print(info.visibleFraction),
      },
```

`info.visibleFraction` Widget이 얼마나 보이는지를 나타내는 0이상 1이하 범위의 수

```dart
  void _onVisibilityChanged(VisibilityInfo info) {
    if (info.visibleFraction == 1 && !_videoPlayerController.value.isPlaying) {
      _videoPlayerController.play();
    }
  }

  @override
  Widget build(BuildContext context) {
    return VisibilityDetector(
      key: Key("${widget.index}"),
      onVisibilityChanged: _onVisibilityChanged,
```

`IgnorePointer` 해당 영역을 무시하고 뒤 영역을 터치할 수 있다.

```dart
const Positioned.fill(
  child: IgnorePointer(
    child: Center(
      child: FaIcon(
        FontAwesomeIcons.play,
        color: Colors.white,
        size: Sizes.size52,
      ),
    ),
  ),
),
```

### 7.5 AnimationController

`AnimationController` button 애니메이션을 위해

```dart
class _VideoPostState extends State<VideoPost>
    with SingleTickerProviderStateMixin {

  @override
  void initState() {
    // TODO: implement initState
    super.initState();
    _initVideoPlayer();

    _animationController = AnimationController(
      vsync: this,
    );
  }
```

`_animationController.reverse();` upperBound -> lowerBound

`_animationController.forward();` lowerBound -> upperBound

```dart
  @override
    void initState() {
      super.initState();
      _initVideoPlayer();

      _animationController = AnimationController(
        vsync: this,
        lowerBound: 1.0,
        upperBound: 1.5,
        value: 1.5,
        duration: _animationDuration,
      );

      _animationController.addListener(() {
        setState(() {});
      });
    }

  void _onTogglePause() {
    if (_videoPlayerController.value.isPlaying) {
      _videoPlayerController.pause();
      _animationController.reverse();
    } else {
      _videoPlayerController.play();
      _animationController.forward();
    }
    setState(() {
      _isPaused = !_isPaused;
    });
  }
  Positioned.fill(
    child: IgnorePointer(
      child: Center(
        child: Transform.scale(
          scale: _animationController.value,
          child: AnimatedOpacity(
            opacity: _isPaused ? 1 : 0,
            duration: _animationDuration,
            child: const FaIcon(
              FontAwesomeIcons.play,
              color: Colors.white,
              size: Sizes.size52,
            ),
          ),
        ),
      ),
    ),
  ),
```

`setState(() {});` 를 쓰는게 1차 방법

### 7.6 AnimatedBuilder

`setState(() {});` 를 쓰지않고 `AnimatedBuilder`를 사용

```dart
@override
void initState() {
  super.initState();
  _initVideoPlayer();

  _animationController = AnimationController(
    vsync: this,
    lowerBound: 1.0,
    upperBound: 1.5,
    value: 1.5,
    duration: _animationDuration,
  );
  // _animationController.addListener(() {
  //   setState(() {});
  // });
}
Positioned.fill(
  child: IgnorePointer(
    child: Center(
      child: AnimatedBuilder(
        animation: _animationController, // _animationController 실행될 때 이것을 진행ㄴ
        builder: (context, child) {
          return Transform.scale(
            scale: _animationController.value,
            child: child, // child 아래 것을 적용
          );
        },
        child: Transform.scale(
          scale: _animationController.value,
          child: AnimatedOpacity(
            opacity: _isPaused ? 1 : 0,
            duration: _animationDuration,
            child: const FaIcon(
              FontAwesomeIcons.play,
              color: Colors.white,
              size: Sizes.size52,
            ),
          ),
        ),
      ),
    ),
  ),
),

```

### 7.7 SingleTickerProviderStateMixin

`vsync` 위젯이 안보일 때 사용하지 않게 하는 것 `vsync`를 상용하려면 `SingleTickerProviderStateMixin` 필요

`AnimationController`가 여러개면 `TickerProviderStateMixin` 사용

### 7.8 Vidoe UI

```dart
_videoPlayerController.setLooping(true);
```

## 8 COMMENTS SECTION

### 8.3 Text Input Actions

`textInputActino: TextInputAction.newLine,` 가상 키보드의 done을 enter로 바꿔줌

```dart
textInputActino: TextInputAction.newLine,
```

Input창에 여러줄로 쓰기위한 설정

```dart
  TextField(
    expends: true,
    minLines: null,
    maxLines: null,
  )
```

## 9 DISCOVER

### 9.0 Introduction

AspecRatio 이미지를 특정한 비율로 보여줄 수 있도록 하는 위젯. 이미지를 항상 가로로 할지, 세로로 할지, 아니면 영화비율, 정사각형, 직사각형으로 할지 정하는 것.

### 9.3 GridView

`gridDelegate` contorller 같지만 도움이 같은것

```dart
body: TabBarView(children: [
          GridView.builder(gridDelegate: gridDelegate, itemBuilder: itemBuilder,)
        ]),
```

### 9.5 CupertinoSearchTextField

`resizeToAvoidBottomInset` 키보드가 올라올 때 body 사이즈 리사이징

```dart
  Widget build(BuildContext context) {
    return DefaultTabController(
      length: tabs.length,
      child: Scaffold(
        resizeToAvoidBottomInset: false,

```

`keyboardDismissBehavior` 키보드 사라지게 하는 옵션

```dart

body: TabBarView(
  children: [
    GridView.builder(
      keyboardDismissBehavior: ScrollViewKeyboardDismissBehavior.onDrag,
```

## 10 INBOX

### 10.1 RichText

`splashColor` 버튼을 누르면 파처럼 퍼지는 애니메이션 제거

```dart
theme: ThemeData(
  primaryColor: const Color(0xffe9435a),
  scaffoldBackgroundColor: Colors.white,
  splashColor: Colors.transparent,
```

## 12 USER PROFILE

### 12.6 TabBar

`FractionallySizedBox`는 father의 너비와 높이에 의존해서 너비와 높이를 가진다.

### 12.7 PersistentTabBar

`NestedScrollView` SliverAppBar, TabBar를 사용하는 경우 사용

`headerSliverBuilder`

### 12.8 Conclusions

```dart
if(!mounted) return;
```

컴포넌트가 마운트 되지 않으면 튕겨내기

## 13 SETTINGS

`CircularProgressIndicator.adaptive()` iso android인지 구분해서 로깅 애니메이션 적용

```

```

### 13.1 AboutThisTitle

`ListTitle` 이 여플이 사용 중인 모든 오픈 소스 소프트웨어 라이센스 보여줌

## 13.4 CupertinoAlertDialog

```dart
CupertinoAlertDialog(
  title: Text("Are you sire?"),
  content: Text("Plz dont go"),
  actions: [
    CupertinoDialogAction(
      onPressed: () => Novigator.of(conteent).pop(),
     )
  ]

)
```

## 13.5 CupertinoActionSheet

## 14 RESPONSIVE FLUTTER WEB

### 14.1 OrientationBuilder

```dart
void main() async {
  WidetsFlutterBinding.ensureInintialized();

  await SystemChrome.setPreferredOrientations(
    [DeviceOrientation.portraitUp]
  );

  runApp(const TikTokApp());
}
```

### 14.2 kIsWeb

`kIsWeb` 아 앱이 웹에서 작동하도록 되어 있는지 파악. 이경우 영상 볼륨을 0으로 해야 자동 재생이 허락된다. 인스타그램도 웹에서는 무음으로 재생.

```dart
if (kIsWeb) {
 await _videoPlayerController.setVolume(0);
}
```

### 14.3 LayoutBuilder

내부 `Container`의 최대 크기를 알려준다.

```dart
body: LayoutBuilder(
  builder: (context, constraints) => Container (
    width: constraints.maxWidth,
    height: constraints.maxheight,
  )
)

```

## 15 DARK MODE

### 15.2 TextTheme

```dart

theme:
```

### 15.4 Typography

font, color만 제공하는 TextTheme

```dart
textTheme: Typography.whiteMountainView,

```

### 15.9 Concolusion

https://pub.dev/packages/flex_color_scheme 다트모드 라이트모드에 관한 기본 색상 정의

`flutter pub add flex_color_scheme`

```dart
class MyApp extends StatelessWidget {
  const MyApp({Key? key}) : super(key: key);
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      // The Mandy red, light theme.
      theme: FlexThemeData.light(scheme: FlexScheme.mandyRed),
      // The Mandy red, dark theme.
      darkTheme: FlexThemeData.dark(scheme: FlexScheme.mandyRed),
      // Use dark or light theme based on system setting.
      themeMode: ThemeMode.system,
      home: const MyHomePage(title: 'Flutter Demo Home Page'),
    );
  }
}

```

## 16 APP TRANSLATION

번역 섹션

### 16.1 Localizations

pubspec.yaml

```dart
dependencies:
  flutter_localizations:
    sdk: flutter
  intl: any
```

강제로 해당 화면의 언어 바꾸는 방법

```dart
@override
Widget build(BuildContext context) {
  return Localizations.override(
    content: context,
    locale: const Locale("es"),
    child: Scaffold(
      appBar: Scaffold(

      )
    )
  )
}

```

## 17 NAVIGATOR DEEP DIVE

### 17.1 await push()

push method는 future 다.

```dart

void _onLoginTap(BuildContext context) async {
  final result = await Navigator.of(context).push(
    MatrialPageRoute(
      builder: (content) => const LoginScreen(),
    ),
  );
  print(result);

}

// 단순히 다시 화면으로 돌아왔다는 뜻
void _onLoginTap(BuildContext context) async {
  await Navigator.of(context).push(
    MatrialPageRoute(
      builder: (content) => const LoginScreen(),
    ),
  );
  print("user came back");

}
```

### 17.3 pushNamed

```dart
  Navigator.of(context).pushNamed("/username);
```

main.dart에 routes 설정

```dart
  initialRoute: "/",
  routes: {
    "/": (context) => SignUpScreen(),
    "/usernmae": (context) => const UsernameScreen(),
    "/login": (context) => const LoginScreen(),
  }
```

```dart
void _onLoginTap(BuildContext context) async {
  Navigator.of(context).pushNamed("/login");
}

```

비슷한 방식으로

```dart
class SignUpScreen extends StatelessWidget {
  static String routeName = "/";
}

```

main.dart

```dart
initialRoute: SignUpScreen.routeName,
  routes: {
    SignUpScreen.routeName: (context) => SignUpScreen(),
    "/usernmae": (context) => const UsernameScreen(),
    "/login": (context) => const LoginScreen(),
  }

```

```dart
void _onLoginTap(BuildContext context) async {
  Navigator.of(context).pushNamed(LoginScreen.routeName);
}
```

### 17.4 pushNamed Arg

pushNamed에 Arg를 전송

```dart
Navigator.pushNamed(
  context,
  EmailScreen.routeName,
  arguments: EmailScreenArgs(username: _username)
);

```

email_screen.dart

```dart
Widget build(BuildContext context ) {
  final args = ModalRoute.of(context)!.settings.arguments as EmailScreenArgs;
}

Text(
  "What is your email, ${args.username}"
)

```

## 18 NAVIGATOR2

### 18.1 GoRouter

router.dart

```dart
final router = GoRouter(
  routes: [
    GoRoute(
      path: SignUpScreen.routeName,
      builder: (context, state) => const SignUpScreen(),
    ),
    GoRoute(
      path: LoginScreen.routeName,
      builder: (context, state) => const LoginScreen(),
    ),
    GoRoute(
      path: EmailScreen.routeName,
      builder: (context, state) {
        final args = state.extra as EmailScreenArgs;
        return const EmailScreen(username: args.username );
      },
    ),
    GoRoute(
      path: "users/:username",
      builder: (context, state) {
        final username = state.parmas['username'];
        final tab = state.queryParams["show"];
        return UserProfileScreen(username: username!, tab: tab!);
      },
    ),
  ]
)
```

### 18.3 queryParams

```dart
context.push(EmailScreen.routeName, extra: EmailScreenArgs(username: _username),
)'
```

### 18.4 CustomTransitionPage

```dart
final router = GoRouter(
  routes: [
    Goroute(
      name: SingUpScreen.routename,
      path: SignUpScreen.routeURL,
      builder: (context, state) => const SignUpScreen(),
      routes: [
        GoRoute(
          path: UsernameScreen.routeURL,
          name: UsernameScreen.routeName,
          builder: (context, state) => const UsernameScreen(),
          routes: [
            GoRoute(
              name: EmailScreen.routeName,
              path: EmailScreen.routeURL,
              builder: (context, state) {
                final args = state.extra as EmailScreenArgs;
                return EmailScreen(username: args.username);
              }
            )
          ]
        )
      ]
    )
  ]
)
```

## 19 VIDEO RECORDING

### 19.1 Introduction

여기서 휴대포으로 테스트 할 수 있는 방법이 나온다.

`flutter pub add camera` 카메라 패키지 실행

`/android/build.gradle` 여기서

```dart

if (flutterRoot == null) {
  <!-- 삭제 -->
    throw new GradleException("Flutter SDK not found. Define location with flutter.sdk in the local.properties file.")
  <!-- 삭제 끝 -->
}

defaultConfig {
        // TODO: Specify your own unique Application ID (https://developer.android.com/studio/build/application-id.html).
        applicationId "com.example.tictok_clone"
        // You can update the following values to match your application needs.
        // For more information, see: https://docs.flutter.dev/deployment/android#reviewing-the-gradle-build-configuration.
        minSdkVersion flutter.minSdkVersion
        minSdkVersion 21
        targetSdkVersion flutter.targetSdkVersion
        versionCode flutterVersionCode.toInteger()
        versionName flutterVersionName
    }
```

```dart
    minSdkVersion flutter.minSdkVersion -> 이걸
    minSdkVersion 21 -> 이것으로 변경
```

권한을 요청하는 패키지 `permission_handler`설치

`flutter pub add permission_handler`

or

```dart
dependencies:
  permission_handler: ^10.2.0
```

### 19.2 CameraController

```dart

Future<void> initPermissions() async {
  final cameraPermission = await Permission.camera.request();
  final micPermission = await Permission.microphone.request();

  final cameraDenied = cameraPermission.isDenied || cameraPermission.isPermanentlyDenied;
  final micDenied = micPermission.isDenied || micPermission.isPermanentlyDenied;

  <!-- isPermanentlyDenied -> 영구적 물어보지마 -->
  <!-- isDenied -> 일단 거절 -->

  if(!cameraDenied && !micDenined) {

  }
}

@override
void initState() {
  super.initState();
  initPermissions();
}

@override
Widget build(BuildContext context) {
  return Scaffold(
    backgroundColor: Colors.black,
    body: _hasPermission
      ? null
      : Column(
        children: const [
          Text("Requesting permissions..."),
          Gaps.v20,
          CircularProgressIndicator.adaptive()
        ]
      )
  )
}
```

### 19.5 Recording Animation

onTap: 눌렀다 떼는 것

onTapDown: 놀러있는 것
onTapUp: 손을 떼는 것


### 19.6 startVideoRecording

```dart

Future<void> initCamera() async {
  if(camera.isEmpty) {
    return;
  }

  _cameraController = CameraController(
    cameras[_isSelfieMode ? 1 : 0], 
    ResolutionPreset.ultraHigh,
  );

  await _cameraController.initalize();

  await _cameraController.prepareForVideoRecording(); 

  _flashMode = _cameraController.value.flashMode;
}

```

`await _cameraController.prepareForVideoRecording(); ` ios에서 필요한 세팅 이걸 안하면 소리와 영상 싱크가 안맞을 수 있따. 


### 19.9 AppLifecycleState

카메라를 쓰다가 앱을 종료하면 카메라를 제거 해야한다. 

`didChangeAppLifecycleState()`

```dart
class _VideoRecordingScreenState extends State<VideoRecordingScreen> with TickerProviderStateMixin, WidgetsBindingObserver {

  @override
  void initState() {
    super.initState();
    WidgetsBinding.instance.addObserver(this);
  }

  @override
  void didChangeAppLifecycleState(AppLifesyscleState state async {
    if (!_hasPermission) return;
    if (!_cameraController.value.isInitialized) return;
    if(state == AppLifecycleState.inactive) {
      _cameraController.dispose();
    } else if (state == AppLifecycleState.resumed) {
      initCamera();
    }
  }

  Future<void> initCamera() async {
    setState(() {});
  }

}

```

### 19.10 Code Challenge 

손가락으로 누르고 있는 상태에서 위로 올려서 줌을 하고 줌 아웃을 한다. 

추천 카메라 라이브러리 cameraAwesome
https://pub.dev/packages/camerawesome 


## 20 STATE MANAGEMENT

### 20.1 _noCamera 

사진 접근 권한 
ios > Runner > Info.plist

```
<key>NSPhotoLibraryUsageDescription</key>
<string>Plz let me see your photos</string>

```

가로모드를 지우려면

```
<key>UISupportedInterfaceOrientations</key>
<array>
  <string>UIInterfaceOrientationPortrait</string>
  <string>UIInterfaceOrientationLandscapeLeft</string> // 얘네를 지우면 됨
  <string>UIInterfaceOrientationLandscapeRight</string>// 얘네를 지우면 됨
</array>
<key>UISupportedInterfaceOrientations~ipad</key>
<array>
  <string>UIInterfaceOrientationPortrait</string>
  <string>UIInterfaceOrientationPortraitUpsideDown</string>
  <string>UIInterfaceOrientationLandscapeLeft</string> // 얘네를 지우면 됨
  <string>UIInterfaceOrientationLandscapeRight</string> // 얘네를 지우면 됨
</array>

```

시물레이터에 영상 넣고 싶으면 drag & drop하면 된다. 그냥 바탕화면 상태에서 하면 된다. 

### 20.2 Router Part One

GoRouter 와 Navigator 1.0을 같이 쓴다. 

GoRouter는 URL로 접근할 수 있는 페이지. 

Navigator 1.0 은 Password 입력 창 처럼 URL이 바뀌지 않고 화면만 빠뀌는 페이지를 적용한다. 

### 20.11 Provieder 
pubspec.yaml에 가서 아래 버전 dependencies에 넣는다. 

```
provider: 6.0.5 
```


## 21 MVVM WITH PROVIDER 

`WidgetsFlutterBinding.ensureInitialized();` 얘를 적어야 `SharedPreferences`를 할 수 있었다. 


## 22 RIVERPOD

### 22.0 Introduction

pubspec.yaml에 가서 아래 버전 dependencies에 넣는다. 

'flutter_riverpod: ^2.4.0'

### 22.1 NotifierProvider 

```dart 
final darkModeConfigProvider =
    NotifierProvider<DarkModeConfigViewModel, DarkModeConfigModel>(
  () => throw UnimplementedError(),
);

```

`throw UnimplementedError()` 이것을 한 이유는 main.dart의

`final preferenses = await SharedPreferences.getInstance();` 이것 때문, API에서 받는 다면 이것이 필요 없다. 


## 23 FIREBASE SETUP

### 23.1 Installration

https://firebase.google.com/docs/cli?hl=ko#install-cli-mac-linux 

`curl -sL https://firebase.tools | bash` cli 설치 한 번만 하면 된다. 

그다음 터미널에 `firebase login` 

`dart pub global activate flutterfire_cli` 명령어 치기 

`flutterfire configure` 명령어 치기 

`iso, android, web` 만하기 

`flutter pub add firebase_core` 명령어 치기 

`flutterfire configure` 한번 더 치고 기존 만들었던 것 선택 

`flutter pub add firebase_auth` 로그인 플러그인 설치 

`flutter pub add cloud_firestore` 

`flutter pub add firebase_storage`

main.dart에 아래 내용 추가 

```dart
void main() async {
  await Firebase.initializeApp(
    options: DefaultFirebaseOptions.currentPlatform,
  );
```

### 23.3 AuthenticationRepository 

로그인 안했을 경우 리다이렉트 설정 

router.dart 에 아래부분을 넣는다. 

```dart
  redirect: (context, state) {
    final isLoggedIn = ref.read(authRepo).isLoggedIn;
    if (!isLoggedIn) {
      if (state.uri != Feed.routeName) {
        return Feed.routeName;
      }
    }
    return null;
  },

```

## 25 USER PROFILE

### 25.0 Introduction 

파이어베이스로 가서 기존에 만들었던 테스트 User를 없앤다

그리고 Cloude Firestore 생성

서울지역을 선택한 다음 Storage 활성화 한다 

### 25.2 UserProfileModel 

firebase_auth는 로그인한 본인만 접근 가능. 그래서 email같은 외부 노출 정보는 별도 데이터베이스를 만들어야 한다. 

### 25.5 AvatarViewModel

아바타를 올리는 것만 따로 뽑는다.

`flutter pub add image_picker` 이미지 피커 패키지 설치 

## 26 VIDEO UPLOAD

### 26.2 uploadVideoProvider 

```dart

Future<void> uploadVideo(File video) async {
    final user = ref.read(authRepo).user;
    state = AsyncValue.loading();
    state = await AsyncValue.guard(() async {
      final task = await _repository.uploadVideoFile(
        video,
        user!.uid,
      );
      if (task.metadata != null) {
        await _repository.saveVideo(VideoModel(
            title: "From Fultter!",
            description: "hello yeah!",
            fileUrl: task.ref.getDownloadURL(),
            thumbnailUrl: "", // 얘는 Cloud Function이 파일 URL을 가지고 만든다.
            creatorUid: creatorUid,
            likes: likes,
            comments: comments,
            createdAt: createdAt,
            creator: creator));
      }
    });
  }
```
