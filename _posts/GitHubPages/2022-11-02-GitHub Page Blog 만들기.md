---
title: GitHub Page Blog 제작
date: 2022-11-02 +/-TTTT
categories: [Git&GitHub, GitHub-Pages]
tags: [github-page] # TAG names should always be lowercase
---

# GitHub Page Blog 만들기

## Ruby 설치

1. Hombrew 이용한 Ruby 설치

```shell
brew update                       # Homebrew 업데이트
brew install rbenv ruby-build 		# rbenv 와 ruby-build 설치
```



2. bash_profile 수정

```shell
eval "$(rbenv init -)"
```



3. Ruby 설치

```shell
rbenv install 2.7.6               # Ruby 2.7.6 버전 설치
rbenv rehash                      # 새 Ruby 설치 후 실행
```

- rbenv: 루비의 버전을 독립적으로 사용할 수 있도록 도와주는 패키지 

## Jekyll Bundler 설치

```shell
gem install jekyll bundler         # jekyll 과 bundler 설치
```

- gem: 루비에서 지원하는 패키지 시스템



## GitHub 페이지 생성

1. GitHub 페이지에서 우측 상단의 New  클릭

![스크린샷 2022-11-02 오후 5.18.25](../../assets/img/postingImg/스크린샷 2022-11-02 오후 5.18.25.png)

- Repository name에 아래 형식대로 작성하고 최하단의 Create repository 클릭

  ![스크린샷 2022-11-02 오후 5.25.43](../../assets/img/postingImg/스크린샷 2022-11-02 오후 5.25.43.png)



## Jekyll 테마 선택

http://jekyllthemes.org/ 링크에서 원하는 테마 선택후 다운로드, 로컬에 만든 폴더로 이동후 복사&붙어넣기



## Gemfile 생성

```bash
bundle init
```



## Bundle 설치

시작할 테마가 있는 폴더 경로(레파지토리)로 이동하여 명령

```shell
bundle install              # bundle 설치
```



## Jekyll 로컬호스트 실행

- 해당 명령어를 입력한 후, [http://localhost:4000](http://localhost:4000/) 사이트로 접속하면 로컬호스트 서버로 접속됨

```shell
bundle exec jekyll serve        # 로컬호스트로 Github page 실행
```

> `jekyll s` 커맨드로 간단히 입력 가능



## jekyll 관련 사이트

- https://jekyllrb-ko.github.io/docs/community/