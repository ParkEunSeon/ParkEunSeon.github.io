---
layout: post
title:  "사이킷런 분류 알고리즘_Decision Tree Algorithm"
date:   2021-11-22 19:00:00 +0700
categories: [merchinelearning]
---



#### 1. Decision Tree 개요

- 결정 트리 학습법은 데이터 마이닝에서 일반적으로 사용되는 방법론으로, 몇몇 입력 변수를 바탕으로 목표 변수의 값을 예측하는 모델을 생성하는 것을 목표로 한다. 
- 매우 쉽고 유연하게 적용될 수 있는 알고리즘이다.
- 사전 가공의 영향이 매우 적지만 예측성능을 향상시키기 위해 복잡한 규칙구조를 가져야하며 이로 인해 과적합이 발생해 오히려 예측 성능이 저하될 수 있다.
- 결정트리 장점
  - 쉽고 직관적임
  - 피처의 스케일링이나 정규화 등의 사전 가공 영향도가 크지 않음
- 결정트리 단점
  - 과적합으로 알고리즘 성능이 떨어짐
  - 이를 극복하기 위해 트리의 크기를 사전에 제한하는 튜닝 필요

#### 2. 정보 균일도 측정방법

- 정보이득(Information Gain) : 엔트로피라는 개념을 기반으로 함
- 엔트로피는 주어진 데이터 집합의 혼잡도를 의미하는데, 서로 다른 값이 섞여있으면 엔트로피가 높고, 같은 값이 섞여 있으면 엔트로피가 낮음
- 정보 이득 지수는 1에서 엔트로피 지수를 뺀 값임
- 즉 1-엔트로피 지수임
- 결정트리는 이 정보이득지수로 분할 기준을 정함(즉,정보이득이 높은 속성을 기준으로 분할함)

#### 3. 지니계수

- 0이 가장 평등하고 1로 갈수록 불평등 함

- 데이터가 다양한 값을 가질수록 평등하며 특정값으로 쏠릴 경우네는 불평등한 값이 됨

- 다양성이 낮을수록 균일도가 높다는 의미로서, 1로 갈수록 균일도가 높으므로 지니계수가 높은 속성을 기준으로 분할하는것

  |          | 같은 데이터(균일도) | 다른데이터(균일도) |
  | -------- | ------------------- | ------------------ |
  | 엔트로피 | 낮음                | 높음               |
  | 정보이득 | 높음                | 낮음               |
  | 지니계수 | 높음(낮음)          | 낮음(높음)         |

  **정보이득이 높은 속성 기준으로(같은 값이 많이 섞여있도록) 분할, 지니계수는 1로 갈수록 균일도가 높아지므로 지니계수가 높은쪽으로 분할함**

  - 기본적으로 지니 계수를 이용해 데이터 세트를 분할함
  - 정보이득이 높거나 지니계수가 낮은 조건을 찾아서 자시트리 노드에 분할함
  - 데이터가 모두 특정 분류에 속하게 되면 분할을 멈추고 분류를 결정함

#### 4. DecisionTree 사용법

```python
class sklearn.tree.DecisionTreeClassifier(*, criterion='gini', splitter='best', max_depth=None, min_samples_split=2, min_samples_leaf=1, min_weight_fraction_leaf=0.0, max_features=None, random_state=None, max_leaf_nodes=None, min_impurity_decrease=0.0, class_weight=None, ccp_alpha=0.0)
```

![image-20220109163421529](C:\Users\espark\AppData\Roaming\Typora\typora-user-images\image-20220109163421529.png)

#### 5. 결정트리 코드_붓꽃 데이터로드 및 그래프 그리기	

```python
import graphviz
from sklearn.tree import export_graphviz
from sklearn.tree import DecisionTreeClassifier
from sklearn.datasets import load_iris
from sklearn.model_selection import train_test_split
import warnings

# DecisionTree Classifier 생성
dt_clf = DecisionTreeClassifier(random_state=10)

# 붓꽃 데이터 로딩, 학습과 테스트 데이터 세트로 분리
iris_data = load_iris()
X_train, X_test, y_train, y_test = train_test_split(iris_data.data, iris_data.target,test_size=0.2, random_state=10)

#학습
dt_clf.fit(X_train, y_train)
```

```python
from sklearn.tree import export_graphviz

# export_graphviz() 호출 결과로 out_file로 지정된 tree.dot 파일을 생성
export_graphviz(dt_clf, out_file="tree.dot", class_names=iris_data.target_names, \
               feature_names = iris_data.feature_names, impurity=True, filled=True)

```

```python
with open("tree.dot") as f:
    dot_graph = f.read()
graphviz.Source(dot_graph)
```

![](C:\apps\ParkEunSeon.github.io\static\img\_posts\output_decision.svg)

- 결정 트리 알고리즘은 데이터에 있는 규칙을 학습을 통해 자동으로 찾아내서 트리 기반의 분류 규칙을 생성함

- 데이터의 어떤 기준을 바탕으로 규칙을 만들어야 가장 효율적인 분류가 될것인가가 알고리즘의 성능을 크게 좌우함

  



