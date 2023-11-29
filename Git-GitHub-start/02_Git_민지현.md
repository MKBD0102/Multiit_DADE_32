# Git
>(버전을 통해, 분산된 방식으로)   
코드를 관리하는 도구

* SCM(Source Code Management): 코드 관리 도구
* VCS(Version Control System): 버전 관리 시스템(도구)
* DVCS(Distributed VCS): 분산형 버전 관리 시스템(도구)

## Git 명령어
> `git [명령어]`
### 1. 버전 관리 Git 명령어
#### (1) `git init`
> Git 프로젝트 시작
- Git은 폴더 단위로 코드를 관리
- Git 프로젝트 시작 전에는 해당 프로젝트를 관리할 폴더 생성
- 결과: 프로젝트 폴더 내에 `.git` 폴더 생성
```bash
$ git init
Initialized empty Git repository in C:/Users/User/test/.git/
```

#### (2) `git stataus`
> Git 현재 상태 출력
- `git init` 직후
```bash
$ git status
On branch master
-> master라는 브랜치 위에 있어요.

No commits yet
-> 아직 commit이 없어요.

nothing to commit (create/copy files and use "git add" to track)
-> commit할 것이 없어요.(다음으로 해야할 것 설명)
```

- `a.txt` 파일 생성 후
```bash

...

Untracked files: -> 추적되지 않은 파일이 있어요.
    (use "git add <file>..." to include in what will be committed)
        a.txt
    -> commit 될 것에 포함시키고 싶으면 git add <파일명>을 사용

nothing added to commit but untracked files present (use "git add" to track)
-> commit할 것은 없어요. 그러나 추적되지 않은 파일은 있어요.(추적하고 싶으면 git add)
```

- `git add a.txt` 입력 후
```bash

...

Changes to be committed:
    (use "git rm --cached <file>..." to unstage)
        new file: a.txt
```

- `git commit` 후
```
nothing to commit, working tree clean
-> commit 할 게 없음. working tree(== working directory)가 깔끔해요.
```

- 파일 수정 후
```bash
On branch master
Changes not staged for commit:
-> commit하기 위해 stage 되지 않은 변경 사항이 있어요.

    (use "git add <file>..." to update what will be committed)
    (use "git restore <file>..." to discard changes in working directory)
        modified: a.txt

no changes added to commit (use "git add" and/or "git commit -a")
```

#### (3) `git add [파일/폴더]`
> commit을 하기 위한(== 버전을 생성하기 위한 준비단계)
- `git add .`: 현재 폴ㄹ더의 모든 변경 사항 stage

#### (4) `git commit -m 메세지`
> commit == 버전을 생성 == 현재상태의 스냅샷 촬영
- 최초 commit 시
```
Author identity unknown -> 작자미상

*** Please tell me who you are. -> 당신이 누군지 알려주세요.

Run -> 아래의 명령어를 실행주세요.

    git config --global user.email "you@example.com"
    git config --global user.name "Your Name"
```

#### (5) `git config`
> Git에 관한 설정
- `git config --global user.email "이메일"` : global(전역으로) user의 email을 설정
- `git config --global user.email` : 설정값 확인

#### (6) `git log`
> 현재까지의 commit을 출력
- `git log` 출력화면
```
commit 1a7d9384d2f9a064e2ddb4719306defeb51ac3cf (HEAD -> master)
Author: John Kang <hphk.john@gmail.com>
-> 작성자
Date: Tue Mar 16 15:55:10 2021 +0900
-> 날짜

    first commit
    -> 커밋 메시지
```

- `git log --oneline` : 한줄로 출력
```
7c7abf0 (HEAD -> master) Add title
1a7d938 first commit
```

### 2. 백업 Git 명령어
#### (1) `git remote`
> 원격 저장소(Remote Repository)에 대한 정보
- `git remote add`: 원격 저장소 추가
    - `git remote add [저장소이름] [저장소주소]`
    - `git remote add origin https://github.com/xxx`

#### (2) `git push`
> 원격 저장소에 프로젝트 업로드
- `git push [저장소이름] [브랜치이름]`
- `git push origin master`