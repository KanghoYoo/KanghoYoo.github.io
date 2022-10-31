---
title: "Git & GitHub"
excerpt: "Git 설치 및 GitHub 이용방법"

categories:
  - Git&GitHub
tags:
  - [Github, Git]

toc: true
toc_sticky: true

date: 2022-10-18
last_modified_at: 2022-10-20
---

# Git & GitHub

## Git

- 분산 버전 관리 시스템(VCS)
- 프로젝트파일의 변경을 추적하는 시스템
  - 많은 사람들이 효율적으로 프로젝트를 협업할 수 있음
  - 개발자들의 변경사항을 기록하고 원하는 시점으로 돌아갈 수 있음
  - 관리가 용이함

> Git 공식홈페이지: https://git-scm.com/

### Git 설치 및 시작

> Git 공식설치홈페이지: https://git-scm.com/downloads

1. Git홈페이지에서 CLI로 다운로드후 설치 진행

2. 설치를 완료한 후, `git --version`로 Git 버전 확인

3. 이름과 이메일 설정

   ```bash
   git config --global user.name "이름"
   git config --global user.email "이메일"
   ```

4. 터미널에서 프로젝트 폴더로 이동후,

   ```bash
   git init //git 디렉토리를 생성 및  현재 저장소에 대한 모든 변경사항을 추적/관리하게 됨
   ```

   명령어 입력

### Repositories (저장소)

- Git으로 관리하는 프로젝트 저장소
  - **Local repository** - 본인의 컴퓨터에 저장된 로컬 버전의 프로젝트 저장소
  - **Remote repository** - 원격서버 버전의 프로젝트 저장소. 협업할때 유용함. 프로젝트 코드를 공유 및 다른 사람의 코드를 확인가능, 로컬 버전의 프로젝트와 병합하고, 변경 사항을 적용 할 수 있음

### Ignoring files

- staging area 에 추가하고 싶지 않거나, git 에서 관리하지 않아도 되는 파일이 있을 때, `.gitignore` 파일을 프로젝트 폴더에 생성 해당하는 파일명과 폴더명을 나열하면 됨

```js
.DS_*
*.log
logs
**/*.backup.*
**/*.back.*
node_modules
bower_components
```

### Branches

- 독립적으로 어떤 작업을 진행하기 위한 개념
- 다른 브랜치에 영향을 받지 않아 동시에 여러 작업 가능
- 브랜치로 작업의 기록을 중간 중간에 남기게 되므로 문제가 생겼을 때, 원인을 발견하거나 해결방안을 찾기 쉬워짐

## GitHub

- 프로젝트 저장소(레파스토리지)
- 개발자들의 소셜 네트워크
- 버전 관리 프로젝트 관리를 해주는 호스팅 서비스 제공

> 깃허브 링크: http://github.com/

### GitHub 시작하기

#### 내 로컬 Repository를 GitHub 에 push 하기

1. 로컬에서 `add`와 `commit` 진행
2. Github 으로 이동 후 새로운 **repository를 생성**
3. 나의 로컬 repository를 GitHub repository와 `Remote`
4. 새 remote 를 이용하여 코드 `Push`

#### repository 생성하기

1. GitHub로 이동 후 우측 상단 `+` 버튼을 누른 뒤 **'New repository'** 옵션을 선택
2. **'Repository name'**을 설정

#### repository 에 코드 push 하기

1. **'Create repository'** 버튼을 눌러서 이동되는 GitHub repository 의 시작 페이지에서 나오는 설명 따라 실행

> ❗️로컬환경에 이미 Git repository 가 존재할 경우, 두번째 `...or push an existing repository from the command line` 부분 순서대로 진행

2. 변경된 로컬 repo를 GitHub repo로 push

#### repository 클론하기 (clone)

1. **'Clone or download'** 초록색 버튼을 누른 뒤 아래 복사 아이콘을 클릭
2. 해당 repo 를 다운로드 받고 싶은 경로로 이동한 뒤 **git clone** 명령어에 방금 복사해준 URL 을 붙여주고 실행

#### Pull Request (PR)

- 해당 repository 를 열람할 수 있는 권한이 있는 개발자들이 작업내용에 대한 리뷰를 해주거나, 변경 사항을 확인 가능
- PR을 통하여 프로젝트 오너에게 내가 작업한 브랜치의 작업내용을 master 브랜치에 반영 요청을 할 수 있음

#### Conflicts (충돌)

- 어떤 파일의 변경사항이 기준이 되는 master 브랜치의 파일과 겹쳐, Git 에서 어떤 버전의 코드를 선택해야하는지 모를 때 발생
- 개발자가 직접 코드를 비교해 충돌을 해결하고 merge 해야함
