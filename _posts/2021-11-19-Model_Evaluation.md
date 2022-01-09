---
layout: post
title:  "사이킷런 머신러닝 평가"
date:   2021-11-20 18:00:00 +0700
categories: [MerchineLearning]
---





#### 1. 분류(Classification) 머신러닝 평가 지표

- 정확도(Accuracy)

  ![image-20220109151803336](C:\Users\espark\AppData\Roaming\Typora\typora-user-images\image-20220109151803336.png)

  - 정확도는 분류 모델을 평가하기 위한 하나의 메트릭임
  - 비공식적으로 **정확도** 는 우리 모델이 옳았던 예측의 비율임
  - 이진 분류의 경우 정확도는 다음과 같이 양수 및 음수 측면에서도 계산할 수 있음
  - 모델이 얼마나 정확하게 분류를 하는지 나타냄

  - 사용법(https://scikit-learn.org/stable/modules/generated/sklearn.metrics.accuracy_score.html 참조)

    ```python
    sklearn.metrics.accuracy_score(*y_true*, *y_pred*, ***, *normalize=True*, *sample_weight=None*)
    ```

    - **y_true** : 정답 레이블
    - **y_pred** : classifier가 반환한 예측 레이블
    - **normalize** bool, default=True : **기본값=참**인 경우 올바르게 분류된 샘플의 수를 반환함. **거짓**인 경우 올바르지 않게 분류된 샘플의 비율을 반환함
    - **sample_weight** : 기본값 = None, 샘플 가중치로 배열을 input 하면 됨

- 오차행렬(Confusion Matrix)

  ![image-20220109152036364](C:\Users\espark\AppData\Roaming\Typora\typora-user-images\image-20220109152036364.png)

  - 이진 분류의 경우 정확도는 다음과 같이 양수 및 음수 측면에서도 계산할 수 있음

  - 여기서 *TP* = 참 긍정, *TN* = 참 부정, *FP* = 거짓 긍정, *FN* = 거짓 부정.

    - True Positive: 암을 암이라고 정확하게 예측
    - True Negative: 암이 아닌것을 암이 아니라고 정확하게 예측
    - False Positive: 암을 암이 아니라고 잘못 예측
    - False Negative: 암이 아닌것을 암이라고 잘못 예측

  - 양수 레이블과 음수 레이블 수 사이에 상당한 차이가 있는 이와 같은 **클래스 불균형 데이터 세트로** 작업할 때 정확도만으로는 전체 내용을 알 수 없음

  - [사용법](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.confusion_matrix.html)

    ```python
    sklearn.metrics.confusion_matrix(y_true, y_pred, *, labels=None, sample_weight=None, normalize=None)[source]
    ```

    - **y_true** : 정답 레이블

    - **y_pred** : 분류 classification이 반환한 레이블

    - **labels** : 행렬을 인덱싱할 레이블 목록. 레이블의 하위 집합을 재정렬하거나 선택하는데 사용할 수 있음. None인 경우 y_true나 y_pred가 정렬된 순서로 사용됨

    - **sample_weight** :샘플 가중치

    - **normalize**{‘true’, ‘pred’, ‘all’}, default=None : i번째 행과 j번째 열 항목이 실제 레이블이 i번째 클래스이고 예측 레이블이 j번째 클래스인 샘플 수를 나타내는 정오분류표임

      ```python
      y_true = ["cat", "ant", "cat", "cat", "ant", "bird"]
      y_pred = ["ant", "ant", "cat", "cat", "ant", "cat"]
      confusion_matrix(y_true, y_pred, labels=["ant", "bird", "cat"])
      결과 : array([[2, 0, 0],
            		 [0, 0, 1],
             		 [1, 0, 2]])
      ```

      

- 정밀도(Precision) 

  - 정밀도(precision)은 양성 클래스에 속한다고 출력한 샘플 중 실제로 양성 클래스에 속하는 샘플 수의 비율을 말한다. 높을수록 좋은 모형이다. FDS의 경우, 사기 거래라고 판단한 거래 중 실제 사기 거래의 비율이 된다.

  - 모델이 True라고 분류한 것 중에서 실제 true인 것

  - [사용법](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.precision_score.html)

    ```python
    sklearn.metrics.precision_score(y_true, y_pred, *, labels=None, pos_label=1, average='binary', sample_weight=None, zero_division='warn')
    ```

    - **y_true** : 정답 레이블
    - **y_pred** : 분류 classification이 반환한 레이블

- 재현율(Recall)

  - 재현율(recall)은 실제 양성 클래스에 속한 표본 중에 양성 클래스에 속한다고 출력한 표본의 수의 비율을 뜻한다. 높을수록 좋은 모형이다. FDS의 경우 실제 사기 거래 중에서 실제 사기 거래라고 예측한 거래의 비율이 된다. TPR(true positive rate) 또는 민감도(sensitivity)라고도 한다.

  - 실제 True인 것 중에서 모델이 True라고 예측한 것의 비율

  - precision과 recall은 상호보완적으로 사용할 수 있으며, 두 지표가 모두 높을수록 좋은 모델임

  - [사용법](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.recall_score.html?highlight=recall#sklearn.metrics.recall_score)

    ```python
    sklearn.metrics.recall_score(y_true, y_pred, *, labels=None, pos_label=1, average='binary', sample_weight=None, zero_division='warn')
    ```

    

- F1 스코어

  - 정밀도와 재현율의 가중조화평균(weight harmonic average)을 F점수(F-score)라고 한다. 정밀도에 주어지는 가중치를 베타(beta)라고 한다.
    $$
    Fβ=(1+β2)(precision×recall)/(β2precision+recall)Fβ=(1+β2)(precision×recall)/(β2precision+recall)
    $$
    베타가 1인 경우를 특별히 F1점수라고 한다.
    $$
    F1=2⋅precision⋅recall/(precision+recall)F1=2⋅precision⋅recall/(precision+recall)
    $$

  - 사이킷런 패키지의 metrics 패키지에서는 정밀도, 재현율, F1점수를 구하는 `classification_report` 명령을 제공한다. 이 명령은 각각의 클래스를 양성(positive) 클래스로 보았을 때의 정밀도, 재현율, F1점수를 각각 구하고 그 평균값으로 전체 모형의 성능을 평가한다.

  - [사용법](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.f1_score.html?highlight=f1_score#sklearn.metrics.f1_score)

    ```python
    sklearn.metrics.f1_score(y_true, y_pred, *, labels=None, pos_label=1, average='binary', sample_weight=None, zero_division='warn')
    ```

    

- ROC AUC

  - ROC(Receiver Operator Characteristic) 커브는 클래스 판별 기준값의 변화에 따른 위양성률(fall-out)과 재현율(recall)의 변화를 시각화한 것이다.

  - 모든 이진 분류 모형은 판별 평면으로부터의 거리에 해당하는 판별함수(discriminant function)를 가지며 판별함수값이 음수이면 0인 클래스, 양수이면 1인 클래스에 해당한다고 판별한다. 즉 0 이 클래스 판별 기준값이 된다. ROC 커브는 이 클래스 판별 기준값이 달라진다면 판별 결과가 어떻게 달라지는지는 표현한 것이다.

  - AUC : ROC curve는 그래프이기 때문에 명확한 수치로써 비교하기가 어렵기때문에 그래프 아래의 면적값을 이용함. 이것이 바로 **AUC(Area Under Curve)**임. 최대값은 1이며 좋은 모델(즉, Fall-out에 비해 Recall 값이 클수록) 1에 가까운 값이 나옴

  - 사용법

    ![image-20220109160012596](C:\Users\espark\AppData\Roaming\Typora\typora-user-images\image-20220109160012596.png)

    - [ROC_AUC_SCORE](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.roc_auc_score.html?highlight=roc#sklearn.metrics.roc_auc_score)	

      ```python
      sklearn.metrics.roc_auc_score(*y_true*, *y_score*, ***, *average='macro'*, *sample_weight=None*, *max_fpr=None*, *multi_class='raise'*, *labels=None*)
      ```

      

  

