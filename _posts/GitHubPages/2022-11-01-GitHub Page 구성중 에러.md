---
title: GitHub Page 구성중 에러
date: 2022-11-01 +/-TTTT
categories: [Git&GitHub, GitHub-Pages]
tags: [github-page] # TAG names should always be lowercase
---

# GitHub Page 구성중 에러

### ❗️문제 상황

현재 나의 상태

- Mac을 사용
- Jekyll로 Chirpy Theme 사용
- Ruby Gemfile 사용
- CSS가 적용되지 않고 `---layout: home # Index page---` 화면만 나옴

- Github Action에서 gh-pages가 생성되지 않음



### 💡해결 방안

- `---layout: home # Index page---` 구글링
- GitHub Repository의 `setting` - `pages` - `Bulid and deployment`옵션의 `Sorce` 변경 -> `GitHub Actions` 사용
  - sorce 빌드를 변경
- 터미널에 `bundle lock --add-platform x86_64-linux` 입력
  - Ruby의 버전과 mac os 문제로 에러 발생 해결