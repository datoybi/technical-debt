# Git 사용시 명령어 정리

## Commit

### 새 리포 만들었을 때

```
git remote add origin https://github.com/datoybi/Datastructure-and-Algorithm-JS.git
git branch -M main
git push -u origin main
```

### 커밋 취소하고 싶을 때

```
git reset --soft HEAD~1
git reset HEAD~3 (앞의 3개 다 없앤다는 뜻)
```

### 커밋 변경사항 보기

```
git show
```

### Readme 적용했을 때 이렇게 해보기

```
git init
git branch -M main
git remote add origin https://github.com/datoybi/blog-posting.git
git add .
git fetch
git pull origin main --allow-unrelated-histories
git commit -m "first commit"
git push -u origin main
```

```
echo "# blog-posting" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/datoybi/blog-posting.git
git push -u origin main
```

### 어느 브렌치에 있는지 보기

```
git branch
```

### checkout 안될때

```
git fetch
```

## 브랜치

### master에 저장되어 있는걸 main으로 merge 하고싶을때

```
// main브랜치에서
git merge master
commit
```

### branch 생성

```
git branch main
```

### branch 삭제

```
git branch -D master
```

### branch merge 할때 (다음에 정리하기)

```
git checkout main
git fetch // 가져오기
git pull origin main --allow-unrelated-histories
git commit
```

### 특정 브랜치 pull 하기

```
git pull git pull origin mission2_dasomyun
```

---

### 마크다운 참고 문서

https://gist.github.com/ihoneymon/652be052a0727ad59601

### 참고 git menual

https://backlog.com/git-tutorial/kr/stepup/stepup2_2.html

### readme.md 떄문에 고생할때 참고

https://stackoverflow.com/questions/2452226/master-branch-and-origin-master-have-diverged-how-to-undiverge-branches/2452610

---

## ERROR

### git merge 할때 자꾸 unrelated histories 에러 뜰때

C:\dsy\Workspace\krsoftServer>git pull origin main --allow-unrelated-histories

### Large files detected 관련 에러처리

- 기존에 add 해둔 내용이 있다면 unstaging

```
git rm -r --cached "*"
```

### remote origin already exists. 에러

```
git remote remove origin
```

### clone 할때 명령어

```
git branch -m master main
git fetch origin
git branch -u origin/main main
git remote set-head origin -a
```

### 잔디 칠하기

git log 해서 날짜 따오기 Tue Nov 9 18:07:24 2021 +0900

```
git commit --amend --no-edit --date "Wed Jul 20 18:02:13 2022 +0900"
git pull
git push origin main
```

### 특정 브렌치만 clone 하고 싶을 때

```
git clone -b datoybi-patch-1 --single-branch https://github.com/datoybi/hello-github-actions.git
```

### 모든 브렌치 clone

```
git clone https://github.com/datoybi/hello-github-actions.git // 클론하고
git branch -a // 원격저장소에 어떤 브랜치가 있는지 확인하고
git checkout datoybi-patch-1 // 쳌아웃 이건가 밑에껀가 하니까 됐다.
git checkout origin/datoybi-patch-1
```

### git action

Workflow: 자동적으로 처음부터 끝까지 실행되는 트리거
Job: wrkflow의 섹션. 하나, 그 이상의 스텝으로 구성되어 있다. 템플릿은 빌드 잡을 위해 스텝들을 정의한다.
Step: 자동화의 하나의 효과를 나타낸다. 스텝은 유닛이다
Action: 자동적으로 컴퓨터와 호환되는 workflows를 작성하는 방법이다.

### 이런 에러 날때

See git-pull(1) for details.

    git pull <remote> <branch>

If you wish to set tracking information for this branch you can do so with:

    git branch --set-upstream-to=origin/<branch> main

저장소에는 있는데 커밋하려는 내 코드에는 없어서

```
git branch --set-upstream-to=origin/main main
git pull
```

### gitignore를 뒤늦게 해서 추적하지 않는 파일 삭제하고 싶을 떄

```
$ git rm -r --cached . // cache에 기록된 tracking 중인 파일리스트 삭제
$ git add .
$ git commit -m 'remove ignored file'
$ git push {remote} {branch}
```
