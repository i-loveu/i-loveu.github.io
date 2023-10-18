---
title: "Nomad Study Flutter Animations Masterclass"
date: 2023-10-03T20:36:12+09:00
draft: true
---

## IMPLICIT ANIMATIONS

### 1.0 Project Setup

### 1.1 Implicit

'Animated' 를 붙이면 애니메이션 효과를 준다 

### 1.2 AnimatedContainer

### 1.4 TweenAnimationBuilder

tween 값을 줘서 애니메이션을 만든다. 


## 2 EXPLICIT ANIMATIONS

### 2.1 AnimationController 

```dart
  @override
  void initState() {
    // TODO: implement initState
    super.initState();
    Ticker(
      (elapsed) => print(elapsed),
    ).start();
  }
```

`Ticker` 애니메이션 프레임당 1번씩 호출됨

`with SingleTickerProviderStateMixin ` -> 사용자 화면에 떠 있을 경우만 호출. 

`animationController` 는 0 -> 1로 움직인다. 

### 2.3 AnimatedBuilder

```dart

  late final Animation<Color?> _color = ColorTween(
    begin: Colors.amber,
    end: Colors.red,
  ).animate(_animationController);


AnimatedBuilder(
    animation: _color,
    builder: (context, child) {
    return Container(
        color: _color.value,
        width: 400,
        height: 400,
    );
    },
    ),
```

AnimatedBuilder -> 최후로 쓰는게 좋다 .

### 2.5 Explicit Widgets 

### 2.8 AnimationStatus 


`addStatusListener` 활용하면 status를 확인할 수 있다. 

```dart
..addStatusListener((status) {
      if (status == AnimationStatus.completed) {
        _animationController.reverse();
      } else if (status == AnimationStatus.dismissed) {
        _animationController.forward();
      }
    });
```

## 3 APPLE WATCH PROJECT 

`CustomPainter` 위젯을 써서 그려야 한다. 

```dart


class AppleWatchPainter extends CustomPainter {
    @override
    void paint(Canvas canvas, Size size) {
        final rect = Rect.fromLTWH(
        0,
        0,
        size.width,
        size.height,
        );

        final paint = Paint()..color = Colors.blue;

        canvas.drawRect(rect, paint);

        final circlaPaint = Paint()
        ..color = Colors.red
        ..style = PaintingStyle.stroke
        ..strokeWidth = 20;

        canvas.drawCircle(
        Offset(size.width / 2, size.height / 2),
        size.width / 2,
        circlaPaint,
        );
    }

    @override
    bool shouldRepaint(covariant CustomPainter oldDelegate) {
        return false;
    }
}

```

### 3.1 drawArc

`shouldRepaint` 다시 그리기 

```dart
 @override
  bool shouldRepaint(covariant AppleWatchPainter oldDelegate) {
    return oldDelegate.progress != progress;
  }
```


## 4 SWIPING CARDS PROJECT 

### 4.1 Bounds

AnimationController 는 기본적 0 ~ 1로 움직이기 때문에 하한, 상한을 수정한다. 

```dart 
 late final AnimationController _animationController = AnimationController(
    vsync: this,
    duration: Duration(seconds: 2),
    lowerBound: size.width * -1,
    upperBound: size.height,
    value: 0.0,
  );

```

### 4.4 Background Card
이미지를 `assets/covers/` 넣고 아래 pubspec.yaml에 아래와 같이 적는다. 

```yaml
  assets:
    - assets/
    - assets/covers/
```