---
layout: post
title:  "파이썬 기본 문법 정리1"
date:   2021-11-10 22:08:00 +0700
categories: [python]
---



## 1. 변수와 데이터형

### **1.1 print()함수를 사용한 다양한 출력** 

​	 

|    서식    |       값의 예        |            설명             |
| :--------: | :------------------: | :-------------------------: |
| %d, %x, %o |    10, 100, 1234     | 정수(10진수, 16진수, 8진수) |
|     %f     |    0.5, 1.0, 3.14    |   실수(소수점이 붙은 수)    |
|     %c     |       "b","한"       |           한글자            |
|     %s     | "안녕","abcdefg","a" |    두 글자 이상인 문자열    |

 

### 1.2 변수의 선언과 사용

#### 1.2.1 변수선언

다음 예와 같은 a, b, c를 변수라고 한다.

```python
>>> a = 1
>>> b = "python"
>>> c = [1,2,3]
```

변수를 만들 때는 위 예처럼 =(assignment) 기호를 사용한다.

다른 프로그래밍 언어인 C나 JAVA에서는 변수를 만들 때 자료형을 직접 지정해야 한다. 하지만 파이썬은 변수에 저장된 값을 스스로 판단하여 자료형을 지정하기 때문에 더 편리하다.

```
변수 이름 = 변수에 저장할 값
```



#### 1.2.2 변수 생성법

```python
>>> a, b = ('python', 'life')
```

위 예문처럼 튜플로 a, b에 값을 대입할 수 있다. 이 방법은 다음 예문과 완전히 동일하다.

```python
>>> (a, b) = 'python', 'life'
```

튜플 부분에서도 언급했지만 튜플은 괄호를 생략해도 된다.

다음처럼 리스트로 변수를 만들 수도 있다.

```python
>>> [a,b] = ['python', 'life']
```

또한 여러 개의 변수에 같은 값을 대입할 수도 있다.

```python
>>> a = b = 'python'
```

파이썬에서는 위 방법을 사용하여 두 변수의 값을 아주 간단히 바꿀 수 있다.

```python
>>> a = 3
>>> b = 5
>>> a, b = b, a
>>> a
5
>>> b
3
```

처음에 a에 값 3, b에는 값 5가 대입되어 있었지만 a, b = b, a 문장을 수행한 후에는 그 값이 서로 바뀌었음을 확인할 수 있다.파이썬은 스크립트 언어로 컴파일 과정없이 인터프리터에 의해 실행 결과를 바로 확인하고 수정하며 코드를 작성할 수 있습니다.

 

### 1.3 데이터 표현 단위와 진수 변환

#### 1.3.1 코딩

```python
sel = int(input("진수 타입을 결정하시오(16,10,8,2진수)"))

num = input('값 입력: ')

if sel == 16:
    num10 = int(num, 16) # 값을 16진수의 정수(int, integer)로 바꾼다  
    print(int(num10)) 
    print(hex(num10)) # 16진수로 표현  
    print(bin(num10)) # 2진수로 표현  

if sel == 2: 
    num2 = int(num, 2)
    print(num2) 
    print(hex(num2)) 
    print(bin(num2))


```

설명 : 진수타입을 결정하는 값과 해당 진수로 변환하고자 하는 숫자를 각각 입력받는다. 진수타입이 16일 경우 해당 값을 16진수와 2진수로 표현한다.



#### 1.4 문자열

```python
print('"나는"사람이다.')
print('''
"나는"
사람이다.''')
```

문자열을 ''' ''' 로 감싸서 출력하면 엔터키, 쌍따옴표가 적용되어 출력이 됨



### 2. 연산자

#### 2.1 산술연산자

- **산술연산자 종류**

> **+ : 더하기**
> **- : 빼기**
> *** : 곱하기**
> **/ : 나누기**
> **// : 정수 몫**
> **% : 나머지**
>
> ** **: 누승**

#### 2.2 관계연산자

- **관계연산자 종류**

> **> : 크다**
> **>= : 크거나 같다**
> **< : 작다**
> **<= : 작거나 같다**
> **== : 같다**
> **!= : 같지 않다**



#### 기본 연산

```python
# 관계 연산자(Relational Operators)
# 대소 관계와 상등관계를 나타내는 연산자로 결과값이 논리값입니다.
a = 10
b = 3

print("10 == 3 =>", a == b)
print("10 != 3 =>", a != b)
print("10 > 3 =>", a > b)
print("10 >= 3 =>", a >= b)
print("10 < 3 =>", a < b)
print("10 <= 3 =>", a <= b)
print()
```

> 실행 결과

```python
10 == 3 => False
10 != 3 => True
10 > 3 => True
10 >= 3 => True
10 < 3 => False
10 <= 3 => False
```

#### 2.3 논리연산자

- **a and b**

```python
>>> True and True
True
>>> True and False
False
>>> False and True
False
>>> False and False
False
>>> 
```

and는 두 값이 모두 True라야 True입니다. 하나라도 False이면 False가 나옵니다.

이번에는 or입니다.

- **a or b**

```python
>>> True or True
True
>>> True or False
True
>>> False or True
True
>>> False or False
False
```

or는 두 값 중 하나라도 True이면 True입니다. 두 값이 모두 False라야 False가 되죠.

마지막으로 not입니다.

- **not x**

```python
>>> not True
False
>>> not False
True
```

not은 논릿값을 뒤집습니다. 그래서 not True는 False가 되고, not False는 True가 됩니다.

여기서 and, or, not 논리 연산자가 식 하나에 들어있으면 not, and, or 순으로 판단합니다.

```python
>>> not True and False or not False
True
```

식이 꼬여 있어서 상당히 헷갈리죠? 가장 먼저 not True와 not False를 판단하여 False and False or True가 됩니다.

그다음에 False and False를 판단하여 False가 나와서 False or True가 되므로 최종 결과는 True가 됩니다.

```python
not True and False or not False
False and False or True
False or True
True
```

이 식을 괄호로 표현하면 다음과 같은 모양이 됩니다.

```python
>>> ((not True) and False) or (not False)
True
```

순서가 헷갈릴 때는 괄호로 판단 순서를 명확히 나타내 주는 것이 좋습니다.



#### 2.4 연산 우선순위

| 순위 | 연산자                                                       | 설명                                              |
| :--- | :----------------------------------------------------------- | :------------------------------------------------ |
| 1    | (), {}, []                                                   | Tuple, Set, List, Dictionary                      |
| 2    | collection[index] collection[index1, index2] function(aguments ...) object.attribute | 컬렉션의 첨자 슬라이싱 함수의 인수 객체의 속성 등 |
| 3    | **                                                           | 거듭제곱                                          |
| 4    | + , - , ~                                                    | 단항 연산자(부호, bitwise not)                    |
| 5    | * / // %                                                     | 곱하기, 나누기, 정수 몫, 나머지                   |
| 6    | + -                                                          | 더하기, 빼기                                      |
| 7    | << >>                                                        | 시프트 연산                                       |
| 8    | &                                                            | bitwise and                                       |
| 9    | ^                                                            | bitwise xor                                       |
| 10   |                                                              |                                                   |
| 11   | in, not in is, is not <, <=, >, >=, ==, !=                   | 멤버 연산자 아이디 연산자 관계 연산자             |
| 12   | not                                                          | 논리 not                                          |
| 13   | and                                                          | 논리 and                                          |
| 14   | or                                                           | 논리 or                                           |
| 15   | if else                                                      | 삼항 연산자                                       |
| 16   | lambda                                                       | 람다 표현식                                       |

