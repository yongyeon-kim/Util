# #### 1주 2일차

- 수업자료 : [HTML,CSS,Sass.pdf](https://github.com/Fastcampus-WPS-5th/HTML-CSS/blob/master/HTML%2CCSS%2CSass.pdf)

---------
## 1. HTML - 	Hyper Text Markup Language
### 마크업 언어
태그 등을 이용하여 문서나 데이터의 구조를 명기하는 언어


### "하이퍼 텍스트"
링크를 이용해 웹 페이지를 서로 연결하는 것을 의미


`마크업을 이용해 www의 페이지를 서로 오갈 수 있는 웹 문서를 만드는 언어`


## 2. 웹 표준
### W3C
World Wide Web Consortium.

### 웹 표준
WWW을 서술하고 정의하는 공식 표준 및 규격

### 웹 표준 지원 확인
http://html5test.com


## 3. HTML의 기본 구조
```
<!DOCTYPE html>
<html>
<head>
	<title>Document</titile>
</head>
<body>

**본문이 들어갈 자리**
<!-- 주석 표시 -->

</body>
</html>
```

- `<!DOCTYPE html>`은 html5 문서 형식임을 의미
- `<html>`은 html 문서의 시작과 끝을 의미
- `<head>`는 html 문서의 기본 정보를 포함
- `<body>`는 본문


## 4. 태그의 요소와 속성
(Element & Attribute)

`<요소 속성="값">`<br />
`<요소 속성="값>내용</요소>`



##5. Form
 
**form** 은 브라우저(클라이언트)에서 서버로 데이터를 전송하기 위해 사용하는 태그


### form-method
*method*는 폼에서 서버로 데이터를 전송하는 방식을 결정한다. 

- GET : URL에 데이터를 담아 전달 
- POST : URL과는 별도로 데이터를 전달 

### form-action 
form에서 데이터를 전송할 URL 

### input 태그  및  주요속성 

```
  <form action="">
    <!-- input#username[type=text] -->
    <input type="text" name="username"><br>
    <input type="radio" id="radio"><br>
    <input type="checkbox" id="checkbox"><br>
    <input type="button" value=button><br>
    <input type="file" id="file"><br>
    <input type="submit"><br>
    <input type="reset"><br>
    <input type="hidden" id="hidden" value="hiddenValue">
    </div>
  </form>
```

### select 태그 

```
      <select name="number" id="">
        <!-- option[value=$]*4 -->
        <option value="1">First</option>
        <option value="2">Second</option>
        <option value="3">Third</option>
        <option value="4">Fourth</option>
      </select>
```


#### fieldset, legend 태그 

```
  <form action="">
    <fieldset>
      <legend>
        <b>기본정보</b>
      </legend>
      <div>
        <label for="id"><b>ID </b></label>
        <input type="text" id="id" placeholder="ID를 입력하세요"><br>
      </div>

      <div>
        <label for="pwd"><b>비밀번호 </b></label>
        <input type="password" id="pwd" placehoder="비밀번호를 입력하세요"><br>
      </div>

      <div>
        <label for="email"><b>이메일 </b></label>
        <input type="email" id="email"><br>
      </div>

      <div>
        <label for="gender"><b>성별 </b></label>
        <select name="" id="gender">
          <option value="m">남성</option>
          <option value="f">여성</option>
        </select>
      </div>
    </fieldset>

    <fieldset>
      <legend>
        <b>선택입력</b>
      </legend>

      <div>
        <label for="age"><b>나이</b></label>
        <input type="number" id="age" min="1" max="150"><br>
      </div>

      <div>
        <label for="ad"><b>주소</b></label>
        <input type="text" id="ad"><br>
      </div>

      <div>
        <label for="info"><b>자기소개</b></label>
        <textarea name="" id="" cols="30" rows="10" placeholder="자기소개를 입력하세요"></textarea>
      </div>
    </fieldset>
```

## 6. 크롬 개발자도구 

- 브라우저에서 HTML/CSS 요소를 디버깅 할 때 개발자 도구를 사용한다. 

- F12 or alt+comd+i

## 7. CSS

- 마크업 언어가 실제 표시되는 방법을 기술하는 언어		
- 레이아웃과 스타일을 정의할때 사용

선언예시) 

```
selector {
	property: value;
	}
**selector**: 선택자(규칙을 어디에 적용할지 결정)
**property**: 속성	
**value**: 값
```

- id (#) : id는 페이지에서 딱 한번만 선언 가능

- class (.) : class는 여러번 사용 가능

## 8. 외부 CSS사용

`<link rel = "stylesheet" href =  불러올 주소(상대경로)`

`link태그를 사용하여 외부CSS파일을 HTML문서에 연결`

## 9. external 방식
- 현업 개발시 소스 관리 구조의 경우 js, html(jsp), css 등의 소스는 각각 별도의 디렉토리로 분류 하여 관리 한다

- js또는 css를 html 단에서 작성시 같은 역할을 하는 로직을 불필요하게 중복작성하여 프로젝트 자체를 무겁게 할 우려가 있으며, 추후 유지보수 시에도 업무에 부하를 발생 시킨다.

### ex)
- selector-class.css

```
	.section {
	  color: #333;
	  margin-bottom: 40px;
	}
	
	p.section-title {
	  font-size: 18px;
	}
	
	p.section-content {
	  font-size: 13px;
	  line-height: 13px;
	  color: #999;
	}
```

- selector-class.html

```
<head>
  <link rel="stylesheet" href="css/selector-class.css">
</head>
<body>
  <!-- (.section>p.section-title+p.section-content)*2 -->
  <div class="section">
    <p class="section-title">Lorem ipsum dolor sit amet.</p>
    <p class="section-content">Lorem ipsum dolor sit amet.</p>
  </div>

  <div class="section">
    <p class="section-title">Lorem ipsum dolor sit amet.</p>
    <p class="section-content">Lorem ipsum dolor sit amet.</p>
  </div>
</body>
```

----

## 실습

- 포켓몬스터 표 그리기

```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Document</title>
  <style>
    html, body {
      font-size: 12px;
      color: #333;
    }
    table {
      border-collapse: collapse;
      text-align: center;
      border: 1px solid #999;
    }
    tr, th, td {
      border: 1px solid #999;
      padding: 4px 8px;
    }
  </style>
</head>
<body>
  <!--
  table>(thead>tr>td[colspan=9]{포켓몬스터의 전설의 포켓몬})
  +(tbody>(tr>td{지방}+td[colspan=2]{메인 전설의 포켓몬}+td[colspan=6]{그 외 전설의 포켓몬})
  +(tr>td{관동지방}+td[colspan=2]{뮤츠}+td[colspan=2]{프리져}+td[colspan=2]{썬더}+td[colspan=2]{파이어})
  +(tr>td{성도지방}+td{칠색조}+td{루기아}+td[colspan=2]{라이코}+td[colspan=2]{엔테이}+td[colspan=2]{스이쿤})
  +(tr>td[rowspan=2]{호연지방}+td{그란돈}+td{가이오가}+td[colspan=2]{레지락}+td[colspan=2]{레지아이스}+td[colspan=2]{레지스틸})
  +(tr>td[colspan=2]{레쿠쟈}+td[colspan=2]{라티아스}+td[colspan=2]{라티오스}+td[colspan=2]{테오키스})
  +(tr>td[rowspan=2]{칼로스지방}+td{제르네아스}+td{이벨타르}+td[colspan=3]+td[colspan=3])
  +(tr>td[colspan=2]{지가르데}+td[colspan=3]+td[colspan=3])
  +(tr>td[rowspan=3]{알로라지방}+td{코스모그}+td{코스모움}+td[colspan=3]{카푸꼬꼬꼭}+td[colspan=3]{카푸나비나})
  +(tr>td{솔가레오}+td{루나아라}+td[colspan=3]{카푸브루루}+td[colspan=3]{카푸느지느})
  +(tr>td[colspan=2]{네크로즈마}+td[colspan=3]{실버디}+td[colspan=3]{울트라비스트}))
  -->

  <table>
    <thead>
      <tr>
        <td colspan="9">포켓몬스터의 전설의 포켓몬</td>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>지방</td>
        <td colspan="2">메인 전설의 포켓몬</td>
        <td colspan="6">그 외 전설의 포켓몬</td>
      </tr>
      <tr>
        <td>관동지방</td>
        <td colspan="2">뮤츠</td>
        <td colspan="2">프리져</td>
        <td colspan="2">썬더</td>
        <td colspan="2">파이어</td>
      </tr>
      <tr>
        <td>성도지방</td>
        <td>칠색조</td>
        <td>루기아</td>
        <td colspan="2">라이코</td>
        <td colspan="2">엔테이</td>
        <td colspan="2">스이쿤</td>
      </tr>
      <tr>
        <td rowspan="2">호연지방</td>
        <td>그란돈</td>
        <td>가이오가</td>
        <td colspan="2">레지락</td>
        <td colspan="2">레지아이스</td>
        <td colspan="2">레지스틸</td>
      </tr>
      <tr>
        <td colspan="2">레쿠쟈</td>
        <td colspan="2">라티아스</td>
        <td colspan="2">라티오스</td>
        <td colspan="2">테오키스</td>
      </tr>
      <tr>
        <td rowspan="2">칼로스지방</td>
        <td>제르네아스</td>
        <td>이벨타르</td>
        <td colspan="3"></td>
        <td colspan="3"></td>
      </tr>
      <tr>
        <td colspan="2">지가르데</td>
        <td colspan="3"></td>
        <td colspan="3"></td>
      </tr>
      <tr>
        <td rowspan="3">알로라지방</td>
        <td>코스모그</td>
        <td>코스모움</td>
        <td colspan="3">카푸꼬꼬꼭</td>
        <td colspan="3">카푸나비나</td>
      </tr>
      <tr>
        <td>솔가레오</td>
        <td>루나아라</td>
        <td colspan="3">카푸브루루</td>
        <td colspan="3">카푸느지느</td>
      </tr>
      <tr>
        <td colspan="2">네크로즈마</td>
        <td colspan="3">실버디</td>
        <td colspan="3">울트라비스트</td>
      </tr>
    </tbody>
  </table>

</body>
</html>

```