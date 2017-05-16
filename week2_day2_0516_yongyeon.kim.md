# git 
- 참고자료 : https://git-scm.com/book/ko/v2

----

## git reset HEAD 파일명

```
➜  second-project git:(master) ✗ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	new file:   CONTRIBUTING.md
	modified:   README.md
```

위와 같이 add를 잘 못 하여 Staging Area에 잘 못 넣었을 때,
```git reset HEAD CONTRIBUTING.md```를 입력 하면 아래와 같이 Staging Area 에서 제거 된다.

```
➜  second-project git:(master) ✗ git reset HEAD CONTRIBUTING.md

➜  second-project git:(master) ✗ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	modified:   README.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	CONTRIBUTING.md
```

## git checkout -- 파일명

- 수정한 내용을 되돌린다. ( 작업 내용 초기화 )
단, 모든 것이 이전으로 되돌아가기 때문에 정말 마음에 안들 경우에만 사용해야 한다.

```
...
	modified:   CONTRIBUTING.md

no changes added to commit (use "git add" and/or "git commit -a")
➜  second-project git:(master) ✗ git checkout -- CONTRIBUTING.md

➜  second-project git:(master) git status
On branch master
nothing to commit, working directory clean
```

## git remote 리모트저장소URL

- 현재 디렉토리를 remote 저장소와 연결

```
git remote add origin https://github.com/yongyeon-kim/remote-project.git
```

- 현재 프로젝트의 remote 저장소 위치 확인

```
➜  remote-project git:(master) git remote -v
origin	https://github.com/yongyeon-kim/remote-project.git (fetch)
origin	https://github.com/yongyeon-kim/remote-project.git (push)
```

- remote 저장소에 업로드

```
➜  second-project git:(master) git push origin master
Counting objects: 10, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (6/6), done.
Writing objects: 100% (10/10), 828 bytes | 0 bytes/s, done.
Total 10 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), done.
To https://github.com/yongyeon-kim/second-project.git
 * [new branch]      master -> master
```

## git clone origin 리모트저장소URL

- 원격 저장소에 저장돼 있는 데이터를 현재 디렉토리에 다운 받는다.

```
➜  git-practice git clone https://github.com/yongyeon-kim/second-project.git
Cloning into 'second-project'...
remote: Counting objects: 10, done.
remote: Compressing objects: 100% (5/5), done.
remote: Total 10 (delta 1), reused 10 (delta 1), pack-reused 0
Unpacking objects: 100% (10/10), done.
Checking connectivity... done.
```

## git remote add 저장소명 remote저장소URL

- 현재 프로젝트에 두번째 origin(기본) 저장소 외의
두번째 저장소를 생성하며 해당 저장소의 이름을 설정 하는 기능



## git clone remote저장소URL 디렉토리명
- 별도의 디렉토리를 생성 한 후 해당 디렉토리 내부에 소스를 받아온다.

```
➜  git-practice git clone https://github.com/yongyeon-kim/remote-project.git remote-project-clone
Cloning into 'remote-project-clone'...
remote: Counting objects: 3, done.
remote: Total 3 (delta 0), reused 3 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), done.
Checking connectivity... done.

➜  git-practice l ./remote-project-clone
total 8
drwxr-xr-x   4 yykim  staff   136B  5 16 12:04 .
drwxr-xr-x   6 yykim  staff   204B  5 16 12:04 ..
drwxr-xr-x  13 yykim  staff   442B  5 16 12:10 .git
-rw-r--r--   1 yykim  staff    14B  5 16 12:04 hello.txt
```

## git fetch origin

```
➜  remote-project-clone git:(master) git status
On branch master
Your branch is behind 'origin/master' by 1 commit, and can be fast-forwarded.
  (use "git pull" to update your local branch)
nothing to commit, working directory clean

```

```
➜  remote-project-clone git:(master) git merge origin/master
Updating 1ce909b..50394e3
Fast-forward
 README.md | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 README.md
```

## git pull origin master

저장소의 최신 데이터를 현재 디렉토리에 덮어씌운다.


## git tag
- git tag 현재 작업간의 태그 리스트 조회

```
➜  remote-project git:(master) git tag
v1.0
```

- git tag -a 태그명 : 태그를 추가 한다.

```
➜  remote-project git:(master) git tag -a v1.0
```

- git push origin 태그명 : 태그를 저장소에 저장 한다.

```
➜  remote-project git:(master) git push origin v1.0
Counting objects: 1, done.
Writing objects: 100% (1/1), 178 bytes | 0 bytes/s, done.
Total 1 (delta 0), reused 0 (delta 0)
To https://github.com/yongyeon-kim/remote-project.git
 * [new tag]         v1.0 -> v1.0
```

- 예전 커밋 태그 하기

```
$ git log --pretty=oneline
15027957951b64cf874c3557a0f3547bd83b3ff6 Merge branch 'experiment'
a6b4c97498bd301d84096da251c98a07c7723e65 beginning write support
...
```

커밋의 키값을 조회 한 후
**git tag -a 태그명 커밋키값** 을 입력하여 예전 커밋에 태그를 단다.

```
$ git tag -a v1.2 9fceb02
```

----


# branch
## git branch

-  git branch -v : 현재 프런치 조회

```
➜  remote-project git:(master) git branch
* master
```

## git branch 브랜치명

- 입력한 이름으로 새로운 브랜치를 생성함

```
git branch develop : develop 라는 브랜치를 새로 생성함
```

## git branch -m 변경전이름 변경후이름
git branch -m master production



## git checkout 브랜치명

- 사용할 브랜치 이동(변경)

```
➜  remote-project git:(master) git checkout testing
Switched to branch 'testing'

➜  remote-project git:(testing) git branch -v
  master  50394e3 add READEME.md
* testing 50394e3 add READEME.md
```

- 브랜치 조회 시 별 표시가 이동 됨

```
➜  remote-project git:(testing) echo 'text' > test.txt

➜  remote-project git:(testing) ✗ git add test.txt

➜  remote-project git:(testing) ✗ git commit -m 'add test.txt'
[testing e69ac35] add test.txt
 1 file changed, 1 insertion(+)
 create mode 100644 test.txt
```

test.txt 생성 작업 후 checkout을 통해 다시 master로 이동 후 파일을 조회 해 보면,
test.txt 파일이 사라진 것을 확인 할 수 있다.

```
➜  remote-project git:(testing) l
total 24
drwxr-xr-x   6 yykim  staff   204B  5 16 12:38 .
drwxr-xr-x   6 yykim  staff   204B  5 16 12:04 ..
drwxr-xr-x  13 yykim  staff   442B  5 16 12:38 .git
-rw-r--r--   1 yykim  staff    17B  5 16 12:07 README.md
-rw-r--r--   1 yykim  staff    14B  5 16 12:01 hello.txt
-rw-r--r--   1 yykim  staff     5B  5 16 12:38 test.txt

➜  remote-project git:(testing) git checkout master
Switched to branch 'master'

➜  remote-project git:(master) l
total 16
drwxr-xr-x   5 yykim  staff   170B  5 16 12:40 .
drwxr-xr-x   6 yykim  staff   204B  5 16 12:04 ..
drwxr-xr-x  13 yykim  staff   442B  5 16 12:40 .git
-rw-r--r--   1 yykim  staff    17B  5 16 12:07 README.md
-rw-r--r--   1 yykim  staff    14B  5 16 12:01 hello.txt
```

이 것은 파일이 삭제 된 것이 아니며, 파일 추가 작업은 testing 브랜치로 진행이 되었기 때문에이다
최종 취합 되기 전에는 testing 브랜치 에서만 파일이 보인다.

## git checkout -b 브랜치명
- 브랜치 생성과 동시에 해당 브랜치로 checkout 한다.

```
➜  merge-basic git:(production) git checkout -b hotfix
Switched to a new branch 'hotfix'
```

## git branch -d 브랜치명

- 브랜치 삭제

```
➜  merge-basic git:(production) git branch -d hotfix
Deleted branch hotfix (was 108f8e7).
```

---

# git merge 브랜치명

- git 소스 코드 병합

변경 작업을 수행하던 hotFix 에서 production으로 checkout 한 후
git merge hotFix 명령을 수행하면,
hotFix 브랜치의 소스코드를 production 소스코드로 가져와 합치다는 것을 의미 한다.

```
➜  merge-basic git:(production) git merge hotFix
Updating bf97cc9..108f8e7
Fast-forward
 CONTRIBUTE.md | 1 +
 README.md     | 6 ++++++
 2 files changed, 7 insertions(+)
 create mode 100644 CONTRIBUTE.md
```

## MERGE CONFLICT

- 복수의 커밋에 같은 파일이 수정 되어 merge 될 경우 CONFLICT가 발생한다.

```
➜  merge-basic git:(production) git merge develop
Auto-merging README.md
CONFLICT (content): Merge conflict in README.md
Automatic merge failed; fix conflicts and then commit the result.
```

**Merge conflict in README.md** conflict가 발생한 소스 파일을
적절히 수정한 후 git add / commit 을 진행 한다.

```
<<<<<<< HEAD:index.html
<div id="footer">contact : email.support@github.com</div>
=======
<div id="footer">
 please contact us at support@github.com
</div>
>>>>>>> iss53:index.html
```

**'====' 사이의 HEAD와 브랜치(iss53) 사이의 소스를 적절히 수정**

---

# Git 도구 - Stashing과 Cleaning

## git stash

- 커밋하지 않고 나중에 다시 돌아와서 작업을 다시 하고 싶을 것이다. 이 문제는 `git stash`라는 명령으로 해결할 수 있다.

- Stash 명령을 사용하면 워킹 디렉토리에서 수정한 파일들만 저장한다. Stash는 **Modified이면서 Tracked 상태인 파일과 Staging Area에 있는 파일들을 보관해두는 장소**다. 아직 끝내지 않은 수정사항을 스택에 잠시 저장했다가 나중에 다시 적용할 수 있다.

```
➜  simplegit-progit git:(test) ✗ git status
On branch test
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   README
	modified:   Rakefile
	modified:   lib/simplegit.rb

no changes added to commit (use "git add" and/or "git commit -a")
```

테스트 결과 modified 상태가 아닌 경우 동작 하지 않는다
HEAD 상태에 있는 파일이 modified가 없다고 하는 것 같다....;;;

위와 같이 modified 상태의 파일들이 있는 상태에서
git stash 명령을 사용하면 아래와 같이 워크디렉토리에 아무 것도 없어 진다

```
➜  simplegit-progit git:(test) ✗ git stash
Saved working directory and index state WIP on test: ca82a6d changed the verison number
HEAD is now at ca82a6d changed the verison number

➜  simplegit-progit git:(test) git status
On branch test
nothing to commit, working directory clean
```

- git stash list : stash 상태인 작업리스트를 출력 한다.

```
stash@{0}: WIP on test: ca82a6d changed the verison number
```

- git stash apply stash@{n} : n번에 해당하는 stash 리스트의 작업을 불러온다.

```
➜  simplegit-progit git:(test) git stash apply stash@{0}
On branch test
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   README
	modified:   Rakefile
	modified:   lib/simplegit.rb

no changes added to commit (use "git add" and/or "git commit -a")
```

- git stash drop : stash 상태인 작업 리스트를 삭제 한다.

```
➜  simplegit-progit git:(test) ✗ git stash drop
Dropped refs/stash@{0} (227eaa3e408bbcdea6d25337626b68673b5451df)

➜  simplegit-progit git:(test) ✗ git stash list
➜  simplegit-progit git:(test) ✗
```

## git clean

- 작업하고 있던 파일을 Stash 하지 않고 단순히 그 파일들을 치워버리고 싶을 때가 있다. `git clean` 명령이 그 일을 한다.

- 보통은 Merge나 외부 도구가 만들어낸 파일을 지우거나 이전 빌드 작업으로 생성된 각종 파일을 지우는 데 필요하다.

- git clean 명령을 사용하면 워킹 디렉토리 안의 추적하고 있지 않은 모든 파일이 지워지기 때문에 함부로 사용하면 안된다.

- git clean -d` : 추적 중이지 않은 모든 정보를 워킹 디렉토리에서 삭제

- git clean -d -n : 가상으로 실행 한 후 결과를 출력 해달라는 명령

```

...

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	test.txt

no changes added to commit (use "git add" and/or "git commit -a")
➜  simplegit-progit git:(test) ✗ git clean -d -n
Would remove test.txt

➜  simplegit-progit git:(test) ✗ git clean -f -d
Removing test.txt


```

위와 같이 스테이지에 올라가지 않은 파일을 모두 지울 수 있으며
-n 옵션을 통해 가상 테스트 결과를 출력해 볼 수 있다.

`.gitignore`에 명시했거나 해서 무시되는 파일은 지우지 않는다.


----------

# Git 도구 - 검색

## git grep -n 문자열

- 워킹 디렉토리 내의 내용 중 문자열이나 정규표현식으로 검색할 수 있으며
  -n 옵션을 통해 라인 넘버를 같이 확인 할 수 있다.

```
➜  simplegit-progit git:(test) ✗ git grep -n R

README:1:SimpleGit Ruby Library
Rakefile:6:    s.platform  =   Gem::Platform::RUBY
Rakefile:11:    s.summary   =   "A simple gem for using Git in Ruby code."
Rakefile:16:Rake::GemPackageTask.new(spec) do |pkg|
(END)
```
## git log -L :함수(문자열):파일명

- 특정 파일의 함수(문자열)가 포함된 커밋 정보 로그를 출력 한다.

```
$git Log -L :Scott:README

commit a11bef06a3f659402fe7563abf99ad00de2209e6
Author: Scott Chacon <schacon@gmail.com>
Date:   Sat Mar 15 10:31:28 2008 -0700

    first commit

diff --git a/README b/README
--- /dev/null
+++ b/README
@@ -0,0 +6,1 @@
+Author : Scott Chacon
\ No newline at end of file
```

----------

# Git 도구 - 히스토리 단장하기

## git commit --amend
- 최근에 커밋한 내용에 누락 된 것을 추가 한다. ( 마지막 커밋을 수정할 수 있게 열어 준다 )
- 종종 완료한 커밋을 수정해야 할 때가 있다. 너무 일찍 커밋했거나 어떤 파일을 빼먹었을 때 그리고 커밋 메시지를 잘못 적었을 때 한다. 다시 커밋하고 싶으면 --amend 옵션을 사용한다.

```
$ git commit -m 'initial commit'
$ git add forgotten_file
$ git commit --amend
```

----------

# Git 도구 - Reset 명확히 알고 가기

- HEAD : 마지막 커밋의 스냅샷, 다음 커밋의 부모 커밋

```
HEAD는 현재 브랜치를 가리키는 포인터이며,
브랜치는 브랜치에 담긴 커밋 중 가장 마지막 커밋을 가리킨다. 

지금의 HEAD가 가리키는 커밋은 바로 다음 커밋의 부모가 된다.
단순하게 생각하면 HEAD는 마지막 커밋의 스냅샷이다.
```

- index : 다음에 커밋할 스냅샷

```
Index는 바로 다음에 커밋할 것들이다. 
이미 앞에서 우리는 이런 개념을 'Staging Area'라고 배운 바 있다.
'Staging Area'는 사용자가 git commit 명령을 실행했을 때
Git이 처리할 것들이 있는 곳이다.

먼저 Index는 워킹 디렉토리에서 마지막으로 Checkout 한 브랜치의 파일 목록과
파일 내용으로 채워진다.

이후 파일 변경작업을 하고 변경한 내용으로 Index를 업데이트 할 수 있다.
이렇게 업데이트 하고 git commit 명령을 실행하면 Index는 새 커밋으로 변환된다
```

- 워킹 디렉토리 : 샌드 박스

```
워킹 디렉토리는 실제 파일로 존재한다.
바로 눈에 보이기 때문에 사용자가 편집하기 수월하다.
워킹 디렉토리는 샌드박스로 생각하자.
커밋하기 전에는 Index(Staging Area)에 올려놓고 얼마든지 변경할 수 있다.

즉, 커밋 하기 전까지의 작업 내용이 존재하는 작업 공간을 의미 한다.
```


----------

# 명령어 팁

## git log --oneline --decorate --graph --all
- 현재 브랜치의 상태를 그래프로 표시해 준다.

```
* ddb0004 (HEAD -> master) add test.txt
| * e69ac35 (testing) add test.txt
|/
* 50394e3 (tag: v1.0, origin/master) add READEME.md
* 1ce909b First commit
```

## git log --decorate

- 로그의 브랜치, 태그 등의 정보를 출력해 준다.

```
commit 50394e3a8f5413ed9de369e9a8f4556efa30b9e0 (HEAD -> master, tag: v1.0, origin/master, testing)
Author: yongyeon-kim <assavictory@gmail.com>
Date:   Tue May 16 12:07:29 2017 +0900

    add READEME.md
```


