---
layout: post
title:  "파이썬 pandas dataframe"
date:   2021-11-15 19:00:00 +0700
categories: [python]
---



#### 1. Pandas의 데이터 형식

- 시리즈(Series)
  - 1차원 배열

- 데이터프레임(DataFrame)
  - 2차원 배열


#### 2. 데이터프레임(DataFrame)

- 데이터프레임이란

  - 2차원 배열로 행과 열로 구성되어 있음

  - 열(column)에 대한 각각의 이름을 부여할 수 있음

    ```python
    data = {'age':[23,43,12,45],
    		'name':['민준','현우','서연','동현'],
    		'height':[175, 180, 165, 172]}
    x = pd.DataFrame(data,columns = ['name','age','height'])
    ```

    

- 데이터프레임 생성법

  ```python
  df = pd.DataFrame([data, index, columns, dtype, copy ])
  ```

  

- 데이터 프레임 기본 함수(https://pandas.pydata.org/docs/reference/frame.html 참조)

  | [`DataFrame.index`](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.index.html#pandas.DataFrame.index) | DataFrame의 인덱스 반환                              |
  | ------------------------------------------------------------ | ---------------------------------------------------- |
  | [`DataFrame.columns`](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.columns.html#pandas.DataFrame.columns) | DataFrame의 열 레이블 반환                           |
  | [`DataFrame.dtypes`](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.dtypes.html#pandas.DataFrame.dtypes) | DataFrame의 dtypes를 반환                            |
  | [`DataFrame.info`](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.info.html#pandas.DataFrame.info)([verbose, buf, max_cols, ...]) | DataFrame의 간결한 요약정보 반환                     |
  | [`DataFrame.select_dtypes`](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.select_dtypes.html#pandas.DataFrame.select_dtypes) | 열 dtypes를 기반으로 DataFrame 열의 하위 집합을 반환 |
  | [`DataFrame.values`](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.values.html#pandas.DataFrame.values) | DataFrame의 Numpy 표현을 반환                        |
  | [`DataFrame.axes`](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.axes.html#pandas.DataFrame.axes) | DataFrame의 축을 나타내는 목록을 반환                |
  | [`DataFrame.ndim`](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.ndim.html#pandas.DataFrame.ndim) | 축/배열 차원의 수를 나타내는 int를 반환              |
  | [`DataFrame.size`](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.size.html#pandas.DataFrame.size) | 이 객체의 요소 수를 나타내는 int를 반환              |
  | [`DataFrame.shape`](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.shape.html#pandas.DataFrame.shape) | DataFrame의 차원을 나타내는 튜플을 반환              |
  | [`DataFrame.memory_usage`](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.memory_usage.html#pandas.DataFrame.memory_usage) | 각 열의 메모리 사용량을 바이트 단위로 반환           |
  | [`DataFrame.empty`](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.empty.html#pandas.DataFrame.empty) | DataFrame이 비어 있는지 여부를 반환                  |
  | [`DataFrame.set_flags`](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.set_flags.html#pandas.DataFrame.set_flags) | 업데이트된 플래그가 있는 새 객체를 반환              |



