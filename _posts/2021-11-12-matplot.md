---
layout: post
title:  "파이썬 추상메서드, 멀티스레드"
date:   2021-11-12 18:54:00 +0700
categories: [python]
---



#### 1. 객체지향 프로그래밍의 심화 내용

- 클래스의 특별한 메서드

  - _ _ del _ _ () 메서드(소멸자) : 생성자와 반대로 인스턴스 삭제할 때 자동 호출
  - _ _ repr _ _ () 메서드: 인스턴스를 print() 문으로 출력할 때 실행
  - _ _ add _ _ () 메서드 : 인스턴스 사이에 덧셈 작업이 일어날 때 실행되는 메서드, 인스턴스 사이의 덧셈 작업 가능
  - 비교메서드(_ _ lt/le/gt/ge/eq/ne _ _ ()) : 인스턴스 사이의 비교연산자를 사용할 때 호출 

- 추상메서드

  - 서브클래스에서 메서드를 오버라이딩 : 슈퍼클래스에서는 빈 껍질의 메서드만 만들어 놓고 내용은 pass로 채움

    ```python
    # 클래스 선언 부분
    class SuperClass:
    	def method(self):
    		pass
    # superclass를 상속받음
    class SubClass1(SuperClass):
    	def method(self):
    		print('SubClass1에서 method()를 오버라이딩 함')
    # superclass를 상속받음	
    class SubClass2(SuperClass):
    	pass
    
    # 메인 코드 부분
    sub1 = SubClass1()
    sub2 = SubClass2()
    # 오버라이딩한 method()호출
    sub1.method()
    sub2.method()
    ```

  

- 멀티 스레드

  - 프로그램 하나에서 여러 개를 동시에 처리할 수 있도록 제공하는 기능


    ![img](https://blog.kakaocdn.net/dn/EX7zQ/btq1IqEQAKm/rmj8CxAvnltt6IFXYE8rI1/img.png)

     

  - 멀티스레드의 예시 : 자동차 세대가 경주하는 코드

    ```python
    import time
    
    #클래스 선언부분
    class RacingCar :
    	carName = ''
    	def __init__(self, name):
    		self.carName = name
    	
    	def runCar(self):
    		for _ in range(0,3):
    			carStr = self.carName + "~~달립니다.\n"
    			print(carStr, end='')
    			time.sleep(0.1) # 빠른 출력 방지
    			
    ```

    ```python
    import threading
    # 메인코드부분
    car1 = RacingCar('@자동차1')
    car2 = RacingCar('#자동차2')
    car3 = RacingCar('$자동차3')
    
    # 사용 스레드 생성
    th1 = threading.Thread(target=car1.runCar)
    th2 = threading.Thread(target=car2.runCar)
    th3 = threading.Thread(target=car3.runCar)
    
    # 스레드 start
    th1.start()
    th2.start()
    th3.start()
    ```

-  멀티 프로세싱

  - 동시에 CPU를 여러 개 사용함으로써 복잡하고 시간이 오래 걸리는 작업을 병렬 처리하여 단 시간안에 끝낼 수 있게 함

    ```python
    import multiprocessing
    
    # 메인코드부분
    if __name__ == "__main__":
    	car1 = RacingCar('@자동차1')
    	car2 = RacingCar('#자동차2')
    	car3 = RacingCar('$자동차3')
    	
    	# 사용 프로세스 생성
        mp1 = multiprocessing.Process(target=car1.runCar)
        mp2 = multiprocessing.Process(target=car2.runCar)
        mp3 = multiprocessing.Process(target=car3.runCar)
    
        # 프로세스 start
        mp1.start()
        mp2.start()
        mp3.start()
        
        # 프로세스 end
        mp1.join()
        mp2.join()
        mp3.join()
    ```

    

