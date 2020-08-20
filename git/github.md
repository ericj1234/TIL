### # Git 기초

> Git은 분산형 버전관리시스템(DVCS)이다.
>
> 

Git을 윈도우에서 활용하기 위해서는 [git bash](https://gitforwindows.org)를 설치해야 한다. 



## 1. 저장소 초기화

```bash
$ git init
Initialized empty Git repository in C:/Users/i/Desktop/TIL/.git/

(master) $
```

* 로컬 저장소를 만들고 나면, ` .git/`라는 폴더가 생성되고, bash에 `(master)`라고 표기된다.
* 반드시 저장소를 만들기 전에 원하는 디렉토리인지 확인하는 습관을 가지고, 저장소 내부에 저장소를 만들지는 말자. 
  * 예) Desktop -> git 저장소, TIL -> 다른 git 저장소 (X)

# 2. `add`

작업한 내용을 커밋 대상 목록에 추가한다.

```bash
$ git add .			# 현재 디렉토리(하위 디렉토리 포함)
$ git add a.html	# 특정 파일
$ git add b.html c.html	# 특정 다수 파일
$ git add blog/			# 특정 폴더
```

```bash
# 작업 후 상태
$ git status
On branch master

No commits yet
# Untracted files => Git으로 관리된 적 없는 파일
Untracked files:
# 커밋 될 것들에 포함시키기 위해서는 add 명령어를 써라
  (use "git add <file>..." to include in what will be committed)
        github.md
        markdown-images/
        markdown.md
# 총평
# 커밋될 곳에 없다(nothing)
# 하지만, 새로 생성한 파일(untracked files)은 존재한다.
nothing added to commit but untracked files present (use "git add" to track)

```

```bash
$ git add .
```

```bash
# add 명렁어 후 상태
$ git status
On branch master

No commits yet
# 커밋이 될 변경 사항들
# Working directory X 
# Staging area ()
Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   github.md
        new file:   markdown-images/capture.png
        new file:   "markdown-images/\353\213\267\354\247\200\354\261\214\353\246\260\354\240\200.jpg"
        new file:   markdown.md

```

```bash
$ git commit  -m 'Add markdown.md'
[master (root-commit) 325ab94] Add markdown.md
 4 files changed, 80 insertions(+)
 create mode 100644 github.md
 create mode 100644 markdown-images/capture.png
 create mode 100644 "markdown-images/\353\213\267\354\247\200\354\261\214\353\246\260\354\240\200.jpg"
 create mode 100644 markdown.md

```

* 커밋은 버전(이력)을 기록하는 명령어이다.
* 커밋 메시지는 해당하는 이력을 나타낼 수 있도록 작성하여야 한다. 
* 커밋 이력을 확인하기 위해서는 아래의 명령어를 사용한다.

```bash
$ git log
commit 325ab94c3002356b8c07a6797afe7d713bc66e92 (HEAD -> master)
Author: BeomheeJang <ericj1234@naver.com>
Date:   Thu Aug 20 14:58:29 2020 +0900

    Add markdown.md
$ git log -1
$ git log -oneline
325ab94 (HEAD -> master) Add markdown.md
$ git log --oneline -1
```

```bash
$ git status
On branch master
# WD (Working Directory) X
# Staging area X	
nothing to commit, working tree clean
```

# Git 원격 저장소 활용

Git 원격 저장소 기능을 제공 해주는 서비스는 `gitlab, bitbucket, github`등이 있다.

# 0. 원격 저장소 설정

```bash
$ git remote and origin {url}
$ git remote and origin https://github.com/ericj1234/TIL.git
```

* git, 원격저장소를 추가(`add`)하고 `origin`이라는 이름으로 `url`으로 설정
* 설정된 저장소를 확인하기 위해서는 아래의 명령어를 사용한다.

```bash
$ git remote -v
origin  https://github.com/ericj1234/TIL.git (fetch)
origin  https://github.com/ericj1234/TIL.git (push)
```

# 원격 저장소에 push

```bash
$ git push origin master
Enumerating objects: 11, done.
Counting objects: 100% (11/11), done.
Delta compression using up to 8 threads
Compressing objects: 100% (9/9), done.
Writing objects: 100% (11/11), 31.55 KiB | 10.52 MiB/s, done.
Total 11 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/ericj1234/TIL.git
 * [new branch]      master -> master
Branch 'master' set up to track remote branch 'master' from 'origin'.
```



 