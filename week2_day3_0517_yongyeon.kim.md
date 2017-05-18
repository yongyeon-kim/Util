# pyenv, virtualenv, iPython

### pyenv

pyenv는 프로젝트별로 파이썬 버전을 따로 관리할 수 있도록 도와주는 라이브러리입니다.
여러 프로젝트를 동시에 진행하다보면, 어떤 프로젝트에서는 2.7을, 어떤 프로젝트에서는 3.4를 사용하는 식으로 다양한 버전의 사용할 수도 있고, 각각에 설치된 라이브러리간 충돌이 일어날 수도 있습니다.
 
### virtualenv
virtualenv는 파이썬 개발환경을 프로젝트별로 분리해서 관리할 수 있게 해주는 라이브러리입니다.
위의 pyenv와 다른점은, pyenv는 파이썬의 버전을 관리해주는 것이며, virtualenv는 파이썬 패키지 설치 환경을 따로 관리해줍니다.

### iPython
위의 pyenv제작자가, pyenv를 사용할 경우 쉽게 virtualenv를 사용할 수 있도록 만든 라이브러리입니다.

---

# pyenv

## pyenv 설치
- 맥

```brew install pyenv```

```brew install pyenv-virtualenv```

- 리눅스

```https://github.com/yyuu/pyenv-installer```

```curl -L https://raw.githubusercontent.com/yyuu/pyenv-installer/master/bin/pyenv-installer | bash```

## 기본 셸 변경
###zsh
http://theyearlyprophet.com/love-your-terminal.html  
bash와 비슷하게 동작하는 셸로, 사용성이 좋습니다.

#### 맥
```
brew install zsh zsh-completions
curl -L http://install.ohmyz.sh | sh
chsh -s `which zsh`
```


> chsh: /usr/local/bin/zsh: non-standard shell 오류 발생할 경우

```
sudo vim /etc/shells
맨 아래에 `which zsh`했을때의 결과를 추가 후 저장

현재 shell 확인법
echo $SHELL
```

## pyenv 설정

- 설치 후 pyenv관련 설정을 shell설정에 추가
- vi ~/.zshrc

```
export PYENV_ROOT=/usr/local/var/pyenv
if which pyenv > /dev/null; then eval "$(pyenv init -)"; fi
if which pyenv-virtualenv-init > /dev/null; then eval "$(pyenv virtualenv-init -)"; fi
```

### 파이썬 설치 전 필요 패키지
[https://github.com/yyuu/pyenv/wiki/Common-build-problems](https://github.com/yyuu/pyenv/wiki/Common-build-problems)

- 파이썬 셸 관련 설정 (macOS)

> 셸에서 방향키 관련 이슈 해결을 위한 유틸리티 설치

```
관련 유틸리티 설치 (readline, xz)

brew install readline xz
```

### 파이썬 설치

- pyenv install [version]
 : 해당하는 버전의 파이썬을 설치 함
 
```
pyenv를 사용해서 파이썬 3.4.3버전 설치

pyenv install 3.4.3
```

### - pyenv install --list
- 설치 가능한 릴리즈 리스트가 출력 된다.

### - pyenv versions
- pyenv로 설치한 릴리즈 리스트가 출력 된다.

```
➜  python pyenv versions
* system
  3.5.3 (set by /usr/local/var/pyenv/version)
```

- pyenv global 3.5.3 : pyenv에서 사용할 파이썬의 버전을 변경 한다.

```
➜  python pyenv global 3.5.3
```

```
➜  python pyenv versions
  system
* 3.5.3 (set by /usr/local/var/pyenv/version)
```





## pyenv 사용

### 1. pyenv virtualenv <version> <env_name> : 가상환경 생성

```
➜  python pyenv virtualenv 3.5.3 fc-python
```

```
➜  python pyenv virtualenv 3.5.3 fc-python
Requirement already satisfied: setuptools in /usr/local/var/pyenv/versions/3.5.3/envs/fc-python/lib/python3.5/site-packages
Requirement already satisfied: pip in /usr/local/var/pyenv/versions/3.5.3/envs/fc-python/lib/python3.5/site-packages
```

### 2. 사용할 폴더로 이동

```
cd projects
mkdir python
cd python
```

### 3. 특정 디렉토리를에서 자동적으로 사용할 가상환경 설정

```
➜  python pyenv local fc-python

(fc-python) ➜  python pyenv versions
```

설정 후 해당 폴더로 진입 하게 되면 설정 된 가상환경`'(fc-python)'`이 표시 된다.

* 가상환경 삭제

```
pyenv uninstall <env_name>
```



## ipython

### ipython 설치
`(fc-python) ➜  python pip install ipython`

### ipython 실행

> python ipython

```
fc-python) ➜  python ipython
Python 3.5.3 (default, May 17 2017, 11:27:35)
Type 'copyright', 'credits' or 'license' for more information
IPython 6.0.0 -- An enhanced Interactive Python. Type '?' for help.

In [1]:
``` 






---

### 17일 수요일 - `08. 제어문.md : for + zip` 까지 수업 함

### 파이썬 도서 추천
처음 시작하는 파이썬 ( 뱀 )
전문가를 위한 파이썬 ( 도마뱀 )
파이썬 완벽 가이드 데이비드M.비즐리