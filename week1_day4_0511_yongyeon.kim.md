# #### 1주 4일차

- 수업자료 : [HTML,CSS,Sass.pdf](https://github.com/Fastcampus-WPS-5th/HTML-CSS/blob/master/HTML%2CCSS%2CSass.pdf)

---------

## 1. float
- float : 띄우다
- float를 사용하면 해당 요소를 문서의 흐름과 별개로 취급하여, 왼쪽이나 오른쪽으로 띄워줄 수 있습니다.
```즉, block 요소의 경우 inline 속성으로변경 된다.``` 

### 1) right
> inline 속성으로 변경 되며 다음 요소의 위에 얹어지며, 오른쪽으로 정렬 된다.

### 2) left
> inline 속성으로 변경 되며 다음 요소의 위에 얹어지며, 왼쪽으로 정렬 된다.

### 3) clear
> float 속성을 제거 하며, block 요소로 변경 시킨다.

- clear: both; : left, right 모두 제거
- clear: left; : left 제거
- clear: right; : right 제거

#### 4) float 레이아웃
> 레이아웃 구성을 위해 자식 요소를 모두 float 속성이 주어질 경우 자식요소들의 레이아웃은 구성 되지만 부모요소에 소속된 데이터가 없기 때문에 float요소 들의 배경 레이아웃이 깨지게 된다.

> 부모요소에 가상선택자를 사용하여 별도 요소를 생성해주면 배경(부모)레이아웃이 유지 된다.

```
.float-frame {  	width: 300px;
	background-color: #eee;
	...}

★ [클래스명]::after를 사용 하면 [클래스명] 클래스의 css가
   바인딩 된 직후 실행 하게 된다. 반대는 ::before
.float-frame::after. {
// .float-frame css 바인딩 후 임의의 요소 생성	content: ““; // 임의의 요소 내용은 없음	display: block; // 화면에서 없앰	height: 0;
	clear: both;
	// 모든 float 속성을 제거하여 블록요소로 생성함}

.float-unit {  	width: 50px;
	background: #333;
	color: #fff;
	...}
<div class="float-frame">  <div class="float-unit">A</div>
<div class="float-unit">B</div>
<div class="float-unit">C</div>
<div class="float-unit">D</div></div>

```

## 2. position
- static : 기본값

- relative : static과 같은 순서로 배치되지만, top, right, bottom, left속성을 이용해 위치를 지정 가능

- fixed : 브라우저 창을 기준으로 배치

- absolute : 자신과 가장 가까운  ‘position’이 ‘static’이 아닌 부모를 기준으로 배치 (없을 경우 본문(body)기준)

## 3. Semantic Tag
- header 머릿말, 페이지 맨 위나 왼쪽에 삽입 - nav 내비게이션 링크, 가로/세로 형태의 메뉴에 사용 - section 콘텐츠 영역 - article 콘텐츠 내용 - aside 본문 이외의 내용 (메인 내용에 영향을 주지 않는 링크 등) - footer 꼬릿말, 제작자 및 저작권 정보 표시

## 4. Sass
- CSS전처리기 (Pre-processor) ```
Sass와 같은 ‘CSS확장 언어’의 파일을 웹 브라우저에서
해석할 수 있는 css파일로 만들어주는 처리기

개발 생산성을 위해 반복되는 구문들을 생략하고 간략하게 개발하도록
도와주는 기능이며, 별도 컴파일을 통해 css 파일을 생성 한다.
```

★ atom의 경우 sass-autocompile 패키지를 통해 저장시 자동으로 컴파일을 진행 할 수 있어 유용하다.

### Sass 기본구조

```
div.container {
   padding: 15px;
   margin: 0;      > p#main-title {
       font-size: 16px;
       font-weight: bold;       }
        > .fixed {
       position: fixed;
       bottom: 10px;
       right: 10px;     }
}
```

>Sass의 출력 스타일로는 expanded, nested, compact, compressed 방식 등이 있으며, compressed 방식을 많이 사용한다.

>compressed : css 데이터를 공백등을 제거하여 압축한다.


## 5. Sass 문법
### 1. 중첩
```
.container {
  width: 1100px;
  margin: 0 auto;
  
  > #page { <= CSS에서의 .container > #page를 뜻한다      width: 800px;       border: 1px solid #eee;
      padding: 10px; 
    
      p.section-title { <= CSS에서의 .container > #page p.section-title을 뜻한다
        font-size: 20px;
        text-align: center;
      }
    
      p.section-content {
        font-size: 12px;
        color: #999;
      }     }}
```

### 2. 부모 참조 선택자 (&)
```
   //& 가 앞에 쓰일 경우 자신의 부모를 지칭 한다.
   &:hover {  
      color: red;   }  
   //& 앞에 선택자가 있을 경우, 해당 선택자 다음에 현재위치에서의 부모 선택자를 참조한다.   .link-container & {
      font-size: 30px;
   }
   
```

### 3. 중첩 속성
```
   .container {
     margin-left: auto;
     margin-right: auto;
   }

```

   를

```
   .container {
     margin: {
       left: auto;
       right: auto;
     }
   }
```

와 같이 생략하여 사용 할 수 있다.

### 4. 상속 (@extend)
```
   .btn {       background-color: #cdcdcd;
     font-weight: bold;       color: white;       padding: 5px 20px;     }
       .btn-ok {       @extend .btn;
     // 상속을 사용하면 상속 대상이 가지고 있는 속성은
     // 모두 사용하며 일부만 바꿔 요소에 활용 할 수 있다.     background-color: #d9edf7;
   } 
```

### 5. 대체 선택자 (%)
```
   %btn { // 선언하여 소스는 활용 하지만 실제 css 파일 컴파일 시에는 표시 되지 않는다.
     font-weight: bold;
   }
   
   .btn-ok {
     @extend %btn;
     background-color: white;
   }
```


### 6. 변수 ($)
```
   $padding: 10px;
   $bg-color: #ececec;
   $title-font-weight: bold;  
   // 변수의 선언은 $로 한다.    div.container {       background-color: $bg-color;
     padding: $padding;
     // 변수를 사용하여 자주 사용하는 값을 저장하여 사용 한다.     margin: 0;
   }
```

### 7. Sass파일 호출
- Sass 파일을 호출(import) 할 경우 문서 상단에 아래와 같이 입력하며, 확장자를 제외한 파일명만 입력 한다.

```
   @import 'variables';
```