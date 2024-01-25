[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-24ddc0f5d75046c5622901739e7c5dd533143b0c8e959d652212380cedb1ea36.svg)](https://classroom.github.com/a/g6ZC_OOE)
# House Price Prediction | 아파트 실거래가 예측

## Team

| ![박패캠](https://avatars.githubusercontent.com/u/156163982?v=4) | ![이패캠](https://avatars.githubusercontent.com/u/156163982?v=4) | ![최패캠](https://avatars.githubusercontent.com/u/156163982?v=4) | ![김패캠](https://avatars.githubusercontent.com/u/156163982?v=4) |
| :--------------------------------------------------------------: | :--------------------------------------------------------------: | :--------------------------------------------------------------: | :--------------------------------------------------------------: |
|            [김영천](https://github.com/dudcjs2779)             |            [배창현](https://github.com/Bae-ChangHyun)             |            [조예람](https://github.com/huB-ram)             |            [박슬아](https://github.com/SeulaPark)             | 
|                            팀장                             |                            팀원                             |                            팀원                             |                            팀원                             |  

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

- 계약경과일
  - 계약년월일이 최근에 가까울 수록 거래가가 높아지는 현상을 더욱 잘 대변할 수 있도록 현재 날짜와 계약년월일의 차이를 구한 계약경과일 컬럼을 생성
- 전용면적_mean
  - 시군구 + 아파트명으로 groupby해서 전용면적의 평균값을 구해 해당의 전용면적범주의 비율을 대략적으로 나타내기를 의도함
- 3월평단가_std
  - 3개월단위로 나타내는 Datetime 컬람을 생성하고 시군구 + 아파트명으로 groupby해서 3개월간의 평단가의 분산을 나타내는 컬럼을 생성. 가격의 변동이 높은 아파트들이 계속해서 가격의 변동이 심할 것이라는 가설을 대입함.
- 세대당주차대수
  - 주채대수와 세대수 컬럼을 이용해서 세대당 주차대수 컬럼 생성
- 고층도
  - 층과 최고층수 컬럼을 이용해서 고층도(해당 아파트에서 고층인 정도의 비율) 컬럼을 생성
- 건물나이
  - 신축과 구축의 여부를 간접적으로 나타내기 위해 계약년월일 컬럼과 차이를 구해서 건물나이 컬럼을 생성
- 동순위
  - 동별 평균 평단가를 구한 뒤 순위를 매겨 동별로 평단가가 컬럼을 대변하도록 의도함
- 아파트순위
  - 시군구+아파트명별로 평균 평단가를 구한 뒤 순위를 매겨 아파트별로 평단가가 컬럼을 대변하도록 의도함.
- 이전계약_diff
  - 시군구 + 아파트명별로 이전계약과 현재계약의 차이를 나타내는 컬럼을 생성. 최근거래 가격의 컬럼이 가르키는 가격이 너무 오래전 데이터인 경우를 보정하기 위함.

## 4. Modeling

### 4-1 Model descrition

- Catboost
- XGBoost
- LGBM
 아파트실거래가를 예측하는 만큼 거래가에대한 이상치를 실제 이상치로 보지 않고 높은가격과 낮은 가격대를 골고루 잘 맞출 수 있는 모델을 모델링하고자 했습니다. 여러번에 실험과 테스트 결과 CV 점수와 LB 점수가 비레하지 않는다고 판단했고 저희는 실제 부동산 데이터에 가깝다고 판단하는 CV 점수에 집중해서 모델링하기로 팀내에서 결정했습니다. 따라서 팀내에서 가장 검증 데이터에 대해서 RMSE 성능이 좋았던 해당 모델을 제출하게 되었습니다.


### 4-2 Modeling Process

<img width="465" alt="스크린샷 2024-01-26 오전 1 17 49" src="https://github.com/UpstageAILab/upstage-ml-regression-04/assets/120548753/07a753ac-66f0-4578-b8a3-85164d5cd958">


## 5. Result

### 5-1 Leader Board
![스크린샷 2024-01-26 011358](https://github.com/UpstageAILab/upstage-ml-regression-04/assets/42354230/c47f4684-662a-4873-80cb-f3c8c8b4ac0e)
- Rank:9
- Score:106512.0996

### 5-2 Presentation

- _Insert your presentaion file(pdf) link_

## etc

### Meeting Log

- _Insert your meeting log link like Notion or Google Docs_

### Reference

- _Insert related reference_
