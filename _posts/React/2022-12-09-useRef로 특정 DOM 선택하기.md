---
title: useRef로 특정 DOM 선택하기
date: 2022-12-09 +/-TTTT
categories: [React, React]
tags: [react] # TAG names should always be lowercase
---

# 🔖 useRef로 특정 DOM 선택하기

## `📌 배운 내용 및 기억하고 싶은 내용`

- React의 함수형 컴포넌트에서 특정 DOM을 선택할 때는 `useRef();`를 사용한다.
- 클래스 컴포넌트에서는 콜백 함수를 사용하거나 `React.createRef` 라는 함수를 사용한다.

```jsx
import React, { useState, useRef } from 'react';

function InputSample() {
  const [inputs, setInputs] = useState({
    name: '',
    nickname: ''
  });
  // useRef() 함수를 사용하여 Ref 객체 생성 
  const nameInput = useRef();

  const { name, nickname } = inputs;

  const onChange = e => {
    const { value, name } = e.target;
    setInputs({
      ...inputs, 
      [name]: value 
    });
  };

  const onReset = () => {
    setInputs({
      name: '',
      nickname: ''
    });
    // Ref 객체의 .current 값을 통해 DOM을 선택한다.
    nameInput.current.focus();
  };

  return (
    <div>
      <input
        name="name"
        placeholder="이름"
        onChange={onChange}
        value={name}
        // 선택한 DOM을 props로 주어 적용한다.
        ref={nameInput}
      />
      <input
        name="nickname"
        placeholder="닉네임"
        onChange={onChange}
        value={nickname}
      />
      <button onClick={onReset}>초기화</button>
      <div>
        <b>값: </b>
        {name} ({nickname})
      </div>
    </div>
  );
}

export default InputSample;
```

