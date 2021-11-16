---
title: "Typescript Basic"
date: 2021-09-20T11:36:24+09:00
draft: true
---

## 용도

값의 형식을 정의해서 javascript 오류를 막아준다.

```javascript
const greet = (name: string, age: number): string => {
  return must_be_string;
};
```

### object 정의

`interface` 를 사용해 정의

```javascript
interface Human {
  name: string;
  age: number;
  hungry: boolean;
}
```

## 시작하기

`npx create-react-app typescript-project-name --template typescript`

### tsconfig.json

### DefinitelyTyped

https://github.com/DefinitelyTyped/DefinitelyTyped

만약 `styled-conponents`를 사용한다면

`yarn add @types/styled-components`로 설치하면 관련 자동완성 기능을 지원한다
`npm i --save-dev @types/styled-components`

### set state use by interface

```typescript
interface IState {
  counter: number;
}

class App extends Component<props, state> {}
```

```typescript
interface Iprops {
  count: number;
}

const Number: React.FunctionComponent<{ count: number }> = ({ count }) => <></>;

// or

const Number: React.FunctionComponent<Iprops> = ({ count }) => <></>;

export default Number;
```

### styled Components

```typescript
interface IContainerProps {
  isBlue: boolean;
}
const Container = styled.span<{ isBlue: boolean }>``;
// or
const Container = styled.span<IContainerProps>`
  color: ${(props) => (props.isBlue ? "blue" : "black")};
`;

interface Iprops {
  count: number;
}

const Number: React.FunctionComponent<Iprops> = ({ count }) => (
  <Container isBlue={count > 10}>{count}</Container>
);

export default Number;
```

### styled.d.ts

theme에 어떤 컬러가 정의되어 있는지 알려주는 것

참고: https://styled-components.com/docs/api

`style/theme.ts` 파일을 생성하고 definition color를 생성

```typescript
export default {
  blueColor: "red",
};
```

`src/styled.d.ts` 파일을 생성

```typescript
import "styled-components";

// and extend them!
declare module "styled-components" {
  export interface DefaultTheme {
    blueColor: string;
  }
}
```

`src/index.tsx` 파일에 `styled-components`에 들어 있는 `themeProvider`를 이용

```typescript
import React from "react";
import ReactDOM from "react-dom";
import App from "./App";
import { ThemeProvider } from "styled-components";
import theme from "./style/theme";

ReactDOM.render(
  <React.StrictMode>
    <ThemeProvider theme={theme}>
      <App />
    </ThemeProvider>
  </React.StrictMode>,
  document.getElementById("root")
);

// If you want t
```

### router

`npm install --save-dev @types/react-router-dom`
