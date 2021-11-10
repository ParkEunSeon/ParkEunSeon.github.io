---
layout: post
title:  "파이썬 반복문"
date:   2021-11-10 15:08:00 +0700
categories: [python]
---

# 6. 반복문

다음과 같이 문자열을 반복해서 출력해야 하는 경우를 생각해보자.

```python
print("=1=")
print("=2=")
print("=3=")
print("=4=")
print("=5=")
print("=6=")
print("=7=")
print("=8=")
print("=9=")
```

![Copy to clipboard](https://datascienceschool.net/_static/copy-button.svg)

```
=1=
=2=
=3=
=4=
=5=
=6=
=7=
=8=
=9=
```

### 6.1 기본 for문

#### 사용법

```
for 카운터변수 in range(반복횟수):
    반복해서 실행할 명령
for 카운터변수 in ("a", 1, "aaaa"): # 세번반복
    반복해서 실행할 명령
for 카운터변수 in (0,4): # 세번반복, 0이상 4미만
    반복해서 실행할 명령
for 카운터변수 in (0,10,2): # 다섯번반복(0,2,4,6,8) 0이상 10미만 2씩 증가
    반복해서 실행할 명령
```

```python
for i in range(0,3): #3개 : 0이상 3미만
  print("안녕하세요? for문을 공부중입니다.^^")

for i in range(0,10,2): # 5개(0이상 10미만 2씩 증가), 0,2,4,6,8
  print("안녕하세요? for문을 공부중입니다.^^")
```



**TIP**: 카운터변수를 이용해서 작업을 하지 않을 것이라면 _(언더바)를 사용하기도 함



```python
sum = 0
for i in range(1,11): # 1이상 11미만(10개)
  sum += i
print(f"1에서 10까지의 합계 : {sum}")
```

설명 : 1부터 10까지의 합계로 결과는 55가 보인다.

```python
for i in "Hello world!": # len(Hello world!)
  print(i)
```

설명 : Hello World! 의 갯수만큼 반복되어 한글자 한글자 출력이 된다.

**삼항연산자를 이용한 1부터 10까지의 합계**

```python
temp = [i for i in range(500, 1000) if i % 2 == 1]

for i in range(len(temp)):
  hap += temp[i]
print(f"500과 1000사이에 있는 홀수의 합계 : {hap}")
```



### 6.2 중첩 for문

**사용법**

```python
for 카운터변수 in range(반복횟수):
    for 카운터변수 in range(반복횟수):
        반복해서 실행할 명령
    print()
```

중첩 반복문을 사용할 때는 각각의 반복문에서 쓰고 있는 카운터 변수의 이름이 겹치지 않도록 주의해야 한다. 앞의 예에서는 바깥쪽 반복문의 카운터 변수는 i를 사용하였고 안쪽 반복문의 카운터 변수는 j를 사용하여 카운터 변수의 이름이 겹치지 않도록 하였다.

**실습**

```python
guguLine = ""
for i in range(2,10):
  guguLine = guguLine + (f"#  {i}단  #")
print(guguLine)
for i in range(1,10):
  guguLine = " "
  for j in range(2,10):
    guguLine = guguLine + str(f"{j} X {i} = {j*i}") 
  print(guguLine)
```

구구단을 만들 수 있다.

### 6.3 while문

**사용법**

```
while [조건문]:
      [수행부분]
```



- while 반복문은 [조건문]이 **참(True)인 경우 내부의 수행 부분을 진행**하고, [조건문]이 **거짓(False)인 경우 while문을 빠져나감**
- while문의 **조건문 끝에는 꼭 콜론 (:)** 을 붙여줘야함
- while 반복문의 **[수행부분]은 들여쓰기를 통해 구분**을 함
- while 보다 하나 들여쓰기 되어야 while문과 한묶음이라고 인식
- while 반복문은 중첩해서 사용이 가능

### 6.4 break문과 continue문

#### 6.4.1 break문

**사용법**

```
while [조건문]:
  [수행부분1]
  [수행부분2]
  ...
  특정조건:
    break
  [수행부분3]
  ...
```

이렇게 중간에 특정 조건을 만족하면 break가 걸리게 만들 수 있으며, break가 걸리면 바로 그자리에서 반복문을 나오게 됨. 아래 뭐가있든 위에 뭐가 있든 다 무시하고 반복문을 빠져나오게 됨

#### 6.4.2 continue문

```
while [조건문]:
  [수행부분1]
  [수행부분2]
  ...
  특정조건:
    continue
  [수행부분3]
  ...
```

while 반복문을 돌다가 특정 조건을 만족할때, 아래 코드는 무시하고 바로 반복문의 맨위로 올라가고 싶을때가 있을 수 있음.
즉 중간에서 바로 맨 처음으로 올라가는 기능을 한다.