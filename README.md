# 딥러닝토픽

# 일시
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
- 12000개의 데이터만 무작위로 추출
- tweets 변수에서 텍스트만 반영하기 위해 https:// 부분, 특수문자 제거 이후 사전을 만든 후 정수형으로 인코딩
- 종속변수는 good tweet는 1, neutral tweet는 0, bat tweet는 –1로 처리한 후 원핫인코딩 실시
- train data, test data 8:2 비율로 설정

# 프로젝트 내용
- RNN 모형 FITTING(epochs=10, batch size= 32, optimizer=adam, loss=categorical entropy, activation=softmax, 유닛수=64, bidirectional(return_sequences=True) 1번,bidirectional 1번 dropout(0.2)옵션 1번 추가)
- LSTM 모형 FITTING(epochs=10, batch size 32, optimizer=adam, loss=categorical entropy, activation=softmax, 유닛수=128,bidirectional(return_sequences=True) 1번, dropout(0.2)옵션 1번 추가)
- GRU 모형 FITTING(epochs=10, batch size 32, optimizer=adam, loss=categorical entropy, activation=softmax, 유닛수=128,bidirectional(return_sequences=True, recurrent_dropout=0.2) 1번, bidirectional(recurrent_dropout=0.2) 1번 dropout(0.2)옵션 1번 추가)
- test data accuracy 기준(RNN: 64.46%, LSTM: 69.29, GRU: 72.29%) GRU 모형 최종 선택


# 기대효과
- 향후 chatgpt에 대한 의견을 나타내는 tweets이 앞으로도 계속 생겨날 것이고 이 모델을 통해 chatgpt에 대한 전반적인 여론이 어떠한지 파악
