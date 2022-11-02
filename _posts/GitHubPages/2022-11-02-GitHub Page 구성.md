---

title: GitHub Page Blog 커스텀
date: 2022-11-02 +/-TTTT
categories: [Git&GitHub, GitHub-Pages]
tags: [github-page] # TAG names should always be lowercase

---

# Jekyll 디렉토리 구조

### Jekyll 디렉토리 구조

```
.
├── _config.yml
├── _data
│   └── members.yml
├── _drafts
│   ├── begin-with-the-crazy-ideas.md
│   └── on-simplicity-in-technology.md
├── _includes
│   ├── footer.html
│   └── header.html
├── _layouts
│   ├── default.html
│   └── post.html
├── _posts
│   ├── 2007-10-29-why-every-programmer-should-play-nethack.md
│   └── 2009-04-26-barcamp-boston-4-roundup.md
├── _sass
│   ├── _base.scss
│   └── _layout.scss
├── _site
├── .jekyll-cache
│   └── Jekyll
│       └── Cache
│           └── [...]
├── .jekyll-metadata
└── index.html # can also be an 'index.md' with valid front matter
```

---

Chirp Theme 구조

### _Config.yml

- 블로그의 기본 설정 파일, 환경설정 정보를 담고 있으며 여러 setting들이 기록되어 있음
- 프로필, 소개말, Favicon, 사이드바 컬러, url 등 여러 구성 요소들이 저장되어 있음

### _data

- 블로그에 사용할 수 있는 데이터를 모아 놓은 폴더
- `.yml`, `.yaml`, `json`, `.csv` 일 경우, 자동으로 읽어 `site.data` 변수로 가져올 수 있음
- 사이드바와 언어변경이 가능한 폴더

### _includes

- 사이드바, TOC, Footer, 구글애널틱스, 댓글 등 모듈형으로 삽입되어 있는 UI 지정 가능
- 재사용할 수 있는 부분적으로 만들어진 html파일을 보관할 수 있는 폴더
  - ex) head, footer

### _layouts

- 포스트와 블로그 디자인이 연결된 레이아웃을 지정하는 파일이 저장된 폴더
- `default.html`: 최상위 jekyll Blog 구성을 담고 있는 파일
  - `post.html`: Post 형태를 정의해 놓은 html 파일

### _posts

- 작성한 포스트들을 저장하는 폴더
- `yyyy-mm-dd-title.md` 형식을 사용

### _sass

- css 파일들이 저장되어있는 폴더

### _site

- 로컬에서 실행할 때, 화면을 구성하는 UI들의 내용이 담겨져 있는 폴더
- 변경시, 로컬에는 반영되지만 Github에는 반영이 안됨
- 주의❗️ 폴더내 파일 건들지 말것

### _tabs

- 사이드바의 기본 탭메뉴들에 대한 랜딩페이지가 포함된 폴더

### assets

-  이미지와 css 파일, Favicon이 있는 폴더

### Tools

- Github에서 자동 배포를 위한 코드가 들어 있는 폴더