---
title: useEffect를 사용하여 마운트/언마운트/업데이트시 할 작업 설정하기
date: 2022-12-09 +/-TTTT
categories: [React, React]
tags: [react] # TAG names should always be lowercase

---

# 🔖 useEffect를 사용하여 마운트/언마운트/업데이트시 할 작업 설정하기

## `📌 배운 내용 및 기억하고 싶은 내용`

- `Mount`: 처음 나타났을 때를 의미

- `UnMount`: 사라질 때를 의미

- `Update`:  특정 props가 바뀔 때를 의미

- `useEffect`: 특정 작업을 처리할 때 사용

  - ```jsx
    useEffect(() => {
      // 컴포넌트가 생길 때 수행 작업
      return {
          // 컴포넌트가 사라질 때 수행 작업
      }
    }, [의존성])
    ```

  -  첫번째 파라미터: 함수

  -  두번째 파라미터: 의존값이 들어있는 배열 (`deps`)

    - `deps` 배열을 비우면 컴포넌트가 처음 나타날때에만 `useEffect` 에 등록한 함수가 호출됨

  - `useEffect` 에서는 함수를 반환 할 수 있는데 이를 `cleanup` 함수라고 부른다.

    - `deps` 가 비어있는 경우에는 컴포넌트가 사라질 때 `cleanup` 함수가 호출된다.



### 마운트시 하는 작업

- `props` 로 받은 값을 컴포넌트의 로컬 상태로 설정
- 외부 API 요청 (REST API 등)
- 라이브러리 사용 (D3, Video.js 등...)
- setInterval 을 통한 반복작업 혹은 setTimeout 을 통한 작업 예약

### 언마운트시 하는 작업

- 뒷정리 함수

- setInterval, setTimeout 을 사용하여 등록한 작업들 clear 하기 (clearInterval, clearTimeout)
- 라이브러리 인스턴스 제거



### deps에 특정 값 넣기

- deps 에 특정 값을 넣으면 컴포넌트가 처음 마운트 될 때에도 호출이 되고, 지정한 값이 바뀔 때에도 호출이 된다.
  - deps 안에 특정 값이 있다면 언마운트시에도 호출이되고, 값이 바뀌기 직전에도 호출이 된다.
- `useEffect` **안에서 사용하는 상태나, props 가 있다면**, `useEffect` **의** `deps` **에 넣어야한다.**
  - `useEffect` 안에서 사용하는 상태나 props 를 `deps` 에 넣지 않게 된다면 `useEffect` 에 등록한 함수가 실행 될 때 최신 props 나 상태를 가르키지 않게 된다.



### deps 파라미터를 생략하기

- `deps` 파라미터를 생략한다면, 컴포넌트가 리렌더링될 때마다 호출이 된다.
- 리액트 컴포넌트는 기본적으로 부모컴포넌트가 리렌더링되면 바뀐 내용이 없더라도, 자식 컴포넌트 또한 리렌더링된다.
  - 실제 DOM 에 변화가 반영되는 것은 바뀐 내용이 있는 컴포넌트에만 해당하지만,  가상 DOM은 모든걸 다 렌더링하고 있다.





