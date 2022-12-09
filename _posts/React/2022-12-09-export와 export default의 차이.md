---
title: export와 export default의 차이
date: 2022-12-09 +/-TTTT
categories: [React, React]
tags: [react] # TAG names should always be lowercase
---

# 🔖 export와 export default의 차이

## `📌 배운 내용 및 기억하고 싶은 내용`

### export

- 해당 모듈에는 **여러 개의 개체**가 있음
- 여러개의 개체를 내보낼때 사용
- 특정 개체만 따로 import 가능함
- 중괄호 필요함
- 원하는 이름으로 import 불가능

```jsx
// Animals.jsx
function Duck() {
  return <h1>Hi! I'm Duck!</h1>;
}

function Goose() {
  return <h1>Hello! I'm Goose~!</h1>;
}

export Duck;
export Goose;


// AnimalsIntro.jsx
import { Duck } from "./Animals.jsx"
```



### export default

- 해당 모듈에는 하나의 개체(변수, 클래스, 함수...)만 있음
- 하나의 개체를 내보낼때 사용
- 중괄호 필요없음
- 원하는 이름으로 import 가능

```jsx
// Animal.jsx
function Duck() {
  return <h1>Hi! I'm Duck!</h1>;
}

export default Duck;


// AnimalIntro.jsx
import Duck from "./Animal.jsx" // import {default as Duck} from "./Animal"
```

