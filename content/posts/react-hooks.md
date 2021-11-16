---
title: "React Hooks"
date: 2021-09-25T11:28:27+09:00
draft: true
---

## Info

https://reactjs.org/docs/hooks-intro.html

## UseState

### 구성

```javascript
import { useState } from "react";

const useStateFucntionName = (initailvalue) => {
  const [itemName, setItemName] = useState(iniitalValue);
  return {
    itemName,
  };
};
```

## useEffect

componentDidMount, componentWillUnmount, componentWillUpdate 와 비슷하다.

```javascript
const functionNamme = () => console.log("hello");

useEffect(functionNamme, [someState]);
```

someState 값이 변하면 functionName을 실행한다.

```javascript
useEffect(functionNamme, []); // componentDidMount
```

이 경우 한번 실행된다

### useRef();

리엑트에서 input은 ref를 가지고 있는데

```javascript
const potato = useRef();
setTimeout(() => potato.current.focus(), 3000);

return <input ref={potato} placeholder="title" />;
```

이렇게 하면 3초 뒤 위 input에 focus가 잡힌다.

### useCinfirm & usePreventLeave

```javascript
const usePreventLeave = () => {
  const listener = (event) => {
    event.preventDefault();
    event.returnValue = "";
  };
  const enablePrevent = () => window.addEventListener("beforeunload", listener);
  const disablePrevent = () =>
    window.removeEventListener("beforeunload", listener);
  return { enablePrevent, disablePrevent };
};

const App = () => {
  const { enablePrevent, disablePrevent } = usePreventLeave();

  return (
    <>
      <h1>Add To dos</h1>
      <button onClick={enablePrevent}>Prevent</button>
      <button onClick={disablePrevent}>removePrevent</button>
    </>
  );
};

export default App;
```

## useReducer

### Context

필요할 떄마다 불러서 사용. 데이터 저장소

간단한 React 어플리케이션에 적용

### Redux

커다란 States와 많은 변화들이 있을 때 사용

### State Management
