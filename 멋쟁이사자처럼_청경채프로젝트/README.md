# 링크 
https://dacon.io/competitions/official/235961/data

# Dataset Info.

train_input [폴더] - 총 58개 청경채 케이스
각 청경채 케이스 별 환경 데이터 (1분 간격)


train_target [폴더] - 총 58개 청경채 케이스
rate : 각 청경채 케이스 별 잎 면적 증감률 (1일 간격)


test_input [폴더] - 총 6개 청경채 케이스
각 청경채 케이스 별 환경 데이터 (1분 간격)


test_target [폴더] - 총 6개 청경채 케이스
rate : 각 청경채 케이스 별 잎 면적 증감률 (1일 간격)
제출을 위한 양식으로 label에 해당되는 rate의 값은 모두 0으로 가려져있습니다.


submission 은 각 케이스 별로 쪼갠 rate값에 대한 RMSE*100 값을 입력하여 제출
