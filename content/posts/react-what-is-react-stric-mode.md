---
title: "React Stric Mode란?"
slug: "React What Is React Stric Mode"
categories: ["react"]
date: 2021-08-27T16:11:53+09:00
draft: false
---

## React 앱 내의 잠재적 문제를 알아내가 위한 도구

```javascript
ReactDOM.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
  document.getElementById("root")
);
```

용도는 아래와 같습니다.

- 안전하지 않은 생명주기를 사용하는 컴포넌트 발견
- 레거시 문자열 ref 사용에 대한 경고
- 권장되지 않는 findDOMNode 사용에 대한 경고
- 예상치 못한 부작용 검사
- 레거시 context API 검사

### 개발용 모드

> Strict 모드는 개발 모드에서만 활성화되기 때문에, 프로덕션 빌드에는 영향을 끼치지 않습니다.

production 배포되었을 때는 stric 모드가 사라진다.
