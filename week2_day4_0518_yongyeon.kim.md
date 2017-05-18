## while문 (반복문)

## 컴프리헨션
- for + if
[item for item in range(1, 10) if item % 2 ==0]

---

# 함수

# 스코프(영역)

> 18일 스코프(영역) 까지 수업 함



---

# 팁
## setting 파일 DropBox 연동
- dropbox 디렉토리에 셋팅파일을 관리할 공유 디렉토리 생성

```
mkdir mac-settings

/Users/yykim/Dropbox/mac-settings
```

- 기존 설정 파일을 공유 디렉토리에 이동

```
➜  ~ mv ./.zshrc /Users/yykim/Dropbox/mac-settings/
```

- 심볼릭 링크 생성
 : ln -s 원본경로 링크파일경로

```
➜  ~ ln -s /Users/yykim/Dropbox/mac-settings/.zshrc ./.zshrc
```








