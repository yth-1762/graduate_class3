# 딥러닝토픽

#일시
- 2023-03 ~ 2023-06

# 주제
- chatgpt에 대한 tweets의 sentiment 분류

# 배경 및 목적
- chatgpt 출시 이후 이에 대한 다양한 의견을 나타내는 tweets들 존재
- hatgpt 입장에서는 향후 개선을 위해 다양한 의견을 파악하는 것이 중요하다고 판단
- RNN,LSTM,GRU 모델을 활용하여 chatgpt에 대한 tweets의 sentiment(긍정,중립,부정)가 무엇인지 예측
 

# 데이터
- https://www.kaggle.com/datasets/charunisa/chatgpt-sentiment-analysis/code?dataset
Id=2896084 (데이터 출처)
- 데이터 개수 : 217622개
- Serial number, tweets, labels(bad,good,other) 3개의 변수로 구성
  

# 사용언어/모델
- python/ RNN, LSTM, GRU

# 모델 성능 지표
- BIC, RMSE

# 데이터 전처리
- 6월 1일부터 6월 8일 까지의 총 2000개 데이터만 활용(비가 오지 않으면서 지방선거 날과 현충일이 있는 등 8일동안 평일과 휴일이 적절히 잘 섞여 있는 기간이기에 이 기간으로 설정)
- ‘대여시간’ 변수의 범주는 0시부터 23시까지 총 24개의 범주로 이루어져 있다. 0시부터 06시 사이의 이용자수들은 다른 시간대에 비해 상대적으로 이용자수가 적기 때문에 이 시간대 이용자들은 분석 대상에 미포함(3시간 간격으로 총 6개범주로 처리).
- AGE_TYPE 변수는 60대 70대는 50대와 통합
- USE_CNT 변수는 이용건수가 1번인 이용자 1, 1번 이상인 이용자는 0으로 처리
- USE_TYPE 변수는  정기권은 1, 정기권이 아닌 이용권들은 0으로 처리
- FEATURE ENGINEERING: RENT_SPOT(대여장소)(업무,지하철,주거), park(공원 인접 여부), holiday(휴일 여부)

# 프로젝트 내용
- BIC 기준(k=2일때 -10657.99, k=3일때 -10122.29, k=4일때 -9835.712) component가 2인 GMM 모형 fitting /추정 latent variable: 속도, 긴박성
- BIC 기준(k=3일때 -155586.71, k=4일때 -14672.784, k=5일때 -14601.217) component가 3인 MoE 모형 fitting / 추정latent variable: riding purpose, willpower(desire) of riding
- MoE 모형 으로 나온 cluster 별 평균 운동량 예측(cluster1: 83.01738, cluster2: 80.8889, cluster3: 191.2407)
- 운동량의 RMSE와 MAE를 기준으로 MoE를 RANDOM FOREST와 LINEAR MODEL과 비교
- RMSE(randomforest: 61.07248, linear model: 30.85834, MoE: 27.87566) -> MoE가 가장 좋은 성능 보임


# 기대효과
- 서울시(여의도, 상암지역)의 공공자전거 이용자 분류를 MoE를 통해 분류하여 이들이 어떤 component에 속할지 예측.  
- 얼마만큼의 운동량을 가지는지 예측.
