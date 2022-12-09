---
title: useReducer를 사용하여 상태 업데이트 로직 분리하기
date: 2022-12-09 +/-TTTT
categories: [React, React]
tags: [react] # TAG names should always be lowercase
---

# 🔖 useReducer를 사용하여 상태 업데이트 로직 분리하기

## `📌 배운 내용 및 기억하고 싶은 내용`

- `useState`의 대체 함수

- ```jsx
  const [state, dispatch] = useReducer(reducer, initialState);
  ```

  - `state` 는 우리가 앞으로 컴포넌트에서 사용 할 수 있는 상태를 가르키게 되고, `dispatch` 는 액션을 발생시키는 함수다. 
    - dispatch 함수 사용법
      -  `dispatch({ type: 'INCREMENT' })`

- `(state, action) => newState`의 형태로 reducer를 받고 `dispatch` 메서드와 짝의 형태로 현재 state를 반환

- 컴포넌트의 상태 업데이트 로직을 컴포넌트에서 분리시킬 수 있다.

  - 상태 업데이트 로직을 컴포넌트 바깥에 작성 할 수도 있고,  다른 파일에 작성 후 불러와서 사용 할 수도 있음

- `action`에는 객체가 전달되는데 그 안에 `type`  프로퍼티를 주로 설정해서 사용한다.

- `type` 프로퍼티를 통해 switch 문으로 분기한다.

- `state`는 `useReducer`를 통해 저장된 변수이며 주로 `initialState`라는 객체에 초기 정보를 담고 useReducer 에게 전달한다.

```jsx
// useState를 이용한 방법
import React, { useState } from 'react';

function Counter() {
  const [number, setNumber] = useState(0);

  const onIncrease = () => {
    setNumber(prevNumber => prevNumber + 1);
  };

  const onDecrease = () => {
    setNumber(prevNumber => prevNumber - 1);
  };

  return (
    <div>
      <h1>{number}</h1>
      <button onClick={onIncrease}>+1</button>
      <button onClick={onDecrease}>-1</button>
    </div>
  );
}

export default Counter;
```

```jsx
// useReducer를 이용한 방법
import React, { useReducer } from 'react';

function reducer(state, action) {
  switch (action.type) {
    case 'INCREMENT':
      return state + 1;
    case 'DECREMENT':
      return state - 1;
    default:
      return state;
  }
}

function Counter() {
  const [number, dispatch] = useReducer(reducer, 0);

  const onIncrease = () => {
    dispatch({ type: 'INCREMENT' });
  };

  const onDecrease = () => {
    dispatch({ type: 'DECREMENT' });
  };

  return (
    <div>
      <h1>{number}</h1>
      <button onClick={onIncrease}>+1</button>
      <button onClick={onDecrease}>-1</button>
    </div>
  );
}

export default Counter;
```



### action의 예시

```jsx
// 카운터에 1을 더하는 액션
{
  type: 'INCREMENT'
}
// 카운터에 1을 빼는 액션
{
  type: 'DECREMENT'
}
// input 값을 바꾸는 액션
{
  type: 'CHANGE_INPUT',
  key: 'email',
  value: 'tester@react.com'
}
// 새 할 일을 등록하는 액션
{
  type: 'ADD_TODO',
  todo: {
    id: 1,
    text: 'useReducer 배우기',
    done: false,
  }
}
```

- action 객체의 형식은 자유
- `type` 값을 대문자와 _ 로 구성하는 관습이 존재하지만, 꼭 써야할 필요는 없음



### `useState` VS `useReducer`

- **useState**: 컴포넌트에서 관리하는 값이 하나고, 그 값이 단순한 숫자, 문자열 또는 boolean 값이라면 확실히 `useState` 로 관리
- **useReducer**: 컴포넌트에서 관리하는 값이 여러개가 되어서 상태의 구조가 복잡해진다면 `useReducer`로 관리



