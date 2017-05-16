# #### 1주 1일차

- 수업자료 : [emmet](https://docs.emmet.io)

---------
## 1. Elements
생성할 태그 엘레멘트를 입력 한 후 `tab`키

```
div [tab]

<div></div>
```

## 2. Nesting operators

### 1. Child >

하위에 태그 생성

```
div>ul>li [tab]


<div>
  <ul>
    <li></li>
  </ul>
</div>
```

### 2. Sibling +

같은 레벨에 각각 태그 생성

```
div+p+bq [tab]


<div></div>
<p></p>
<blockquote></blockquote>
```

### 3. Climb-up ^

^의 갯수만큼 아래 라인에 태그 생성

```
div+div>p>span+em [tab]


<div></div>
<div>
    <p><span></span><em></em></p>
</div>
div+div>p>span+em^bq [tab]


<div></div>
<div>
    <p><span></span><em></em></p>
    <blockquote></blockquote>
</div>
div+div>p>span+em^^^bq [tab]


<div></div>
<div>
    <p><span></span><em></em></p>
</div>
<blockquote></blockquote>
```

### 4. Multiplication *

지정한 갯수만큼 태그 생성

```
ul>li*5 [tab]

<ul>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
</ul>
ul>li{항목}*5 [tab]

<ul>
    <li>항목</li>
    <li>항목</li>
    <li>항목</li>
    <li>항목</li>
    <li>항목</li>
</ul>
```

### 5. Grouping ()

복잡하게 사용 시, 그룹핑 가능

```
div>(header>ul>li*2>a)+footer>p [tab]


<div>
    <header>
        <ul>
            <li><a href=""></a></li>
            <li><a href=""></a></li>
        </ul>
    </header>
    <footer>
        <p></p>
    </footer>
</div>
(div>dl>(dt+dd)*3)+footer>p [tab]

<div>
    <dl>
        <dt></dt>
        <dd></dd>
        <dt></dt>
        <dd></dd>
        <dt></dt>
        <dd></dd>
    </dl>
</div>
<footer>
    <p></p>
</footer>
Attribute operators
```

####1. ID and Class

```
div#header+div.page+div#footer.class1.class2.class3 [tab]
```

```
<div id="header"></div>
<div class="page"></div>
<div id="footer" class="class1 class2 class3"></div>
```

####2. Custom attributes

```
td[title="Hello world!" colspan=3] [tab]
```

```
<td title="Hello world!" colspan="3"></td>
```

#### 3. Item numbering $

```
ul>li.item$*5 [tab]

```

```
<ul>
    <li class="item1"></li>
    <li class="item2"></li>
    <li class="item3"></li>
    <li class="item4"></li>
    <li class="item5"></li>
</ul>
ul>li.item$$$*5
```

```
<ul>
    <li class="item001"></li>
    <li class="item002"></li>
    <li class="item003"></li>
    <li class="item004"></li>
    <li class="item005"></li>
</ul>
```

#### 4. Changing numbering base and direction

```
ul>li.item$@-*5 [tab]
```

```
<ul>
    <li class="item5"></li>
    <li class="item4"></li>
    <li class="item3"></li>
    <li class="item2"></li>
    <li class="item1"></li>
</ul>
ul>li.item$@3*5 [tab]

```

```
<ul>
    <li class="item3"></li>
    <li class="item4"></li>
    <li class="item5"></li>
    <li class="item6"></li>
    <li class="item7"></li>
</ul>
ul>li.item$@-3*5 [tab]
```
```
<ul>
    <li class="item7"></li>
    <li class="item6"></li>
    <li class="item5"></li>
    <li class="item4"></li>
    <li class="item3"></li>
</ul>
```