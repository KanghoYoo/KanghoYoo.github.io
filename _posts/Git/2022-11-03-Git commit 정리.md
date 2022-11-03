---
title: Git commit 정리
date: 2022-11-02 +/-TTTT
categories: [Git&GitHub, GitCommand]
tags: [git, github] # TAG names should always be lowercase
---

# Git 명령어 상세 정리

## Git commit을 정리 하는 이유

- 

![파일의 라이프사이클.](../../assets/img/postingImg/lifecycle.png)

## 설정 및 초기화

### 사용자 정보

`git config --global user.name “Your name"`

`git config --global user.email "Your email"`

- `--global` 옵션으로 설정하는 것은 한 번만 하면 된다.
- 프로젝트마다 다른 이름과 이메일 주소를 사용하고 싶으면 `--global` 옵션을 빼고 명령을 실행한다.

### 설정 정보 확인

`git config --list`

### 전역 설정 확인

`git config global --list`

### 도움말 보기

`git help <verb>` or`man git-<verb>`



## Commit

### add 명령에서 Git 대화 모드를 사용하여 파일 추가하기

`git add -i`

### 수정되고 추적되는 파일의 변경사항 스테이징하기

`git add -u [<path>[<path>]]`

### 수정되고 추적되는 모든 파일의 변경사항 커밋하기

`git commit -m "<msg>" -a`

### 작업 트리의 변경 사항 되돌리기

`git checkout HEAD <file> [<file>]`

### 커밋되지 않고 스테이징된 변경 사항 재설정하기

`git reset HEAD <file> [<file>]`

### 마지막 커밋 고치기

`git commit -m "<msg>" --amend`

### 파일 상태 짤막하게 확인하기

`git status --short` / `git status -s`



## Branch

### 지역 브랜치 목록보기

`git branch`

### 원격 브랜치 목록보기

`git branch -r`

### 지역과 원격을 포함한 모든 브랜치 보기

`git branch -a`

### 다른 시작 지점에서 브랜치 생성하기

`git branch <new-branch> <base-branch>`

### 기존의 브랜치를 새로운 브랜치에 덮어쓰기

`git branch -f <base-branch> [<new-branch>]`

### 브랜치를 옮기거나 브랜치 명 변경하기

`git checkout -m <base-branch> <new-branch>`

> 새 브랜치가 존재하지 않을 경우

`git checkout -M <base-branch> <new-branch>`

> 무조건 덮어쓰기

### 커밋하지 않고 합치기

`git merge --no-commit`

### 선택하여 합치기

`**git cherry-pick <commit-name>`

### 커밋하지 않고 선택하여 합치기

`git cherry-pick -n <commit-name>`

### 브랜치 이력을 다른 브랜치에 합치기

`git merge - -squash <brnach>`

---



## 파일 무시하기

`.gitignore` 파일에 무시할 파일형식 작성

- `.gitignore` 파일 규칙

  - 아무것도 없는 라인이나, `#`로 시작하는 라인은 무시한다.

  - 표준 Glob 패턴을 사용한다. 이는 프로젝트 전체에 적용된다.

  - 슬래시(`/`)로 시작하면 하위 디렉토리에 적용되지(Recursivity) 않는다.

  - 디렉토리는 슬래시(`/`)를 끝에 사용하는 것으로 표현한다.

  - 느낌표(`!`)로 시작하는 패턴의 파일은 무시하지 않는다.

  - ```
    # 확장자가 .a인 파일 무시
    *.a
    
    # 윗 라인에서 확장자가 .a인 파일은 무시하게 했지만 lib.a는 무시하지 않음
    !lib.a
    
    # 현재 디렉토리에 있는 TODO파일은 무시하고 subdir/TODO처럼 하위디렉토리에 있는 파일은 무시하지 않음
    /TODO
    
    # build/ 디렉토리에 있는 모든 파일은 무시
    build/
    
    # doc/notes.txt 파일은 무시하고 doc/server/arch.txt 파일은 무시하지 않음
    doc/*.txt
    
    # doc 디렉토리 아래의 모든 .pdf 파일을 무시
    doc/**/*.pdf
    ```

    

### Staged와 Unstaged 상태의 변경 내용을 보기

`git diff`

### 커밋하려고 Staging Area에 넣은 파일의 변경 부분을 보기

`git diff --staged` 

- 저장소에 커밋한 것과 Staging Area에 있는 것을 비교

### Staged 상태인 파일의 변경 내용을 보기

 `git diff --cached`

- `--staged` 와 `--cached` 는 같은 옵션

### Staging Area 생략하기

`git commit -a <msg>`

### 파일 삭제하기

`git rm`

### 각 커밋의 diff 결과만 보여주기

`git log -p` / `git log --path`

- `-2`옵션: 붙일 경우 최근 두 개의 결과만 보여줌

### 히스토리 통계 보기

`git log --stat`

- 어떤 파일이 수정됐는지, 얼마나 많은 파일이 변경됐는지, 또 얼마나 많은 라인을 추가하거나 삭제했는지 보여준다. 요약정보는 가장 뒤쪽에 보여준다.

### 히스토리 내용을 보여줄 때 기본 형식 이외에 여러 가지 중에 하나를 선택하기

`git log --pretty=oneline`

- `oneline` 옵션 : 각 커밋을 한 라인으로 보여준다. 이 옵션은 많은 커밋을 한 번에 조회할때 유용하다.
- `format` 옵션 :  나만의 포맷으로 결과를 출력하고 싶을 때 사용한다. 결과를 다른 프로그램으로 파싱하고자 할 때 유용하다.

### 파일 상태를 Unstage로 변경하기

`git reset HEAD <file>`

### 수정된 파일 되돌리기

`git checkout -- <file>...`

> ❗️주의 :  원래 파일로 덮어썼기 때문에 수정한 내용은 전부 사라진다. 수정한 내용이 진짜 마음에 들지 않을 때만 사용해야한다.

### 리모트 저장소 이름을 바꾸기

`git remote rename <remote-repository-name>`

### 리모트 저장소를 삭제하기

`git remote rename <remote-repository-name>`



## 태그

- 릴리즈할때 사용(v1.0)

### 태그 조회하기

`git tag`

### 검색 패턴 사용하여 태그 검색하기

`git tag -l "검색할 패턴"` / `git tag --list "검색할 패턴"`

### 태그 붙이기

- **Lightweight 태그**
  - 브랜치와 비슷한데 브랜치처럼 가리키는 지점을 최신 커밋으로 이동시키지 않는다. 단순히 특정 커밋에 대한 포인터이다.
  - `git tag v1.4-lw`

- **Annotated 태그**
  - Git 데이터베이스에 태그를 만든 사람의 이름, 이메일과 태그를 만든 날짜, 그리고 태그 메시지도 저장한다.
  - `git tag -a v1.4 -m "<msg>"`

### 태그 정보와 커밋 정보 확인하기

`git show v1.4`

### 나중에 태그하기

 `git tag -a v1.2 <commit-hash>`

### 태그 공유하기

`git push origin <tag-name>`

### 만약 한 번에 태그를 여러 개 Push 하기

`git push origin --tags`

### 태그를 Checkout 하기

`git checkout 2.0.0`

### Git Alias

- Git의 명령을 전부 입력하는 것이 귀찮다면 `git config` 를 사용하여 각 명령의 Alias을 쉽게 만들 수 있다. 

- ex)

  ```bash
  $ git config --global alias.co checkout
  $ git config --global alias.br branch
  $ git config --global alias.ci commit
  $ git config --global alias.st status
  ```

  

---

### 하던 작업 일시 중단 하기

`git stash`

> `git status -s`
>
> `git stash --keep-index`
>
> 이미 Staging Area에 들어 있는 파일을 Stash 하지 않는 명령어
>
> ---
>
> `git status -s`
>
> `git stash -u` / `git stash --include-untracked`
>
> 추적 중이지 않은 파일을 같이 저장하려면 Stash 명령을 사용할 때  
>
> ---
>
> `git stash --patch`
>
> 수정된 모든 사항을 저장하지 않는 명령어. 대신 대화형 프롬프트가 뜨며 변경된 데이터 중 저장할 것과 저장하지 않을 것을 지정할 수 있다.

### 저장한 Stash보기

`git stash list`

### 저장했던 Stash 복원하기

`git stash apply `

`git stash apply --index`

> Staged 상태였던 파일을 다시 Staged 상태로 적용시킴 

### Commit 메시지 여러 개 수정하기

1. `git rebase -i HEAD~3`

2. `git commit --amend`

3. `git rebase --continue`

- 여러 커밋 하나로 합치기
  - squash 활용