### regression try log



#####실수 only

1) passenger_count
2) distance
3) avg_speed_h

- **시간 데이터 실수로 반영**

4) R + pickup_hour —> 0.015
5) R + pickup_weekday —> 0.014
6) R + pickup_month —> 0.014
7) R + pickup_hour + pickup_weekday —> 0.014
8) R + pickup_weekday + pickup_month —> 0.014
9) R + pickup_hour + pickup+weekday + pickup_month —> 0.014

#####카테고리 only

1) pickup_month
2) pickup_weekday
3) pickup_hour
4) vendor_id
5) store_and_fwd_flag

#####실수 + 카테고리

1) R + pickup_hour —> 0.015
2) R + pickup_weekday —> 0.015
3) R + pickup_month —> 0.014
4) R + pickup_hour + pickup_weekday —> 0.015\
5) R + pickup_hour + pickup_month —> 0.015
6) R + pickup_weekday + pickup_month —> 0.015
7) R + pickup_hour + pickup+weekday + pickup_month —> 0.015

- **시간 데이터 없이 카테고리값만**

8) R + vendor_id —> 0.015
9) R + store_and_fwd_flag —> 0.014
10) R + vendor_id + store_and_fwd_flag —> 0.015