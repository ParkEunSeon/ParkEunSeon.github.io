---
layout: post
title:  "파이썬 matplotlib"
date:   2021-11-12 19:00:00 +0700
categories: [python]
---



#### 1. Matplotlib란?

- 그래프나 그림을 그릴 수 있는 플라팅(plotting) 라이브러리
- 파이썬에서 제공하는 함수들을 사용하면 매트랩(Matlab)처럼 다룰 수 있으며 제공되는 기능과 문법이 비슷함
- pyplot 모듈을 사용하여 데이터를 시각적으로 표현할 수 있음
  - Matplot과 인터페이스 역할을 하는 것으로 상태 머신이라고 함

#### 2. Matplotlib 작성법

- 기본 그래프 그리기

  - **pyplot.plot()함수**에 하나의 숫자 리스트를 입력함으로써 아래와 같은 그래프가 그려짐

  - **plot()함수**는 리스트의 값들이 y 값들이라고 가정하고, x 값 [0, 1, 2, 3]을 자동으로 만들어냄

  - ***\*matplotlib.pyplot\**** 모듈의 ***\*show()\**** 함수는 그래프를 화면에 나타나도록 합니다.모듈의 **show()**함수는 그래프를 화면에 나타나도록 함

    ```python
    import matplotlib.pyplot as plt
    import numpy as np
    
    plt.plot([4,5,6,7]) #(0,4),(1,5),(2,6),(3,7)
    plt.show()
    ```

    ![](C:\apps\ParkEunSeon.github.io\static\img\output.png)

    ```python
    plt.plot([1, 2, 3, 4], [1, 4, 9, 16])  # 
    plt.show()
    ```

    ![](C:\apps\ParkEunSeon.github.io\static\img\matplotliboutput2.png)

    -  plot() 함수는 다양한 기능을 포함하고 있어서, 임의의 개수의 인자를 받을 수 있음

  - 스타일 지정하기

    ```python
    plt.plot([1, 2, 3, 4], [1, 4, 9, 16], 'bx-.')
    plt.axis([0, 6, 0, 20])  # x축 : 0~6, y축 : 0 ~20
    plt.show()
    ```

    ![](C:\apps\ParkEunSeon.github.io\static\img\output3.png)

  - 여러개의 그래프 그리기

    ```python
    # 200ms 간격으로 균일하게 샘플된 시간
    t = np.arange(0., 10., 0.2)
    
    # 빨간 대쉬, 파란 사각형, 녹색 삼각형
    plt.plot(t, t, 'r--')
    plt.plot(t, t**2, 'bs')
    plt.plot(t, t**3, 'g^')
    plt.show()
    ```

  - label 입력하기

    ```python
    x = ['Mon', 'Tue', 'Med', 'Thur', 'Fri', 'Sat', 'Sun']
    y1 = [13, 16, 15, 18, 16, 17, 16]
    y2 = [17, 14, 17, 16, 15, 15, 14]
    plt.plot(x,y1)
    plt.plot(x,y2)
    plt.xlabel('Daily')
    plt.ylabel('No. of Books Sold')
    ```

    ![](C:\apps\ParkEunSeon.github.io\static\img\output4.png)

  - 레전드(legend) 추가하기

    - legend()
    - legend(labels)
    - legend(handles, labels)

    https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.legend.html?highlight=pyplot%20legend#matplotlib.pyplot.legend

    ```python
    x = ['Mon', 'Tue', 'Med', 'Thur', 'Fri', 'Sat', 'Sun']
    y1 = [13, 16, 15, 18, 16, 17, 16]
    y2 = [17, 14, 17, 16, 15, 15, 14]
    plt.plot(x,y1, label='Sold')
    plt.plot(x,y2, label='On Shelves')
    plt.xlabel('Daily')
    plt.ylabel('No. of Books Sold')
    plt.legend(loc="upper left")
    ```

  - title 넣기

    - {'fontsize': rcParams['axes.titlesize'],

       'fontweight': rcParams['axes.titleweight'],

       'color': rcParams['axes.titlecolor'],

       'verticalalignment': 'baseline',

       'horizontalalignment': loc}

      ```python
      x = ['Mon', 'Tue', 'Med', 'Thur', 'Fri', 'Sat', 'Sun']
      y1 = [13, 16, 15, 18, 16, 17, 16]
      y2 = [17, 14, 17, 16, 15, 15, 14]
      plt.plot(x,y1, label='Sold')
      plt.plot(x,y2, label='On Shelves')
      plt.xlabel('Daily')
      plt.ylabel('No. of Books Sold')
      plt.legend(loc="upper left")
      plt.title('Le Petit Prince : Sold & Left')
      plt.show()
      ```

  - savefing

    - pdf로 그래프를 다운로드함

    - savefig(fname, dpi=None, facecolor='w', edgecolor='w',orientation='portrait', papertype=None, format=None,transparent=False, bbox_inches=None, pad_inches=0.1,frameon=None, metadata=None)

      ```python
      x = np.linspace(0, 10, 20)
      y1 = x**2.0
      y2 = x**1.5
      plt.plot(x,y1,"bo-",linewidth=2,markersize=12, label="First")
      plt.plot(x,y2,"gs-",linewidth=2,markersize=12, label="Second")
      plt.xlabel("X")
      plt.ylabel("Y")
      plt.axis([-0.5, 10.5, -5, 105])
      plt.legend(loc="upper left")
      plt.savefig("mplot.pdf")
      ```

      ![](C:\apps\ParkEunSeon.github.io\static\img\output5.png)

  - histogram

    - matplotlib.pyplot.hist(x, bins=None, range=None, density=False, weights=None, cumulative=False, bottom=None, histtype='bar', align='mid', orientation='vertical', rwidth=None, log=False, color=None, label=None, stacked=False, *, data=None, **kwargs)

      ```python
      weight = [68, 81, 64, 56, 78, 74, 61, 77, 66, 68, 59, 71,
                80, 59, 67, 81, 69, 73, 69, 74, 70, 65]
      plt.hist(weight)
      plt.show()
      ```

      ![](C:\apps\ParkEunSeon.github.io\static\img\output6.png)

  

  

