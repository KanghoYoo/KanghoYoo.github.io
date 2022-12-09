---
title: defaultProps로 기본값 설정
date: 2022-12-09 +/-TTTT
categories: [React, React]
tags: [react] # TAG names should always be lowercase
---

# 🔖 defaultProps로 기본값 설정

## `📌 배운 내용 및 기억하고 싶은 내용`

### defaultProps

- 컴포넌트에 props 를 지정하지 않았을 때 기본적으로 사용할 값을 설정하고 싶을 때 사용

- 컴포넌트에 `defaultProps` 라는 값을 설정하여 사용하면 됨

```jsx
// Hi.js

import React from 'react';

function Hi({ color, name }) {
  return <div style={{ color }}>안녕하세요 {name}</div>
}

// defaultProps로 기본값 설정
Hello.defaultProps = {
  name: '이름없음'
}

export default Hi;

// App.js

import React from 'react';
import Hi from './Hi';

function App() {
  return (
    <>
      <Hi name="Yoo" color="blue"/>
      <Hi color="pink"/>
    </>
  );
}

export default App;
```

