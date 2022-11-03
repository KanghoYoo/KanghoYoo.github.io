---

title: GitHub Page에서 Fork한 레파지토리 잔디밭 적용시키기
date: 2022-11-01 +/-TTTT
categories: [Git&GitHub, GitHub-Pages]
tags: [github-page] # TAG names should always be lowercase

---

# GitHub Page에서 Fork한  Repository 잔디 심기

### ❗️문제 상황

- 블로그는 잘 작동이 되나, 지금까지 입력한 Commit 내역이 GitHub Page에 잔디밭이 적용 안됨
  - GitHub에 잔디 심는 기준
    - GitHub 계정과 Commit 이메일 계정이 동일 해야함
    - 자신의 Repository에서 작업해야함



### 💡 해결 방안

- 새 레파지토리 생성 후, Fork한 이전 레파지토리를 Clone하여 미리 생성한 새 레파지토리에 넣기



1. GitHub Page에서 오른쪽 상단의  `New repository` 클릭 후 생성
2. Fork 하여 작업했던 레파지토리 주소를 Copy
3. Terminal에서 Copy한 Fork 레파지토리를 bare clone 진행
   - `git clone --bare Fork했던 레파지토리 주소`
4. 미리 생성했던 새 레파지토리로 Mirror-push
   - `cd Fork했던 레파지토리 주소 `
   - `git push --mirror 새 레파지토리 주소`
5. Clone 했던 Fork 레파지토리 삭제
   - `cd ..`
   - `rm -rf Fork해던 레파지토리 파일명`



---

### 📝 새로 알게된 Git 명령어

- `git clone --bare 레파지토리 주소`: 레파지토리 자체를 복사해오는 명령어 

  - 브랜치를 직접 복사함, 커밋 이력만 담고있음

  - > non-bare clone은 원격 추적 브랜치를 설정하고 HEAD를 위한 Local 브랜치만 생성

- `git clone --mirror 레파지토리 주소`:  모든참조가 있는 그대로 완벽하게 복사되며, 모든 커밋 이력들을 담고 있음

