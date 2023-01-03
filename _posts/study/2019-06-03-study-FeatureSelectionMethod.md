---
layout: post
title: "Feature Selection Method"
description: >
  #Feature selection #Wrapper method #Filter method #Embedded method'
categories: [study]
tags: [deep]
sitemap: false
hide_last_modified: true
comments: true
---

## Feature Selection Method
**변수 선택 기법(Feature Selection Method)**모델을 돌릴 때, 불필요한 변수들을 제거함으로써 모델의 속도 개선, 오버피팅 방지 등의 효과를 얻기 위해 사용하는 방법

> Feature Selection의 3가지 방법
> 1. Wrapper method : 모델링 돌리면서 변수 채택
> 2. Filter Method : 전처리단에서 통계기법을 사용하여 변수 채택
> 3. Embedded method : 라쏘, 릿지, 엘라스틱넷 등 내장함수를 사용하여 변수 채택

### Wrapper method
Machine Learning의 예측 정확도 측면에서 **가장 좋은 성능을 보이는 Subset을 뽑아내는 방법이다.** Machine Learning을 진행하면서 Best Feature Subset을 찾아가는 방법이기 때문에 시간과 비용이 매우 높게 발생한다. 하지만 최종적으로 Best Feature Subset을 찾아주기 때문에 모델의 성능을 위해서는 매우 바람직한 방법이다. 물론, 해당 모델의 파라미터와 알고리즘 자체는 완성도가 높아야 제대로 된 Best Feature Subset을 찾을 수 있다.

**Forward Selection** 변수가 없는 상태로 시작하며 반복할 때마다 가장 중요한 변수를 추가하여 더이상 성능의 향상이 없을 때까지 변수를 추가한다.

**Backward Elimination** 모든 변수를 가지고 시작하며, 가장 덜 중요한 변수를 하나씩 제거하면서 모델의 성능을 향상시킨다. 더 이상 성능의 향상이 없을 때까지 반복한다.

**Stepwise Selection** Foward Selection 과 Backward Elimination 을 결합하여 사용하는 방식으로, 모든  변수를 가지고 시작하여 가장 도움이 되지 않는 변수를 삭제하거나, 모델에서 빠져있는 변수 중에서 가장 중요한 변수를 추가하는 방법이다. 이와 같이 변수를 추가 또는 삭제를 반복한다. 반대로 아무것도 없는 모델에서 출발해 변수를 추가, 삭제를 반복할 수도 있다. 


### Filter method
Machine Learning에 있어서 Best Feature Subset 을 주는 것이 아니라, 사용자에게 feature-rank를 줌으로 각 Feature 가 얼마큼의 영향력을 가지는지를 알려주는 방법이다. 따라서 해당 모델에 Best Feature Subset 은 아닐 수 있더라도, 사용자에게 **도움을 주는 역할 정도**를 한다고 볼 수 있다. 또한 여기서 각 ranking 화 한 Feature 들은 전부 독립변수로 본다.


### Embedded Method
Embedded method 는 모델의 정확도에 기여하는 피처를 학습합니다. 좀 더 적은 계수를 가지는 회귀식을 찾는 방향으로 제약조건을 주어 이를 제어합니다. 예시로는 아래와 같습니다.

**LASSO** L1-norm을 통해 제약 주는 방법

**Ridge** L2-norm을 통해 제약 주는 방법

**Elastic Net** 위 둘을 선형결합한 방법

**SelectFromModel** Tree 기반 알고리즘에서 피처를 뽑아오는 방법(RandomForest, LightGBM 등)


## 참고
- https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=euleekwon&logNo=221465108279
- https://dyddl1993.tistory.com/18
- https://subinium.github.io/feature-selection/
