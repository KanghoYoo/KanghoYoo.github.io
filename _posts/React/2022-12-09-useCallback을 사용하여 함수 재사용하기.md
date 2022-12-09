---
title: useCallback을 사용하여 함수 재사용하기
date: 2022-12-09 +/-TTTT
categories: [React, React]
tags: [react] # TAG names should always be lowercase
---

# 🔖 useCallback을 사용하여 함수 재사용하기

## `📌 배운 내용 및 기억하고 싶은 내용`

- `useMemo`와 `useCallback`의 차이점

  - `useMemo` 는 특정 결과값을 재사용 할 때 사용한다.

  - `useCallback` 은 특정 함수를 새로 만들지 않고 재사용하고 싶을때 사용한다.

- `useCallback`

  -  한번 만든 함수를 필요할때만 새로 만들고 재사용하는 것은 여전히 중요하다.
    - 나중에 컴포넌트에서 `props` 가 바뀌지 않았으면 Virtual DOM 에 새로 렌더링하는 것 조차 하지 않고 컴포넌트의 결과물을 재사용 하는 최적화 작업을 할 때, 함수를 재사용하는것이 필수다.
  - 

  ```jsx
  const memoizedCallback = useCallback(
    () => {
      doSomething(a, b);
    },
    [a, b],
  );
  ```

- > ##### ❗️주의 
  >
  > 함수 안에서 사용하는 상태 혹은 props 가 있다면 꼭, `deps` 배열안에 포함시켜야 된다.
  >
  > 만약에 `deps` 배열 안에 함수에서 사용하는 값을 넣지 않게 된다면, 함수 내에서 해당 값들을 참조할때 가장 최신 값을 참조 할 것이라고 보장 할 수 없다. 
  >
  > props 로 받아온 함수가 있다면,  `deps` 에 넣어야한다.

  - `useCallback(fn, deps)`은 `useMemo(() => fn, deps)`와 같다.
