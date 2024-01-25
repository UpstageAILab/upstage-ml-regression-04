[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-24ddc0f5d75046c5622901739e7c5dd533143b0c8e959d652212380cedb1ea36.svg)](https://classroom.github.com/a/g6ZC_OOE)
# House Price Prediction | 아파트 실거래가 예측

## Team

| ![박패캠](https://avatars.githubusercontent.com/u/156163982?v=4) | ![이패캠](https://avatars.githubusercontent.com/u/156163982?v=4) | ![최패캠](https://avatars.githubusercontent.com/u/156163982?v=4) | ![김패캠](https://avatars.githubusercontent.com/u/156163982?v=4) |
| :--------------------------------------------------------------: | :--------------------------------------------------------------: | :--------------------------------------------------------------: | :--------------------------------------------------------------: |
|            [김영천](https://github.com/dudcjs2779)             |            [배창현](https://github.com/Bae-ChangHyun)             |            [조예람](https://github.com/huB-ram)             |            [박슬아](https://github.com/SeulaPark)             | 
|                            팀장, 담당 역할                             |                            담당 역할                             |                            담당 역할                             |                            담당 역할                             |  

## 1. Competetion Info

### 1-1 Overview

House Price Prediction 경진대회는 주어진 데이터를 활용하여 서울의 아파트 실거래가를 효과적으로 예측하는 모델을 개발하는 대회입니다. 

부동산 실거래가의 예측은 시세를 예측하여 적정한 가격에 구매와 판매를 도와주게 합니다. 그리고, 정부의 입장에서는 비정상적으로 시세가 이상한 부분을 체크하여 이상 신호를 파악하거나, 업거래 다운거래 등 부정한 거래를 하는 사람들을 잡아낼 수도 있습니다. 

저희는 이러한 목적 하에서 다양한 부동산 관련 의사결정을 돕고자 하는 부동산 실거래가를 예측하는 모델을 개발하는 것입니다. 특히, 가장 중요한 서울시로 한정해서 서울시의 아파트 가격을 예측하려고합니다.

### 1-2 Timeline

Jan 15, 2024 ~ Jan 25, 2024

### 1-3 Evaluation

RMSE

해당 시점의 매매 실거래가를 예측하는 Regression 대회이며, 평가지표는 RMSE(Root Mean Squared Error)를 사용합니다.
RMSE는 예측된 값과 실제 값 간의 평균편차를 측정합니다. 아파트 매매의 맥락에서는 회귀 모델이 실제 거래 가격의 차이를 얼마나 잘 잡아내는지 측정합니다. 

## 2. Components

### Directory

- _Insert your directory structure_

## 3. Data descrption

### 3-1 Dataset overview

Train
: 2007년 1월 1일부터 2023년 6월 30일 사이의 예측해야 할 거래금액(target)을 포함한, 52개의 아파트의 정보에 대한 변수와 거래시점에 대한 변수 총 1,118,822개

Test
: 학습 데이터기간 이후 3개월인 2023년 7월 1일부터 2023년 9월 26일까지의 정보로 구성되어 총 9272개

### 3-2 EDA
전용면적범주: 40미만-소형, 40\~60-중소형, 60~85-중형, 85\~135-중대형, 135초과-대형

- 전용면적
  - 거래가와 매우 큰 상관관계를 가짐 
  - 중소형과 중형의 분포가 가장 많음
- 계약년월일
  - 최근날짜에 가까워질 수록 거래가와 매우 높은 양의 상관관계
- 층
  - 거래가와 약한 상관관계
  - 전용면적이 크거나 거래가가 높은 아파트의 경우 오히려 상관관계가 낮음
  - 중소형 면적에서 가장 높은 상관관계를 보이고 이후 중형, 중대형, 대형으로 갈수록 상관관계가 낮아짐
  - 고층 아파트의 경우 일정 층수 이상인 경우 상관관계가 거의 없어지는 것으로 보임
- 주차대수
  - 거래가와 약한 상관관계가 있으며 세대당주차대수 컬럼을 만들었을때 상관관계가 0.23->0.39로 증가하였음


### 3-3 Feature engineering

- _Describe feature engineering process_

## 4. Modeling

### 4-1 Model descrition

- _Write model information and why your select this model_

### 4-2 Modeling Process

- _Write model train and test process with capture_

## 5. Result

### 5-1 Leader Board

- _Insert Leader Board Capture_
- _Write rank and score_

### 5-2 Presentation

- _Insert your presentaion file(pdf) link_

## etc

### Meeting Log

- _Insert your meeting log link like Notion or Google Docs_

### Reference

- _Insert related reference_
