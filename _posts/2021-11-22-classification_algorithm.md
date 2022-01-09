---
layout: post
title:  "사이킷런 분류 알고리즘"
date:   2021-11-22 18:00:00 +0700
categories: [merchinelearning]
---



#### 1. 분류(Classification) 알고리즘

- 분류(classification)는 학습데이터로 주어진 데이터의 피처와 레이블값(결정값, 클래스 값)을 머신러닝 알고리즘으로 학습해 모델을 생성하고, 이렇게 생성된 모델에 새로운 데이터값이 주어졌을때 미지의 레이블 값을 예측하는 것임

- 대표적인 분류 알고리즘

  - 베이즈(Bayes)통계와 생성모델에 기반한 나이브 베이즈(Naive Bayes)

    - 나이브 베이즈 알고리즘은 베이즈(Bayes) 정리를 기반으로 만들어진 분류 알고리즘이다. 

      

      ![img](https://blog.kakaocdn.net/dn/NTMaT/btq0oaopU4r/hNu5saVJOtopMhQikpF0W1/img.png)

      

      P(A | B)는 조건부 확률로 사건 B가 발생했을 때 사건 A가 발생할 확률을 의미한다. 

      나이브 베이즈 알고리즘은 미리 발생한 사건들을 학습시킨 모델을 만든 후 새로운 데이터가 들어오면 이전의 사건들을 기반으로 이 데이터가 어떤 행동을 할 것인지 예측하는 원리이다.

  - 독립변수와 종속변수의 선형관계성에 기반한 로지스틱 회귀

    - 로지스틱 회귀는 일반적이고 효과적인 분류 알고리즘이다. 이름에 회귀라는 단어가 종종 회귀 분석에만 사용될 것처럼 헷갈리곤 하지만 범주형 자료를 분류하는데 매우 강력한 알고리즘이다. 독립변수와 종속변수의 선형 관계성을 기반으로 만들어졌다.

  - 데이터 균일도에 따른 규칙 기반의 결정 트리

    - 결정 트리는 트리(Tree) 기반의 분류 알고리즘으로 직관적으로 이해하기 쉽다. 규칙 노드(Decision Node)에서 규칙에 따라 분할되며 각각의 서브 트리(Sub Tree)를 생성한다. 계속되는 규칙에 따라 노드가 분할되며 최종적으로 리프 노드(Leaf Node)에서는 클래스 값을 가지게 된다. 데이터가 주어졌을 때 각 노드의 단계를 거치며 분류를 하게 되며 마지막 노드에 도달했을 때 그 노드의 값으로 데이터의 클래스를 예측하는 방식이다.

       

      

      ![img](https://blog.kakaocdn.net/dn/bya8ZP/btq0kDZcQyf/m975jDSkk694FFX141DVT0/img.webp)

      

    - 분류를 위해 규칙들을 계속해서 추가한다는 것은 규칙 노드들이 많아지는 것을 의미하며 이는 모델이 더욱더 복잡해지고 결국에는 과적합(overfitting)까지 발생할 수 있게 된다. 결정 트리를 구성할 때 한쪽으로 치우치지 않게 적절히 분할해야 하며 가지치기를 통해 관련성이 적은 서브 트리를 제거하거나 트리의 깊이에 제한을 두는 등의 방식으로 과적합이 일어나지 않을 적절한 트리를 만들어야 한다.

  - 개별 클래스 간의 최대 분류 마진을 효과적으로 찾아주는 서포트 벡터 머신(SVM)

    - 서포트 벡터 머신은 딥러닝이 대두하기 전까지 가장 많이 활용되던 머신러닝 알고리즘이다. 클래스를 분류할 수 있는 다양한 경계선이 존재하는데 그중 최적의 라인을 찾아내는 원리이다. 명확하게 분류할 수 있는 데이터 집단에서 뛰어난 성능을 나타내며 고차원 공간에서도 효과적으로 사용이 가능하다.

       ![img](https://blog.kakaocdn.net/dn/bAZqh3/btq0oMnkgVV/ywOrb0QncQh2akTJ75hiNk/img.jpg)

      

    - 2차원의 공간에서는 경계를 라인으로 그려낼 수 있지만 다차원이 되면 경계를 평면으로 나타내야 하고 이를 초평면(Hyperplane)이라고 부른다. 각각의 데이터 그룹에서 초평면이랑 가장 인접한 데이터를 서포트 벡터(Support vector)라고 하며 초평면과 서포트 벡터 간의 거리인 마진(Margin) 값을 최대로 만들어 냈을 때 최적의 분류 조건에 만족한다.

  - 근접거리를 기준으로 하는 최소근접(Nearest Neighbor) 알고리즘

    - K-최소 근접(K-Nearest Neighbor) 알고리즘 즉 KNN 알고리즘은 데이터들 간의 유사한 특징을 기준으로 분류하는 알고리즘이다. 주어진 데이터의 주변 이웃 데이터들의 특징을 파악하고 가장 유사한 데이터 그룹에 포함되도록 하는 방식이다.

      

      ![KNN algorithm image](https://editor.analyticsvidhya.com/uploads/17303KNN%20working.png)

    - K 개의 다른 레이블을 가진 이웃을 파악하여 분류를 진행하며 주변 이웃임을 확인하기 위해 유클리드 거리(Euclidean distance) 계산을 사용한다. 유사도를 가진 데이터를 파악할 수 있기 때문에 추천 시스템을 구현하거나 의사결정을 위한 시스템을 만들 때 많이 사용된다.

  - 심층 연결 기반의 신경망(Neural Network)

    - 신경망(Neural Network)은 신경세포(Neural)을 구현해 인간의 뇌의 구조를 모방한 알고리즘이다. 심층 신경망은 이러한 신경망을 여러 층으로 늘려 두텁게 만든 것이다. 

      

      ![img](https://blog.kakaocdn.net/dn/cnOJ5j/btq0n9C6eVK/0y1GkMPQkGTcm3nSW8N8Sk/img.jpg)

      

       

    - Input layer를 통해 학습할 데이터를 입력하고 여러 층의 Hidden layer를 거쳐 Output layer로 결과를 도출한다. 이때 output 값으로 얻은 예측 값과 실제 값의 차이를 계산하여 신경망의 가중치(Weight) 값을 조정하여 학습을 반복한다.

    - 이러한 심층 연결 기반의 신경망을 학습하는 과정을 딥러닝(Deep Learning)이라고 하며 DNN 알고리즘 외에도 CNN, RNN, MLP 등의 심층 연결 기반 신경망 알고리즘이 있다.

  - 서로 다른(또는 같은) 머신러닝 알고리즘을 결합한 앙상블(Ensemble)

    - 앙상블 학습은 여러 개의 분류기(Classifier)에서 각각 예측을 수행하고 그 예측을 결합해서 더 나은 예측 결과를 도출해내는 방법이다. 머리를 맞대고 문제를 풀면 쉽게 정답에 도달할 수 있다는 생각에서 비롯되었으며 대부분의 정형 데이터를 분류해 낼 때 뛰어난 효과를 나타낸다. 

      

      ![img](https://blog.kakaocdn.net/dn/c0GS1D/btq0oKXlvq3/kVJfVkROvF4q8cSXGdvDm1/img.png)https://link.springer.com/article/10.1007/s00500-019-04141-w

      

    - 앙상블 학습은 보팅(Voting), 배깅(Bagging), 부스팅(Boosting), 스태킹(stacking) 등 다양한 방식이 있다. 보팅은 하나의 데이터 셋에서 다양한 알고리즘의 분류기를 사용해 예측한 값을 결합하는 방식이다. 배깅은 한 가지의 알고리즘 분류기를 통해 다양한 데이터 셋 각각을 학습시켜 예측한 값을 결합한다. 부스팅은 여러 개의 분류기를 학습하면서 앞서 예측을 진행한 분류기가 예측에 틀린 데이터에 대해 가중치(weight)를 부여하여 다음 분류기의 학습을 진행하는 방식이다. 스태킹은 미리 다른 알고리즘 분류기로로 학습한 예측 값을 다시 학습용 데이터로 만들어 다른 분류기에 재 학습시키는 방식이다.