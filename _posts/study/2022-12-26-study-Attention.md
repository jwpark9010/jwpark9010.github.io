---
layout: post
title: Attention
description: >
  Attention
categories: [study, deep]
tags: [deep]
sitemap: false
hide_last_modified: true
comments: true
---
# Attention 등장 배경

LSTM은 데이터의 시간에 따른 흐름을 분석한다. 과거와 현재의 패턴을 학습하고 미래의 패턴을 예측한다. Attention은 과거와 현재의 패턴을 학습할 때 현재가 과거의 어느 시점과 더 유사한지를 판단한다.
현재 상황을 판단할 때 과거 흐름 중에 어느 시점에 더 집중할 것인지를 판단하는 것이다.
LSTM은 과거의 상황을 균등하게 취급하는 데 반해 Attention은 중요한 과거에 더 높은 가중치를 두는 방식이다. 따라서 LSTM보다 더 개선된 방법이라 할 수있다. 
