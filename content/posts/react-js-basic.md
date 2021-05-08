---
title: "Javascript Basic"
slug: "Javascript Basic"
categories: ["ReactJS"]
tags: ["router"]
date: 2021-03-07T16:21:32+09:00
draft: true
---

## React Router

간단한 컴포넌트 묶음 `Router`를 만들고 `Route`를 만든다

### ReactJs 규칙

return 두개는 할 수 없다. Fragments를 사용하여 다수의 컴포넌트를 return한다

```
return <><Router /></>

```

### Redirect

Route에 매치되는 것이 없으면 어디로 가세요.

```javascript
<Router>
  <>
    <Route path="/" exact component={Home}></Route>
    <Route path="/tv" component={TV}></Route>
    <Route path="/search" component={Search}></Route>
    <Route path="/detail" component={Detail}></Route>
    <Redirect from="*" to="/" />
  </>
</Router>
```

### Switch

하나의 Route만 Render

```javascript
<Router>
  <Switch>
    <Route path="/" exact component={Home}></Route>
    <Route path="/tv" component={TV}></Route>
    <Route path="/search" component={Search}></Route>
    <Route path="/detail" component={Detail}></Route>
    <Redirect from="*" to="/" />
  </Switch>
</Router>
```

### exact

정확히 일치해야 Route

```javascript
<Route path="/tv" exact component={TV}></Route>
```
