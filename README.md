# NH투자증권(주식보유기간예측)
### 프로젝트 수행기간- 2021-08-30~ 2021-12
### 실행환경 COLAB + LOCAL 두가지 버전으로 실행 (자원의 한계)

## 프로젝트 상세설명

- NH 투자증권 고객 데이터를 분석하여 향후 주식보유기간 예측모델 구축
## 추가변수 설명 (개장일기준)
- hist_d : 최근 보유하고있는 주식의 소유기간을 2020년 12월 31일 기준으로 끊은 값 
- past_d : 과거 보유했던 주식의 보유기간( 한국 개장일 기준) ( 출처 http://open.krx.co.kr/contents/MKD/01/0110/01100305/MKD01100305.jsp) (공휴일+휴장일 제외하고계산)


## 제외 변수 기준
- 액면가,종목이름 등 주식보유기간에 영향을 크게 주지않는다고 판단한 변수들은 제외

## 기존변수 
- 원천컬럼명	한글컬럼명	예시	비고


ACT_ID	계좌ID	27666E123D	사내 계좌번호를 토대로 임의 생성한 값으로 사용
SEX_DIT_CD	성별	01	1:남성 / 2:여성
CUS_AGE_STN_CD	연령구간	30	"사내 CUS_AGE를 토대로 연령대 구분  
01: 20세~25세미만  
02: 25세~30세미만  
03: 30세~35세미만  
04: 35세~40세미만  
05: 40세~45세미만  
06: 45세~50세미만  
07: 50세~55세미만  
08: 55세~60세미만  
09: 60세~65세미만"  

IVS_ICN_CD	투자성향	04	"계좌 가입시 설문조사로 결정되는 투자성향  
01: 안정형  
02: 안정추구형  
03: 위험중립형  
04: 적극투자형  
05: 공격투자형  
09: 전문투자가형  
00: 정보제공미동의  
99: 미정의"  


CUS_AET_STN_CD	고객자산구간	01	"고객총자산 금액을 구간별로 구분한 코드   
01: 0원이상-1천만원미만  
02: 1천만원이상-3천만원미만  
03: 3천만원이상-5천만원미만  
04: 5천만원이상-1억원미만  
05: 1억원이상-3억원미만  
06: 3억원이상"  


MRZ_PDT_TP_SGM_CD	주거래상품군	01	"고객의 월말 기준 잔고가 가장 많은 상품의 유형으로 분류, 잔고가 동일할 경우 상품소분류코드가 작은 순으로 우선 인식  
01: Only CMA  
02: 국내주식  
03: 해외주식  
04: 선물옵션  
05: 금속  
06: 국내채권  
07: 해외채권  
08: 펀드  
09: ELS/DLS  
10: 신탁_퇴직연금  
11: RP  
12: 발행어음  
14: WRAP  
15: 신용대출  
99: 미정의"  


LSG_SGM_CD	LIFESTAGE	02	"고객 Life stage, 업종 등 고려하여 유사 특성을 보유한 고객 클래스 도출  
02: 사회초년생 (20-29세)  
03: 가족형성기_남자 (30-39세 & 남자)  
04: 가족형성기_여자 (30-39세 & 여자)  
05: 가족성숙기_직장인 (40-59세 & 직장인 & 남자)  
06: 가족성숙기_주부 (40-59세 & 주부 & 여자 )  
07: 가족성숙기_남자 (40-59세 & 기타 & 남자 )  
08: 가족성숙기_여자 (40-59세 & 기타 & 여자)  
09: 은퇴기 (60-69세)"  


TCO_CUS_GRD_CD	고객등급	05	"자산 및 수익 기준 고객의 등급을 부여  
01: 탑클래스 (자산1)10억이상 or 수익기여도2) 5백만원 이상)  
02: 골드 (자산3억이상 or 수익기여도 3백만원 이상)  
03: 로얄 (자산1억이상 or 수익기여도 1백만원 이상)  
04: 그린 (자산3천이상 or 수익기여도 5십만원 이상)  
05: 블루 (자산1천이상 or 수익기여도 1십만원 이상)  
09: 등급 미정의  
99: 미정의 (결측치)"  


TOT_IVS_TE_SGM_CD	총투자기간	01	"계좌를 개설한 이래 고객이 100만원 이상 보유한 개월 수   
01: 6개월 미만  
02: 6개월-1년 미만  
03: 1년-3년 미만  
04: 3년-5년 미만  
05: 5년-10년 미만  
06: 10년 이상"  


MRZ_BTP_DIT_CD	주거래업종구분	01	"해당월 거래 금액이 가장 큰 업종 구분   
01: 건설업  
02: 금융업  
03: 기계  
04: 방송/통신  
05: 서비스/오락/문화  
06: 운송/운수  
07: 유통  
08: 의료/의약  
09: 전기/전자  
10: 제조  
11: 철강  
12: 화학  
13: IT  
14: 기타  
15: 혼합  
16: 비매매  


잔고정보 (국내 주식건에 한해)				  
	국내주식 잔고이력(STK_BNC_HIST.CSV)  			
	원천컬럼명	한글컬럼명	예시	비고  
	ACT_ID	계좌번호	27666E123D	사내 계좌번호를 토대로 임의 생성한 값으로 사용  
	BSE_DT	기준일자	20200522	  
	IEM_CD	종목코드	A000100	  
	BNC_QTY	잔고수량	500	  
	TOT_AET_AMT	잔고금액	945000	  
	STK_PAR_PR	액면가	1000  
  
 국내주식 보유기간(STK_HLD_.CSV)			
원천컬럼명	한글컬럼명	예시	비고  
ACT_ID	계좌번호	27666E123D	사내 계좌번호를 토대로 임의 생성한 값으로 사용  
IEM_CD	종목코드	A168330	  
BYN_DT	매수일	20200522	  
HOLD_D	보유일	6	  
HOLD_D_21	보유일(‘21년)	5	  
TP	학습구분	trn	"trn: 학습 구분  

종목정보(IEM_INFO.CSV)		  		
	원천컬럼명	한글컬럼명	예시	비고  
	IEM_CD	종목코드	A000080	  
	BTP_CFC_CD	종목업종	05	"01: 건설  
02: 금융  
03: 기계  
04: 통신  
05: 서비스  
06: 운송  
07: 유통  
08: 의료  
09: 전기  
10: 제조  
11: 철강  
12: 화학  
13: IT  
14: 기타 "  
	MKT_PR_TAL_SCL_TP_CD	시가총액규모유형  
01	"01: 대형주   
02: 중형주  
03: 소형주  
99: 기타"  
	STK_DIT_CD	시장구분	02	
"01: 코스피200  
02: 코스닥150    
99: 기타"  
	IEM_KRL_NM	종목한글명	동화약품보통주


### 모델링

- LGBM,XGBOOST 두개를 이용(2021-09-26기준)
- LGBM,XGBOOST 를 BLENDING 해서 혼합예측
- FEATURE IMPORTANCE 를 이용해 몇가지 특징들은 제외
- hyper parameter tuning (리소스 한계로 인해 GRID SEARCH 는 불가능했고 중요 변수인 max_depth,learning_rate,iteration,reg_alpha,reg_lambda 를 우선적으로 튜닝하였음
- 





### Gradient Boosting

#### 대부분 회귀문제에서는 loss function 으로 mse 를 사용 -> negative gradient = residual(잔차) 가 된다. A 모델로 예측후 잔차를 계산하고  그 잔차를 정답으로 B모델을 훈련, 그리고 또 잔차를 계산하여 C모델을훈련 등등 으로 여러 모델을 결합하여 예측


#### Ensemble:
1. Voting: 서로 다른 종류의 모델의 예측을 결합하여 최종값 결정 ( 제일 많이나온값을 택하거나 확률값들의 평균이 제일 높은것을 택하거나 등등 )
2. bagging: 동일 알고리즘의 모델을 여러개사용 but 데이터 샘플링을 다르게 
3. gradient boosting: 잔차를 학습
