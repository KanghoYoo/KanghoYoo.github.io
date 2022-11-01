# Rebase
- master 브랜치의 기존의 마지막 커밋 뒤에 병합할 브랜치의 커밋들이 합쳐지게 하여 master 브랜치에 재배치(rebase) 하는 것
- 커밋내용들을 재정렬함
- 히스토리를 작성

## Git에서 Merge와 Rebase의 차이
- Merge는 기본적인 git의 병합 방법으로, conflict이 있다면 해결하는 커밋이 하나 더 추가된다
- 히스토리를 보존
- commit이 되돌리거나 git log를 확인할 때, 한 눈에 들어오지 않은 단점

- Rebase는 커밋의 시간과 관계없이 마지막에 merge되는 branch의 commit을 가장 뒤에 붙이는 것

## Rebase 사용법
```
git pull origin master
git pull --rebase origin master
$ git add .
$ git rebase --continue