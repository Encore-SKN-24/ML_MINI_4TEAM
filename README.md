# ML_MINI_4TEAM

# **프로젝트 명 : K-Culture SNS 언급 빈도에 따른 지역 관광 소비 성장률**

## 💡**팀명**

### 아이이반스

## 🌟 **팀원 소개**  

| 이름       | GitHub ID                           |
|:---:|------------------------------------|
| 🧑‍💻 김규호  | https://github.com/kyu5KIm |
| 👩‍💻 김수진  | https://github.com/KimSujin02 |
| 👩‍💻 박정은  | https://github.com/brainkat |
| 👨‍💻 이동민  | https://github.com/LeeDongMin0115 |
| 👨‍💻 정석원  | https://github.com/JeongSW123 |

## 1. 프로젝트 개요
<img width="639" height="826" alt="스크린샷 2026-02-10 193306" src="https://github.com/user-attachments/assets/24192bb2-4f93-4370-8854-81f10ed533c5" />

### 1.1 프로젝트 주제 선정 배경
전 세계적으로 K-컬처가 유행하며 수많은 관광객이 SNS에 관련 콘텐츠를 쏟아내고 있습니다. 저희 팀은 **"온라인상의 뜨거운 관심이 실제 지역 경제 성장에 얼마나 기여하는가?"** 라는 질문에서 시작했습니다. 단순한 유행을 넘어, 디지털 데이터가 실질적인 지역 활성화의 지표가 될 수 있는지 확인하고자 합니다.

### 1.2 프로젝트 목적
‘온라인(SNS)의 언급량이 오프라인의 소비 지출량에 영향을 끼칠 것이다’ 라는 가설을 통해 전국의 시군구별 각 관광지의 데이터를 분석하여 가설을 검증하는 활동을 진행하는것 뿐만 아니라 지속적인 성장을 머신러닝을 통해 학습하고 지역 성장률 예측을 통해 관련 정책 및 행사 유치 정보를 제공하는 것이 목적이다. 

## 2. 데이터 선택 및 구조

### 2.1 데이터 선택
- **출처**: 문화 빅데이터 플랫폼 (관광지별 소셜 언급량, 평점, 소비액 등)
- **특징**: 전국 시군구별 관광객 수와 SNS 지표가 결합된 다차원 데이터
  
**데이터 출처** <br>
문화 빅데이터 플랫폼(https://www.bigdata-culture.kr/bigdata/user/data_market/detail.do?id=265dad48-d0bd-46ec-a8a4-a93b227d0b42#)

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
<img width="1589" height="166" alt="image" src="https://github.com/user-attachments/assets/742bee4b-aa63-4ec9-98db-650ee1e2546a"/>

## 4. 데이터 전처리 및 EDA (탐색적 데이터 분석)

### 4.1 이상치 수정
|이상치 확인|이상치 수정|결과값|
|:---:|:---:|:---:|
|<img width="192" height="511" alt="시도별 이상치 사진" src="https://github.com/user-attachments/assets/0a30f775-9949-4617-8335-f00e0efa893e" />|<img width="200" height="276" alt="image" src="https://github.com/user-attachments/assets/54995e18-16f3-4cb9-ae73-8e1cc53ba0f3" />|<img width="196" height="332" alt="스크린샷 2026-02-11 오전 12 50 55" src="https://github.com/user-attachments/assets/fef5f234-dd30-4877-bb11-ea7d094fa0b6" />|
|<img width="133" height="505" alt="이상치 변경전" src="https://github.com/user-attachments/assets/103cd8c7-fa67-467e-908e-72aa8d03fa3b" />|<img width="217" height="508" alt="시군구 이상치 수정" src="https://github.com/user-attachments/assets/ebd8e7f7-9fa5-463f-a37b-3747adb32d67" />|<img width="191" height="543" alt="이상치 변경후" src="https://github.com/user-attachments/assets/31db3d52-fd48-49fc-9097-665aed9e2d06" />|


### 4.2 데이터 조회
<img width="463" height="421" alt="image" src="https://github.com/user-attachments/assets/36014529-569a-4416-b011-deb50dfa5017" />

### 4.3 그래프 시각화

|막대그래프|
|:---:|
|<img width="1143" height="658" alt="상위 15개 시- 관광소비금액 평균" src="https://github.com/user-attachments/assets/abdcdf9d-26d8-4cd8-8b20-82594ebc28ef"/>|
| 수도인 서울의 소비금액이 가장 높고, 서울 내에서는 강남구가 소비 지역 1위 |

|산점도|
|:---:|
|<img width="1012" height="546" alt="리뷰수 대 관광소비금액 (선형 회귀선) 관계" src="https://github.com/user-attachments/assets/445f027a-ad5c-41f3-9311-a05c10c6da45" />|
|리뷰 수가 많다고 소비를 많이 하는 것은 아님, 리뷰의 양(수)보다 리뷰의 질(평점)이 소비에 더 중요한 요인|

|히트맵|
|:---:|
|<img width="766" height="681" alt="주요 관광 및 sns 언급 빈도 지표 간 상관관계" src="https://github.com/user-attachments/assets/ae465dd0-77fc-4203-b56e-9e56ce232839" />|
|관광소비금액과 관광고객수 상관관계 확인(양의 상관관계)|

|관광 효율성|
|:---:|
|<img width="1300" height="623" alt="관광 효율" src="https://github.com/user-attachments/assets/13e8709c-d93f-4209-b018-39af98fd053e" />|
|서울과 부산 등 대도시를 중심으로 관광객당 소비가 높게 나타남|

<!-- |만족도와 리뷰수 살펴보기|
|:---:|
|<img width="589" height="616" alt="리뷰 수 인기 대 만족도" src="https://github.com/user-attachments/assets/6fbd1263-923f-40d8-ab49-87b4bf711878" />|
|리뷰 수가 많다고 해서 평점이 반드시 비례해서 높은 것은 아님을 보여줌|
-->
|관광객 수와 소비금액의 관계|
|:---:|
|<img width="676" height="578" alt="스크린샷 2026-02-10 192426" src="https://github.com/user-attachments/assets/5ac1b642-0259-4724-8dd6-c017424fe02f" />|

### 5. 머신러닝 파이프라인
<img width="474" height="208" alt="머신러닝 파이프라인" src="https://github.com/user-attachments/assets/1b185c16-9dba-4593-a652-9df85e0aba4a" />

#### 학습에 사용된 변수
- SNS 언급 빈도 및 증감률
- 구글 리뷰 수, 평점
- 관광객 수
- 이전 시점 소비 데이터 (Lag 변수)

#### - 테스트 모델 및 하이퍼파라미터 후보군

|Random Forest : 랜덤 포레스트|Gradient Boosting : 그래디언트 부스팅|
|:---:|:---:|
|<img width="562" height="645" alt="image" src="https://github.com/user-attachments/assets/0f3681fb-7cc6-438d-b470-f1faeb750248" />|<img width="516" height="485" alt="image" src="https://github.com/user-attachments/assets/06529e05-8a88-4138-b0fc-f0b5f0a0d2ef" />|
|XGBoost : eXtreme Gradient Boosting|
|<img width="495" height="601" alt="image" src="https://github.com/user-attachments/assets/34903874-ef56-4433-bfe2-94860cd85743" />|

|최종 변수 결과|
|:---:|
|<img width="628" height="1058" alt="image" src="https://github.com/user-attachments/assets/e1f2fa05-8917-43f1-8d90-dc3314fcb9d8" />|
|교차 검증 결과|
|<img width="606" height="161" alt="image" src="https://github.com/user-attachments/assets/77886b2f-2103-463c-a033-2ce51d306454" />|

|예측에 영향이 큰 변수 상위 5가지|
|:---:|
|<img width="1222" height="718" alt="스크린샷 2026-02-10 192038" src="https://github.com/user-attachments/assets/33b46e26-8f39-4493-bef5-dc1271b2380c" />|

|예측에 따른 상승 확률이 높은 / 낮은 지역 10개의 지역|
|<img width="1507" height="526" alt="스크린샷 2026-02-10 191936" src="https://github.com/user-attachments/assets/8f338371-79df-4a7e-872a-2ad250ff5aaa" />|


## 6. 최종 인사이트 및 정책적 제언
### 6.1 데이터 분석 인사이트
- **양(Quantity)보다 질(Quality)의 결합**:
  단순히 언급 빈도가 높다고 소비 성장이 보장되지는 않습니다. 평점과 리뷰 수가 동반 상승하는 지역일수록 소비 성장 예측 확률이 높았습니다. 화제성으로 방문을 유도할 수는 있으나, 실제 소비를 이끌어내는 핵심은 **관광지의 만족도**입니다.
- **지속 가능한 경제의 축**: 지난 10년간 K-컬처 산업은 매출 2.3배, 수출 3.9배라는 양적 성장을 이뤄냈으며, 본 분석 또한 이러한 흐름을 뒷받침합니다.
  
### 6.2 정책적 제언
- **선제적 인프라 확충**: 모델이 예측한 '차월 소비 급증 지역'을 대상으로 쓰레기 처리, 주차장 확보, 안전요원 배치 등 수용 태세를 한 달 전에 미리 점검하여 관광객 만족도를 제고해야 합니다.
-  **골든타임 마케팅**: SNS 언급량이 급증한 시점으로부터 1개월 이내에 지역 프로모션이나 할인 쿠폰을 집중 배포하여 잠재 고객의 실제 방문율을 극대화해야 합니다.
- **소상공인 데이터 지원**: 지역 상인들에게 차월 예상 유입객 추이 데이터를 제공하여, 식자재 재고 관리 및 인력 배치를 효율화할 수 있도록 실질적으로 지원해야 합니다.

### 7. 한계점
본 프로젝트는 유의미한 예측 성과를 거두었으나, 데이터 및 모델링 측면에서 다음과 같은 한계가 존재합니다. 향후 연구에서 이를 보완한다면 더욱 정교한 모델을 구축할 수 있을 것입니다.
#### 모델 및 외부 요인의 한계
- 외부 변수 미반영:
 관광 소비는 기상 상황(폭우, 폭설), 환율, 정치적 이슈 등 외부 요인에 민감합니다. 현재 모델은 이러한 거시 경제 지표를 포함하지 않아 급격한 환경 변화 시 예측력이 저하될 수 있습니다. 향후 외부 변수 추가를 통한 정교화 작업이 필요합니다.

🌈 **회고록**

김규호: <br>
keep: 프로젝트를 시작하면서 주제를 정할 때 목적과 기대 효과를 확실하게 생각한다. <br>
problem: 시계열 데이터를 사용해 수집할 수 있는 데이터의 한계가 있다보니 예측값이 잘 나오지 않은게 아쉽다.  <br>
try: 기상청 날씨 데이터나 환율같은 이벤트 변수를 추가하면 예측력이 훨씬 올라갈 것 같다. <br>

김수진: 정책에 활용 가능한 데이터를 기반으로 머신러닝을 적용해 보며, 분석 결과가 현장 의사결정과 연결될 수 있다는 점을 체감할 수 있었습니다. 피처 설계 과정에서는 어떤 변수가 실제 정책 판단에 의미 있는지 고민하며 다소 어려움을 느꼈고, 단순한 모델 성능보다 결과를 어떻게 활용할 수 있을지 우선적으로 고려하게 되었습니다.

박정은: 데이터를 수집하면서 서로 다른 데이터들을 하나로 묶을 수 있는 연결 고리(공통 분모)를 찾는 과정에서 지속적인 어려움을 겪었습니다.  예측 모델을 위해 가능한 한 다양한 조합에 에상 값을 논의했던 점은 매우 유익했다고 생각합니다.  데이터들이 서로 완벽하게 들어맞지 않더라도, 이를 최대한 활용하고 연결해 결과물을 도출하는 시도를 지속해보고 싶습니다.

이동민: 주제를 정할 때 목적·기대효과를 먼저 명확히 잡는 게 중요하다는 걸 배웠습니다. 다만 변수 설계가 어렵고 서로 다른 데이터들을 하나로 묶는 공통 분모를 찾는 과정에서 어려움이 있었고 예측 성능과 결과 해석부분이 아쉬웠습니다. 다음에는 변수를 보강하고 완성도를 높일 수 있도록 노력하겠습니다.

정석원: 주제를 정하고 데이터를 수집하면서 여러 데이터들을 하나로 묶고 원하는 결론을 도출하기까지 계속해서 어려움을 겪었고, 시계열 데이터를 이용하다 보니 한계점이 명확하게 보여 원하던 예측값을 도출해내지 못해서 아쉬웠다. 또 다른 변수를 추가하면 예측 성능을 더 올릴 수 있을거 같습니다.

