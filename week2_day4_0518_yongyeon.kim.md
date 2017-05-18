## while문 (반복문)

- ## 컴프리헨션 (Comprehension)

  함축 또는 내포

  iterable한 객체로부터 파이썬의 자료구조를 만드는 방법. 가독성과 사용성에서 이득을 얻을 수 있을 경우 항상 사용해준다.

  #### 리스트 컴프리헨션

```
  [표현식 for 항목 in iterable객체]
```

  [1,2,3,4,5]를 만드는 방법

  ##### range와 for문을 사용할 경우

```
  numbers = []
  for item in range(1, 6):
     numbers.append(item)

  numbers
  [1, 2, 3, 4, 5]
```

  ##### 리스트 컴프리헨션을 사용할 경우

```
  [item for item in range(1, 6)]
  [1, 2, 3, 4, 5]
```

  만약 각 item에 2배의 값을 할당하고 싶다면?

  만약 1~5중 짝수만 해당하는 리스트를 만들고 싶다면?

  ##### 리스트 컴프리헨션의 중첩

```
  for color in colors:
    for fruit in fruits:
```

```
  [(color, fruit) for color in colors for fruit in fruits]
```

  #### 셋 컴프리헨션

```
  {표현식 for 표현식 in iterable객체}
```

  #### 제네레이터 컴프리헨션

```
  (표현식 for 표현식 in interable객체)
```

  괄호로 되어있지만 튜플을 생성하지 않는다. (튜플은 컴프리헨션이 없다)

  제너레이터 객체는 순회 가능하며, 리스트 형태로 만들 수 있다.

---

# 함수

반복적인 작업을 하는 코드를 재사용이 가능하게 정의해 놓은 것.

```
def 함수명(매개변수[parameters]):
	동작
```

#### 함수의 정의, 실행

```
# 실행 시 'call func'를 print하는 함수 정의
def func():
   print('call func')
 

# 함수 자체는 function객체를 참조하는 변수
func
<function func at 0x10dabf378>

# 함수를 실행시키기 위해 () 사용
```
func()
call func
```

#### 리턴값이 있는 함수 정의

```
 def return_true():
   return True
 
return_true()
True


함수의 결과로 Bool값을 갖는 데이터를 리턴하여 if문이나 while문의 조건으로 사용 가능하다.

#### 매개변수를 사용하는 함수 정의

```
 def print_arguments(something):
   print(something)
 
 print_arguments('ABC')
ABC
```

#### 매개변수(parameter)와 인자(argument)의 차이

함수 내부에서 함수에게 전달되어 온 변수는 매개변수라 부르며, 함수를 호출할 때 전달하는 변수는 인자로 부른다.

```
# 함수 정의때는 매개변수
def func(매개변수1, 매개변수2):
```
  
# 함수 호출시에는 인자
```
func(인자1, 인자2)
```

#### 리턴값이 없을 경우

함수에서 리턴해 주는 값이 없을 경우, 아무것도 없다는 뜻을 가진 `None`객체를 얻는다.

#### 위치 인자(Positional arguments)

매개변수의 순서대로 인자를 전달하여 사용하는 경우

```
def student(name, age, gender):
   return {'name': name, 'age': age, 'gender': gender}
 
student('hanyeong.lee', 30, 'male')
{'name': 'hanyeong.lee', 'age': 30, 'gender': 'male'}
```

#### 키워드 인자(Keyword arguments)

매개변수의 이름을 지정하여 인자로 전달하여 사용하는 경우

```
 student(age=30, name='hanyeong.lee', gender='male')
{'name': 'hanyeong.lee', 'age': 30, 'gender': 'male'}
```

**위치인자와 키워드인자를 동시에 쓴다면, 위치인자가 먼저 와야 한다**

#### 기본 매개변수값 지정

인자가 제공되지 않을 경우, 기본 매개변수로 사용할 값을 지정할 수 있다.

```
def student(name, age, gender, cls='WPS'):
   return {'name': name, 'age': age, 'gender': gender, 'class': cls}
 
student('hanyeong.lee', 30, 'male')
{'name': 'hanyeong.lee', 'age': 30, 'gender': 'male', 'class': 'WPS'}
```

#### 기본 매개변수값의 정의 시점

기본 매개변수값은 함수가 실행될 때 마다 계산되지 않고, 함수가 정의되는 시점에 계산되어 계속해서 사용된다.

```
def return_list(value, result=[]):
   result.append(value)
   return result
 
return_list('apple')
['apple']
return_list('banana')
['apple', 'banana']
```

함수가 실행되는 시점에 기본 매개변수값을 계산하기 위해, 아래와 같이 바꿔준다.

```
 def return_list(value, result=None):
   if result is None:
     result = []
   result.append(value)
   return result
 
 return_list('apple')
['apple']
 return_list('banana')
['banana']
```

#### 위치인자 묶음

함수에 위치인자로 주어진 변수들의 묶음은 `*매개변수명`으로 사용할 수 있다.  
관용적으로 `*args`를 사용한다.

```
def print_args(*args):
  print(args)
```

#### 키워드인자 묶음

함수에 키워드인자로 주어진 변수들의 묶음은 `**매개변수명`으로 사용할 수 있다.
관용적으로 `**kwargs`를 사용한다.

```
def print_kwargs(**kwargs):
  print(kwargs)
```

#### docstring

함수를 정의한 문서 역할을 한다.  
함수 정의 후, 몸체의 시작부분에 문자열로 작성하며, 여러줄로도 작성 가능하다.

```
 def print_args(*args):
   'Print positional arguments'
   print(args)
 
 help(print_args)
```

#### 함수를 인자로 전달

파이썬에서는 함수 역시 다른 객체와 동등하게 취급되므로, 함수에서 인자로 함수를 전달, 실행, 리턴하는 형태로 프로그래밍이 가능하다.

- 'call func'를 출력하는 함수를 정의하고, 함수를 인자로 받아 실행하는 함수를 정의하여 첫 번째에 정의한 함수를 인자로 전달해 실행해보자.

#### 내부 함수

함수 안에서 또 다른 함수를 정의해 사용할 수 있다.

- 문자열 인자를 하나 전달받는 함수를 만들고, 해당 함수 내부에 전달받은 문자열을 대문자화해서 리턴해주는 내부 함수를 구현한다.  
  문자열을 전달받는 함수는 내부함수를 실행한 결과를 리턴하도록 한다.

#### 스코프(영역)

파이썬에서는 코드 작성 시, 각 함수마다 독립적인 스코프(영역)을 가진다.  
메인 프로그램(현재 동작하는 프로그램의 최상위 위치)의 영역은 전역 영역(Global Scope)라고 하며, 전역 스코프 내부에서 독립적인 영역을 갖고 있는 경우에는 지역 영역(Local Scope)라고 부른다.

아래 코드의 경우, `show_global_champion`함수 내부의 영역은 별개의 로컬 스코프를 가지며, `champion`변수는 전역 영역의 것을 가져와 출력하는것을 볼 수 있다.

```
champion = 'Lux'

def show_global_champion():
    print('show_global_champion : {}'.format(champion))

show_global_champion()
print('print champion : {}'.format(champion))
```

위 코드를 아래와 같이 변경 후, 실행 해 본다.

```
champion = 'Lux'

def show_global_champion():
    print('show_global_champion : {}'.format(champion))

def change_global_champion():
    print('before change_global_champion : {}'.format(champion))
    champion = 'Ahri'
    print('after change_global_champion : {}'.format(champion))

show_global_champion()
change_global_champion()
```

`change_global_champion`함수에서 오류가 발생한다.

첫 번째 코드에서는 `champion`변수가 함수의 로컬 스코프에 존재하지 않기 때문에 글로블 스코프에서 해당 변수를 찾아 출력하였으나, 이번 코드에서는 내부에 또다른 `champion`변수가 존재하기 때문에 할당하기 전인 변수를 사용한 것으로 판단하여 프로그램에서 오류를 발생시킨다.

이름이 같은 두 변수가 다른 객체임을 내장함수 `id`를 사용해 확인해보자.

또한, 각 영역에 해당하는 데이터들은 `locals()`함수를 사용해 확인 할 수 있으며, 전역 영역의 데이터들은 `globals()`함수를 사용한다.





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
mv ./.zshrc /Users/yykim/Dropbox/mac-settings/
```

- 심볼릭 링크 생성
   : ln -s 원본경로 링크파일경로

```
ln -s /Users/yykim/Dropbox/mac-settings/.zshrc ./.zshrc
```
