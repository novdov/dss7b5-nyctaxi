## Regression Team Project

### [Data Science School 7th Team B-5 (발표자료)](https://github.com/novdov/dss7b5-nyctaxi/blob/master/main/5%ED%8C%80(committer)_B_%EB%B0%9C%ED%91%9C%EC%9E%90%EB%A3%8C.ipynb)

DSS 7B-5 회귀분석 팀프로젝트 - New York City Taxi Trip Duration

출처: [Kaggle Competition - New York City Taxi Trip Duration](https://www.kaggle.com/c/nyc-taxi-trip-duration)

- 사용 언어: Python
- 회귀 모델링: OLS (statsmodel), Ridge (scikit-learn)

### Overview

- 목표: 뉴욕시 택시 운행별 소요 시간 예측 모델 구축
- 데이터 출처: 2016 NYC Cab trip record data (by TLC)
- 평가 지표: RMSLE 

### Data fields

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
  - datetime 파싱 (to month, weekday, hour)
  - 카테고리 데이터 인코딩
  - 위/경도로부터 거리와 이동 각도 (bearing) 계산

### 2. 변수 분석
- 변수 시각화
  - 타겟(Trip Duration)의 분포
  - 타겟 데이터와 변수간 시각화
  - 아웃라이어 파악
- 변수간 상관관계 파악
  - Correlation Coefficient
- 변수 중요도/영향 파악
  - F-test
  - VIF (Multicollinearity)
  - One-Way ANOVA

### 3. Modeling (OLS)
- 1차 modeling
    - 여러 변수 시도
- 2차 modeling
    - 아웃라이어 제거 (Cook's Distance 이용)
    - 잔차 정규성 확인
    - 모델 선택
      <img src="https://github.com/novdov/dss7b5-nyctaxi/blob/master/img/model2.png?raw=true">

### 4. 결과 진단
- Cross Validation
  - K-Fold Cross Validation
  - Ridge

### 5. Kaggle submission (Score: 0.50591, 808/1257)
<img src="https://github.com/novdov/dss7b5-nyctaxi/blob/master/img/rkaggle_submission_0314_02.png?raw=true">

### 6. Lesson

- feature 개수가 적은 상황에서 주어진 feature의 제한적인 활용으로 모델 성능 개선이 어려웠음
    - 위/경도 변수로부터 ‘distance’만 유의미하게 활용함
    - speed 활용한 모델링 실패 (아웃라이어 제거할수록 잔차 정규성 악화)
    - 시간별 trip duration의 유의미한 변화를 발견했지만 모델에 적극적으로 반영되지 못함
        - 각 시간 변수의 interaction이 반영되지 않음
        - 실수변수로 반영했지만, polynomial 특성을 제대로 파악/반영하지 못함

<img src="https://github.com/novdov/dss7b5-nyctaxi/blob/master/img/model1_partial.png?raw=true">

- OLS분석 진행시 과학적인 모델링 방법론의 부재에 대한 아쉬움

### [7. Follow-Up (0.50591 --> 0.48977, 769/1257)](https://github.com/novdov/dss7b5-nyctaxi/blob/master/main/5%ED%8C%80(committer)_B_%EB%B0%9C%ED%91%9C%EC%9E%90%EB%A3%8C-followup.ipynb)

```
model = sm.OLS.from_formula("np.log1p(trip_duration) ~ scale(np.log1p(distance)) + scale(bearing)"
                            "+ C(pickup_hour):C(pickup_weekday)"
                            "+ scale(pickup_longitude) + C(vendor_id)", train_rev01)
```

<img src="https://github.com/novdov/dss7b5-nyctaxi/blob/master/img/kaggle_submission_0415.png?raw=true">

- 3차 Modeling
    - 시간 변수 카테고리로 반영
    - weekday/hour interaction
    -  R Squared 0.700 ---> 0.725로 상승
