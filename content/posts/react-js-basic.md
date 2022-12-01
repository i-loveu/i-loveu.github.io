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

### setState

새로운 state 불러와서 값을 바꿔주며 render()을 호출한다

### current

```javascript
this.setState({ count: this.state.count - 1 });
this.setState((current) => ({ count: current.count - 1 }));
```

위에 줄을 아래줄로 변경할 수 있따

### componentDidUpdate

state가 변경되고 render()를 호출하고 실행된다

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

### 루프

kye를 지정한다. 하지만 `<Profile>`에서 key값을 인자로 받지는 않는다.

```javascript
{
  data
    ? data?.dancers?.map((dancer) => (
        <Profile
          id={dancer.id}
          avatar={dancer.avatar}
          nick={dancer.nick}
          loginId={dancer.loginId}
          key={dancer.loginId}
        />
      ))
    : "Loading...";
}

interface ProfileProps {
  id: number;
  loginId: string;
  nick: string | null;
  avatar: string | null;
}
```
