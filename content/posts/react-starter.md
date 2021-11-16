---
title: "React Starter"
date: 2021-09-05T11:22:49+09:00
draft: true
---

## project Setup

### create-react-app 프로젝트 시작

`npx create-react-app project-name`

### 불필요 파일 삭제

App.js, index.js 빼고 src 폴더 내 파일 삭제

### Router 추가

`src/Components` 폴더 생성 후 App.js Components 폴더로 이동

index.js App 경로 수정 `./Components/App`

.env 파일 추가 후 `NODE_PATH=src` 추가

`Components/Router.js``

```javascript
import {
  HashRouter as Router,
  Route,
  Redirect,
  Switch,
} from "react-router-dom";
import Home from "../Routes/Home";
import TV from "../Routes/TV";
import Search from "../Routes/Search";

export default () => (
  <Router>
    <Switch>
      <Route path="/" exact component={Home} />
      <Route path="/tv" component={TV} />
      <Route path="/search" component={Search} />
      <Redirect from="*" to="/" />
    </Switch>
  </Router>
);
```

#### Switch 추가

한번에 하나의 Route만 랜더

### Header 추가

## Style

### styled-components 추가

`yarn add styled-components`

### GlobalStyle.js 추가

폰트 등 전체적으로 적용할 css

#### styled-reset 추가

`yarn add styled-reset`

### withRouter 추가

컴포턴트들과 연결되는 props를 다룬다

```javascript
import { Link, withRouter } from "react-router-dom";

const SHeader = ({ location: { pathname } }) => (
  <Header>
    {console.log(pathname)}
    <List>
      <Item current={pathname == "/"}>
        <SLink to="/">Home</SLink>
      </Item>
      <Item current={pathname == "/tv"}>
        <SLink to="tv">TV</SLink>
      </Item>
      <Item current={pathname == "/search"}>
        <SLink to="search">Search</SLink>
      </Item>
    </List>
  </Header>
);

export default withRouter(SHeader);
```

## Networking

영화 DB 얻어오는 사이트 계정얻기 https://www.themoviedb.org/

API 사이트: https://developers.themoviedb.org/3/getting-started/introduction

### add axios

`yarn add axios`

create `api.js`

```javascript
import axios from "axios";

const api = axios.create({
  baseURL: "https://api.themoviedb.org/3/",
  params: {
    api_key: "ad6efc0d7346f003**************",
    language: "en-US",
  },
});

export const movieApi = {
  nowPlaying: () => api.get("movie/now_playing"),
  upComing: () => api.get("movie/upcoming"),
  popular: () => api.get("movie/popular"),
  movie: (id) =>
    api.get(`movie/${id}`, {
      params: {
        append_to_response: "videos",
      },
    }),
  search: (term) =>
    api.get("search/movie", {
      params: {
        guery: encodeURIComponent(term),
      },
    }),
};
```

## CONTAINERS

### handleSubmit

## Presenters

### error js

```javascript
import PropTypes from "prop-types";
import styled from "styled-components";

const Container = styled.div``;

const Text = styled.span`
  color: #e74c3c;
`;

const Error = ({ text }) => {
  <Container>
    <Text>{text}</Text>
  </Container>;
};

Error.propTypes = {
  text: PropTypes.string.isRequired,
};

export default Error;
```

### Add react-helmet

`yarn add react-helmet`

```javascript
import Helmet from "react-helmet";

const DetailPresenter = ({ result, error, loading }) => (
  <>
    <Helmet>
      <title>Loading | Nomflix</title>
    </Helmet>
    {loading ? (
      <Loader />
    ) : (
      <Container>
        <Helmet>
          <title>
            {result.original_title
              ? result.original_title
              : result.original_name}{" "}
            | Nomflix
          </title>
        </Helmet>
        <BackDrop bgImage={result.backdrop_path} />
        <Content>
          <Poster
            src={
              result.poster_path
                ? `https://image.tmdb.org/t/p/original${result.poster_path}`
                : require("../../assets/modootango-logo.png")
            }
          />
          <Data>
            <h1>
              {result.original_title
                ? result.original_title
                : result.original_name}
            </h1>
          </Data>
        </Content>
      </Container>
    )}
  </>
);
```
