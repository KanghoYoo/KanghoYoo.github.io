---
title: export์ export default์ ์ฐจ์ด
date: 2022-12-09 +/-TTTT
categories: [React, React]
tags: [react] # TAG names should always be lowercase
---

# ๐ export์ export default์ ์ฐจ์ด

## `๐ ๋ฐฐ์ด ๋ด์ฉ ๋ฐ ๊ธฐ์ตํ๊ณ  ์ถ์ ๋ด์ฉ`

### export

- ํด๋น ๋ชจ๋์๋ **์ฌ๋ฌ ๊ฐ์ ๊ฐ์ฒด**๊ฐ ์์
- ์ฌ๋ฌ๊ฐ์ ๊ฐ์ฒด๋ฅผ ๋ด๋ณด๋ผ๋ ์ฌ์ฉ
- ํน์  ๊ฐ์ฒด๋ง ๋ฐ๋ก import ๊ฐ๋ฅํจ
- ์ค๊ดํธ ํ์ํจ
- ์ํ๋ ์ด๋ฆ์ผ๋ก import ๋ถ๊ฐ๋ฅ

```jsx
// Animals.js
function Duck() {
  return <h1>Hi! I'm Duck!</h1>;
}

function Goose() {
  return <h1>Hello! I'm Goose~!</h1>;
}

export Duck;
export Goose;


// AnimalsIntro.js
import { Duck } from "./Animals.js"
```



### export default

- ํด๋น ๋ชจ๋์๋ ํ๋์ ๊ฐ์ฒด(๋ณ์, ํด๋์ค, ํจ์...)๋ง ์์
- ํ๋์ ๊ฐ์ฒด๋ฅผ ๋ด๋ณด๋ผ๋ ์ฌ์ฉ
- ์ค๊ดํธ ํ์์์
- ์ํ๋ ์ด๋ฆ์ผ๋ก import ๊ฐ๋ฅ

```jsx
// Animal.js
function Duck() {
  return <h1>Hi! I'm Duck!</h1>;
}

export default Duck;


// AnimalIntro.jsx
import Duck from "./Animal.js" // import {default as Duck} from "./Animal"
```

