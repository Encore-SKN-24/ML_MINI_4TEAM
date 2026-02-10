# ML_MINI_4TEAM

# **프로젝트 명 : K-Culture SNS 언급 빈도에 따른 지역 관광 소비 성장률**

## 💡**팀명**

### 아이이반스

## 🌟 **팀원 소개**  

| 이름       | GitHub ID                           |
|------------|------------------------------------|
| 🧑‍💻 김규호  | https://github.com/kyu5KIm |
| 👩‍💻 김수진  | https://github.com/KimSujin02 |
| 👩‍💻 박정은  | https://github.com/brainkat |
| 👨‍💻 이동민  | https://github.com/LeeDongMin0115 |
| 👨‍💻 정석원  | https://github.com/JeongSW123 |


## 1. 프로젝트 개요
<img width="639" height="826" alt="스크린샷 2026-02-10 193306" src="https://github.com/user-attachments/assets/24192bb2-4f93-4370-8854-81f10ed533c5" />

### 1.1 프로젝트 주제 선정 배경
SNS의 영향력이 지속적으로 상승하고 있는데 지금 전세계적으로 K-컬쳐가 유행하고 있습니다.  지금 수많은 관광객들이 K-키워드에 많은 관심을 가지며 컨텐츠를 제작합니다. 하지만 지역 관광 및 성장에 정말로 영향이 있는지,  온라인의 뜨거운 관심이 실제 지역의 성장에 기여를 했는지를 확인한다.

### 1.2 프로젝트 목적
‘온라인(SNS)의 언급량이 오프라인의 소비 지출량에 영향을 끼칠 것이다’ 라는 가설을 통해 전국의 시군구별 각 관광지의 데이터를 분석하여 가설을 검증하는 활동을 진행하는것 뿐만 아니라 지속적인 성장을 머신러닝을 통해 학습하고 지역 성장률 예측을 통해 관련 정책 및 행사 유치 정보를 제공하는 것이 목적이다. 

## 2. 데이터 선택 및 구조

### 2.1 데이터 선택
관광지별 소셜 언급량, 구글 평점 및 리뷰 개수, 관광객 수, 관광 소비액 등의 정보를 포함

**데이터 출처**
문화 빅데이터 플랫폼 : https://www.bigdata-culture.kr/bigdata/user/data_market/detail.do?id=265dad48-d0bd-46ec-a8a4-a93b227d0b42#!

---

### 2.2. 데이터 구조

|컬럼영문명|컬럼한글명|
|---|---|
|TRRSRT_NM|관광지명|
|BASE_YM|기준년월|
|CHNNEL_NM|채널명|
|BASE_YEAR_ACCMLT_FQ_CO|기준년도누적빈도수|
|BASE_YM_FQ_CO|	기준년월빈도수|
|BASE_YEAR_BEFORE_MT_FQ_CO|기준년도이전월빈도수|
|BEFORE_MT_VERSUS_FQ_CO_IRDS_RT|이전월대비빈도수증감율|
|AVRG_SCORE_VALUE|평점값|
|REVIEW_CO|리뷰수|
|PLACE_TY|장소유형|
|LC_LA|위치위도|
|LC_LO|위치경도|
|ADDR|주소|
|CTPRVN_NM|시도명|
|SIGNGU_NM|시군구명|
|TURSM_CSTMR_CO|관광고객수|
|BEFORE_YEAR_MT_TURSM_CSTMR_CO|이전년도월관광고객수|
|TURSM_CSTMR_CO_IRDS_RT|관광고객수증감율|
|TURSM_SPND_PRICE|관광소비금액|
|NATIVE_TURSM_SPND_PRICE|내국인관광소비금액|
|FRNR_TURSM_SPND_PRICE|외국인관광소비금액|

#### **분석 타겟 컬럼**
- `NEXT_GROWTH_LABEL` : 다음달 관광 소비 금액 상승 여부 (0 or 1)
  
#### **주요 변수**
- **기본**: 관광객 수, 내국인 소비 금액, 리뷰 수, 평균 평점
- **SNS**: SNS 빈도수(`BASE_YM_FQ_CO`), 전월 빈도수(`BASE_YEAR_BEFORE_MT_FQ_CO`)

<br>

## 3. 데이터 기초 통계량
<img width="1589" height="166" alt="image" src="https://github.com/user-attachments/assets/742bee4b-aa63-4ec9-98db-650ee1e2546a" />

## 4. 데이터 전처리 및 EDA (탐색적 데이터 분석)
|이상치 확인|이상치 수정|결과값|
|---|---|---|
|<img width="192" height="511" alt="시도별 이상치 사진" src="https://github.com/user-attachments/assets/0a30f775-9949-4617-8335-f00e0efa893e" />|<img width="217" height="508" alt="시군구 이상치 수정" src="https://github.com/user-attachments/assets/ebd8e7f7-9fa5-463f-a37b-3747adb32d67" />|<img width="196" height="332" alt="스크린샷 2026-02-11 오전 12 50 55" src="https://github.com/user-attachments/assets/fef5f234-dd30-4877-bb11-ea7d094fa0b6" />|




### 4.1 데이터 조회
<img width="403" height="365" alt="스크린샷 2026-02-10 201808" src="https://github.com/user-attachments/assets/a48dca90-1ec5-4e7d-b3d3-17b9cad4bd32" />
석원님

### 4-2. 그래프 시각화

#### 막대그래프
<img width="1143" height="658" alt="상위 15개 시- 관광소비금액 평균" src="https://github.com/user-attachments/assets/abdcdf9d-26d8-4cd8-8b20-82594ebc28ef" />

#### 산점도
<img width="1012" height="546" alt="리뷰수 대 관광소비금액 (선형 회귀선) 관계" src="https://github.com/user-attachments/assets/445f027a-ad5c-41f3-9311-a05c10c6da45" />

#### 분포도
<img width="1181" height="688" alt="시도명별로 리뷰 수 분포" src="https://github.com/user-attachments/assets/ae389151-8b43-49ff-8371-89f2a56aeae2" />

#### 히트맵
<img width="766" height="681" alt="주요 관광 및 sns 언급 빈도 지표 간 상관관계" src="https://github.com/user-attachments/assets/ae465dd0-77fc-4203-b56e-9e56ce232839" />

#### 관광 효율성 
<img width="1300" height="623" alt="관광 효율" src="https://github.com/user-attachments/assets/13e8709c-d93f-4209-b018-39af98fd053e" />

### 만족도와 리뷰수 살펴보기
<img width="589" height="616" alt="리뷰 수 인기 대 만족도" src="https://github.com/user-attachments/assets/6fbd1263-923f-40d8-ab49-87b4bf711878" />

### 관광객 수와 소비금액의 관계
<img width="676" height="578" alt="스크린샷 2026-02-10 192426" src="https://github.com/user-attachments/assets/5ac1b642-0259-4724-8dd6-c017424fe02f" />

### 혼동 행렬
<img width="765" height="481" alt="스크린샷 2026-02-10 192056" src="https://github.com/user-attachments/assets/e47f451a-2d6c-4ce3-80d4-bb34dab83d30" />


### 예측에 영향이 큰 변수 상위 5가지
<img width="1222" height="718" alt="스크린샷 2026-02-10 192038" src="https://github.com/user-attachments/assets/33b46e26-8f39-4493-bef5-dc1271b2380c" />


### 예측에 따른 상승 확률이 높은 / 낮은 지역 10개의 지역
<img width="1507" height="526" alt="스크린샷 2026-02-10 191936" src="https://github.com/user-attachments/assets/8f338371-79df-4a7e-872a-2ad250ff5aaa" />




### 5. 머신러닝 파이프라인
<img width="474" height="208" alt="머신러닝 파이프라인" src="https://github.com/user-attachments/assets/1b185c16-9dba-4593-a652-9df85e0aba4a" />


#### - 학습에 사용된 변수
- SNS 언급 빈도 및 증감률
- 구글 리뷰 수, 평점
- 관광객 수
- 이전 시점 소비 데이터 (Lag 변수)

#### - 테스트 모델 및 하이퍼파라미터 후보군

- Random Forest : 랜덤 포레스트 <br>
<img width="562" height="645" alt="image" src="https://github.com/user-attachments/assets/0f3681fb-7cc6-438d-b470-f1faeb750248" />

- Gradient Boosting : 그래디언트 부스팅 <br>
<img width="516" height="485" alt="image" src="https://github.com/user-attachments/assets/06529e05-8a88-4138-b0fc-f0b5f0a0d2ef" />

- XGBoost : eXtreme Gradient Boosting <br>
<img width="495" height="601" alt="image" src="https://github.com/user-attachments/assets/34903874-ef56-4433-bfe2-94860cd85743" />

각 모델별로 다양한 하이퍼파라미터 후보군을 설정하여 성능을 비교함

#### - 최종 변수 결과
<img width="628" height="1058" alt="image" src="https://github.com/user-attachments/assets/e1f2fa05-8917-43f1-8d90-dc3314fcb9d8" />

#### - 교차 검증 결과
<img width="606" height="161" alt="image" src="https://github.com/user-attachments/assets/77886b2f-2103-463c-a033-2ce51d306454" />


## 6. 최종 인사이트 및 정책적 제언
### 6.1 데이터 분석 인사이트
1. 양보다 중요한 질의 결합
   언급 빈도수가 높다고 해서 소비 성장이 보장되는 것은 아닙니다. 평점과 리뷰수가 함께 상승하는 지역일수록 소비 성장 예측 확률이 높게 나타났습니다. 화제성으로 방문객을 유지할 수는 있지만, 실제 소비를 이끌어내는 것은 관광지의 만족도입니다.
2. K-Culture의 지역 낙수효과
   서울 및 주요 대도시뿐 아니라, 특정 K-푸트/뷰티 키워드와 연결된 지방 소도시에서도 SNS 언급량 증가 후 소비 성장이 관측되었습니다. 소셜 트랜드가 지역 균형 발전에 기여할 잠재력이 있음을 보여줍니다.
### 6.2 정책적 제언
 - 모델이 예측한 '다음 달 소비 급증 예상 지역'을 대상으로 쓰레기 처리, 주차장 확보, 안전요원 배치등 인프라를 1개월 전에 미리 준비하여 관광객 만족도를 높여야 합니다.
 - SNS 언급량이 급증한 시점으로부터 1개월 내에 해당 지역 프로모션이나 할인 쿠폰을 배포하여, 잠재 고객의 실제 방문율을 극대화해야 합니다.
 - 지역 소상공인들에게 다음 달 우리 동네 예상 유입객 추이 데이터를 제공하여, 식자재 재고 관리 및 인력 배치를 효율화 하도록 지원해야 합니다.

### 7. 한계점
본 프로젝트는 유의미한 예측 성과를 거두었으나, 데이터 및 모델링 측면에서 다음과 같은 한계가 존재합니다. 향후 연구에서 이를 보완한다면 더욱 정교한 모델을 구축할 수 있을 것입니다.
#### 7.1 데이터의 한계

#### 7-2 모델 및 외부 요인의 한계
- 외부 변수 미반영:
  관광 소비는 날씨(폭우,폭설), 전염병, 환율, 정치적 이슈등 외부 요인에 매우 민감합니다 본 모델은 기상 데이터나 경제 지표를 포함하지 않아 급격한 환경 변화시 예측 성능이 저하 될 수 있습니다.


🌈 **회고록**

김규호:

김수진:

박정은:

이동민:

정석원:
