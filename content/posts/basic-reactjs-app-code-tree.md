---
title: "Basic Reactjs App Code Tree with Nomadcoder"
slug: "Basic Reactjs App Code Tree"
tags: ["nomadcoder"]
date: 2021-03-13T18:32:04+09:00
draft: true
---

## 초보를 위한 React JS

실행 

```
npx create-react-app nomflix
```

삭제하는 파일 
`App.css index.css`

### .env 생성

src부터 바라보도록 설정

```
NODE_PATH=src
```

## Router 설치

컴포넌트 묶음 Router 설치 

가이드문서: https://reactrouter.com/web/guides/quick-start 

```
yarn add react-router-dom
```

### HashRouter vs BrowserRouter

#### HashRouter 

앱처럽 보여주고 싶다면 HashRouter.

간단하지만 url에 /#/detail 처럼 Hash가 붙는다.

Hash 사용 

#### BrowserRouter 

사이트처럽 보여주고 싶다면 BrowserRouter.

url이 /detail 처럼 보인다. 실제브라우져처럼 보여줌.

HTML History API 사용

### Components

Components/Router.js

```javascript
import React from 'react';
import { HashRouter as Router, Route } from 'react-router-dom';
import Home from "../Routes/Home";
import TV from "../Routes/TV";
import Search from "../Routes/Search";
import Detail from "../Routes/Detail";

const coco = () => (
    <Router>
        <>
            <Route path="/" exact component={Home}></Route>
            <Route path="/tv" exact component={TV}></Route>
            <Route path="/search" exact component={Search}></Route>
            <Route path="/detail" exact component={Detail}></Route>
        </>
    </Router>
)

export default coco;

```



### Home 

Routes/Home.js

```javascript
const Home = () => {
    return "home";
}; 

export default Home;

```

## style 

### add style components 

style 안에 있는 컴포넌트를 생성할 수 있게 한다.

```
yarn add styled-components
```

### add styled-reset

SC를 이용해서 css를 초기화해서 0의 상태에서 시작하게 하는 것 


## plugin 


styled-components 에서 css를 사용하기 위한 플러그인
[vscode-styled-components](https://marketplace.visualstudio.com/items?itemName=jpoissonnier.vscode-styled-components)
추가 

## withRouter 

다른 컴포넌트를 감싸는 컴포넌트. 어떤 컴포넌트와도 연결할 수 있다. 

```javascript
import { Link, withRouter } from "react-router-dom";


const Header = (props) => (
    <HeaderStyle>
        <List>
            <Item current={false}>
                <SLink to="/">Movies</SLink>
            </Item>
            <Item current={true}>
                <SLink to="/tv">TV</SLink>
            </Item>
            <Item current={false}>
                <SLink to="/search">Search</SLink>
            </Item>
        </List>
    </HeaderStyle>
);

export default withRouter(Header);
```

## networking 

https://www.themoviedb.org/ 가입하기 


## yarn add axios

https://github.com/axios/axios  

Axios의 인스턴스를 설정해줄 수 있다. 

```
yarn add axios
```

## 검색을 위한 stirng encoding 

encodeURIComponent를 사용한다

```
search: (term) => api.get("search/movie", {
    params: {
        query: encodeURIComponent(term)
    }
})
```
