# K-MOOC 실습으로 배우는 머신러닝 6강

## TODO
1. Decision Tree
2. Decision Tree 학습
3. Decision Tree Regression

## DONE

### Decision Tree Learning 정의
특정 기준(질문)에 따라 데이터를 구분하는 모델을 의사 결정 트리(Decision Tree) 모델이라고 합니다.

![image](https://user-images.githubusercontent.com/88615790/202986804-2473a74d-b80d-4784-884d-baf183fcd8bc.png)

### 관련 용어
* 결정 트리에서 질문이나 정답은 노드(Node)라고 불립니다.
*   맨 처음 분류 기준을 Root Node라고 하고
*   중간 분류 기준을 Intermediate Node
*   맨 마지막 노드를 Terminal Node 혹은 Leaf Node라고 합니다.( Class Label을 나타낸다.)

결정 트리의 기본 아이디어는, Leaf Node가 가장 섞이지 않은 상태로 완전히 분류되는 것, 즉 불순도를 낮도록 만드는 것입니다.

#### 불순도 (Impurity)
* 결정트리에서 분기기준을 선택하기 위해서는 불순도(impurity)라는 개념을 사용합니다.
* 해당 범주 안에 서로 다른 데이터가 얼마나 섞여 있는지를 뜻합니다.
* 다양한 개체들이 섞여 있을수록 불순도가 높아집니다.
* 분기기준 설정 시 현재노드의 불순도에 비해 자식노드의 불순도가 감소되도록 합니다.

### 의사결정나무 설계의 핵심 과제 : 
* 어떻게 나무를 키울 것인가?
* 불필요한 것들은 어떻게 쳐낼 것인가 ?  

대표적인 알고리즘: CART , C4.5 , CHAID 알고리즘

### CART(Classification And Regression Tree) 알고리즘 
* 가장 널리 사용되는 의사결정나무 알고리즘
* 불순도 측정 시 목표 변수가 범주형인 경우 지니 계수를 사용하고 , 연속형인 경우 분산을 사용하여 Binary Classification을 수행한다. 
* CART 알고리즘에서는 모든 조합에 대해 Gini index를 계산한 후, Gini index가 가장 낮은 지표를 찾아 분기합니다.

#### 지니지수
지니지수는 얼마나 불확실한가? (=얼마나 많은 것들이 섞여있는가?)를 보여준다. 따라서 지니 지수가 0이라는 것은 불확실성이 0이라는 것으로 같은 특성을 가진 객체들끼리 잘 모여있다는 의미이다.
![image](https://user-images.githubusercontent.com/88615790/202988925-323b4d11-215d-48ae-a31c-9e4ef7588630.png)


#### Binary Classification
CART 알고리즘의 또 하나의 특징으로는 가지 분기 시, 여러 개의 자식 노드가 아닌 단 두 개의 노드로 분기한다는 것 입니다 (Binary tree).
![image](https://user-images.githubusercontent.com/88615790/202989506-9c125f7e-eb05-4765-a946-35fe4aa5f483.png)

#### Regression tree
CART 알고리즘은 Regression(회귀)를 지원합니다

회귀 트리 (Regression Tree)의 방법은 간단합니다. 분기 지표를 선택할 때 사용하는 index를 불순도 (Entropy, Gini index)가 아닌, 실제값과 예측값의 오차를 사용합니다.

예를 들어 아래의 데이터 패턴 중 x < 0.3 x<0.3과 x < 0.6 x<0.6을 지표로 하는 나무는 두 개의 초록 점선으로 데이터(가지)를 나눌 것입니다.
![image](https://user-images.githubusercontent.com/88615790/202990123-364b23fa-a81b-4056-891c-959a8a3b9b44.png)

각 구간의 x값이 들어올 경우, training data (파란 점)의 평균값 (빨간 실선)을 예측값으로 내놓습니다. 나무의 깊이가 깊어질 수록, 다시 말하면 데이터를 나누는 초록 점선이 촘촘하게 생길 수록 예측값과 실제값의 오차는 줄어들 것입니다.
![image](https://user-images.githubusercontent.com/88615790/202990247-af5cd8b1-66ae-4bf7-b367-1ffe200b2519.png)


Binary tree의 좌우가지에 대한 오차값 을 계산하고, 좌우 가지에 해당하는 샘플 수의 비율을 가중치로 곱해 전체 오차값을 계산하여 지표간 비교를 통해 최적의 분기를 결정합니다.

Reference:
* https://tyami.github.io/machine%20learning/decision-tree-4-CART/
* https://wooono.tistory.com/104
