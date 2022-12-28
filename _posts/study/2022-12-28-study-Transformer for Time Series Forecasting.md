---
layout: post
title: Transformer for Time Series Forecasting
description: >
  Transformer를 사용하여 시계열 데이터 예측 방법
categories: deep
tags: study deep
sitemap: false
hide_last_modified: true
comments: true
---
# 시계열 데이터에 Transformer 사용시 문제점

Transformer 활용한 기존 연구들은 자연어 처리 분야에 활용되었던 일반적인 Transformer 구조를 빌려 시계열 예측 프레임워크를 구성한다.

자연어 처리에 사용하는 Transformer 모델은 자가회귀(Auto-regressive) 구조로 되어있다.

(Auto-regressive 그림추가)

자가회귀 구조란, 출력한 결괏값이 다시 입력으로 들어가는 구조를 말한다. 이 구조는 출력값에 오차가 생기면 다음 예측값을 출력하는 데 영향을 준다는 문제점이 있다. 자연어 처리의 Transformer는 단어를 출력하기 때문에 이러한 문제점이 덜 두드러지지만, 시계열 예측의 Transformer는 예상되는 수치를 출력하기 때문에 이러한 문제가 더 뚜렷해진다. 그래서 자가 회귀 구조 기반의 Transformer를 시계열 예측에 활용했을 때 예측하고자 하는 시점이 기준 시점보다 멀수록 예측 정확도가 떨어진다는 구조적인 한계점이 있다. 


