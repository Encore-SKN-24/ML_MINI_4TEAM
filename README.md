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

### 4.1 데이터 조회
<img width="403" height="365" alt="스크린샷 2026-02-10 201808" src="https://github.com/user-attachments/assets/a48dca90-1ec5-4e7d-b3d3-17b9cad4bd32" />
석원님

### 4-2. 그래프 시각화

#### 막대그래프

#### 산점도

#### 분포도

#### 히트맵

### 5. 머신러닝 파이프라인

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

### 7. 한계점

🌈 **회고록**

김규호:

김수진:

박정은:

이동민:

정석원:
