### 1. git 설치

--

### 2. vim
 + .vimrc 셋팅 

```
syntax on 
set tabstop=8 
set expandtab 
set softtabstop=4 
set shiftwidth=4 
set number 
filetype indent on 
```
 
 ### 3. zshrc 설치 및 ~/.zshrc 셋팅
 + source ~/.zshrc ( 수정 된 셋팅 파일 수동 적용 - 터미널 재시작 안해도 됨 ) 

--

### 4. git
 + https://git-scm.com/book/ko/v2
 + https://git-scm.com/book/en/v2/images/lifecycle.png
 
 + touch README.md - 빈파일 생성
 
 + git init - 해당 디렉토리를 git 작업 공간으로 만듦
 
 + git add README.md - 해당(작업한) 파일을 git stage 영역에 올린다 ( 저장한다 )
 
 + git commit - HEAD 영역에 올림 ( 작업 내용 취합, 서버에 반영되는 것은 아니며, 로컬에 취합된다. 서버 소스에 적용할 묶음 단위로 이해하면 쉽다. )
 
 + git log 커밋 된 이력을 확인 할 수 있다.
 
 + git diff --staged ( staged 에 있는 파일의 변경 상태만 확인 한다. )
 diff --git a/abc3.txt b/abc3.txt
new file mode 100644
index 0000000..9ed4614
--- /dev/null
+++ b/abc3.txt
@@ -0,0 +1 @@
+ABCD

 + git diff ( 전체영역 modified 포함 한 파일의 변경 상태를 확인 한다.

diff --git a/abc3.txt b/abc3.txt
index 9ed4614..923c5f7 100644
--- a/abc3.txt
+++ b/abc3.txt
@@ -1 +1,2 @@
 ABCD
+EFGH

+ echo 문자열 
( 콘솔에 문자열을 바로 출력 한다. 저장 X )

+ echo '문자열' > 파일명
echo 'show me the money' > abc4.txt
( 파일을 생성하며 '' 내의 문자열을 저장 한다. )

+ cat 파일명 ( 콘솔에서 간단하게 파일 내용을 확인 할 수 있다. 콘솔에 내용 출력 됨 )

+ vim ./.gitinore ( Git으로 관리 하지 않을 파일 형식을 무시하기 위한 케이스를 저장해 놓는다. )

+1 .gitignore 파일에 입력하는 패턴은 아래 규칙을 따른다.

아무것도 없는 라인이나, `#`로 시작하는 라인은 무시한다.

표준 Glob 패턴을 사용한다.

슬래시(/)로 시작하면 하위 디렉토리에 적용되지(Recursivity) 않는다.

디렉토리는 슬래시(/)를 끝에 사용하는 것으로 표현한다.

느낌표(!)로 시작하는 패턴의 파일은 무시하지 않는다.
+2 # 확장자가 .a인 파일 무시
*.a

-# 윗 라인에서 확장자가 .a인 파일은 무시하게 했지만 lib.a는 무시하지 않음
!lib.a

-# 현재 디렉토리에 있는 TODO파일은 무시하고 subdir/TODO처럼 하위디렉토리에 있는 파일은 무시하지 않음
/TODO

-# build/ 디렉토리에 있는 모든 파일은 무시
build/

-# doc/notes.txt 파일은 무시하고 doc/server/arch.txt 파일은 무시하지 않음
doc/*.txt

-# doc 디렉토리 아래의 모든 .pdf 파일을 무시
doc/**/*.pdf


--

+ ln -s 원본파일경로 사용할현재경로 ( 링크를 통해 드랍박스를 통한 셋팅 파일의 백업을 사용 할 수 있다. )

+ git rm
+ git mv
+ git clone
➜  git-practice git clone https://github.com/schacon/simplegit-progit
Cloning into 'simplegit-progit'...
remote: Counting objects: 13, done.
remote: Total 13 (delta 0), reused 0 (delta 0), pack-reused 13
Unpacking objects: 100% (13/13), done.
Checking connectivity... done.
➜  git-practice ls -al
total 8
drwxr-xr-x  5 yykim  staff  170  5 15 16:45 .
drwxr-xr-x  4 yykim  staff  136  5 15 14:05 ..
drwxr-xr-x  9 yykim  staff  306  5 15 16:22 first-project
drwxr-xr-x  6 yykim  staff  204  5 15 16:45 simplegit-progit

+ git log -p -2
-p : 변경된 내용을 상세히 출력 한다.
-2 : 최근 몇 개의 커밋만 출력 한다.

+ 로그 조회 제한 조건
git log --since=2.weeks