## New York City Taxi Trip Duration 간략 설명

https://www.kaggle.com/c/nyc-taxi-trip-duration

**목표**

뉴욕 내 택시 총 운행 지속시간을 예측하는 모델 구현

**평가 Metric - RMSLE (Root Mean Squared Logarithmic Error, 평균제곱급 오차)**



**제출 파일**

- 각 row는 `id`와 `trip_duration`이라는 두 개의 column을 가져야 함
  (`id` : `test.csv`의  ` id`)
- 파일 상단에 header를 포함해야 함

```
id,trip_duration
id00001,978
id00002,978
id00003,978
id00004,978
etc.
```



**분석 파일**

`test.csv` : 625134 운행 기록



**Data fields**

- **id** : 각 운행에 대한 고유 아이디
- **vendor_id** - 각 운행에 대한 서비스 제공자
- **pickup_datetime** - 탑승 날짜/시간
- **dropoff_datetime** - 하차 날짜/시간
- **passenger_count** - 탑승 승객 수
- **pickup_longitude** - 탑승 경도
- **pickup_latitude** - 탑승 위도
- **dropoff_longitude** - 하차 경도
- **dropoff_latitude** - 하차 위도
- **store_and_fwd_flag** - 운행 기록이 서버에 전송되기 전에 차량 메모리에 저장되는 지 여부  Y=저장/포워드; N=미저장/포워드
- **trip_duration** - 운행 (지속)시간 (초)