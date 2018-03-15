Regression Team Project

###Data Science School 7th Team B-5

DSS 7B-5 회귀분석 팀프로젝트 - New York City Taxi Trip Duration

출처: [Kaggle Competition - New York City Taxi Trip Duration](https://www.kaggle.com/c/nyc-taxi-trip-duration)

- Language: Python
- Regression: OLS (statsmodel), Ridge (scikit-learn)

###Overview

- Subject: New York City Taxi Trip Duration
- Dataset: 2016 NYC Cab trip record data (by TLC)
- Objective: Building a model that predicts the duration of each trip in New York City.
- Evaluation: RMSLE 

###Data fields

- id - 각 운행별 고유 id
- vendor_id - 운행별 각 택시 회사의 id
- pickup_datetime - 승차 날짜/시각 (미터기 기록 시작)
- dropoff_datetime - 하차 날짜/시각 (미터기 기록 종료)
- passenger_count - 승객 수
- pickup_longitude - 승차 위도
- pickup_latitude - 승차 경도
- dropoff_longitude - 하차 위도
- dropoff_latitude - 하차 경도
- store_and_fwd_flag - 운행 기록 서비 전송 전 차량 메모리 저장 여부 (Y: 저장/전송, N: 미저장/전송)
- trip_duration - 운행 소요 시간 (초)



## Contents

### 1. 데이터 탐색 및 전처리
- Train/Test Data 탐색
- 변수 기초 전처리
  - datetime parsing (to month, weekday, hour)
  - binarize categorical data
  - get distance, bearing from coordinates

### 2. 변수 분석
- 변수 시각화
  - Distribution of trip duration (dependent variable)
  - pairplot / boxplot
  - weird data from trip duraiton & coordinates
- 변수간 상관관계 파악
  - Correlation Coefficient
- 변수 중요도/영향 파악
  - F-test
  - VIF (Multicollinearity)
  - One-Way ANOVA

### 3. Modeling (OLS)
- 1차 modeling
    - rough modeling
- 2차 modeling
    - Normality of residual
    - Removing outlier (by Cook's Distance)
    - Model selection

### 4. 결과 진단
- Cross Validation
  - K-Fold Cross Validation
  - Ridge / Lasso / Elastic Net
- 정규화 하이퍼 모수 최적화
  - Hyperparameter Tuning (Ridge)

### 5. Kaggle submission

### 6. Lesson