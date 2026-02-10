# ML_MINI_4TEAM

# **프로젝트 명 : 

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


## 🛠️ **기술 스택**


## 1. 프로젝트 개요
<img width="639" height="826" alt="스크린샷 2026-02-10 193306" src="https://github.com/user-attachments/assets/24192bb2-4f93-4370-8854-81f10ed533c5" />

### 1.1 프로젝트 주제 선정 배경

### 1.2 프로젝트 목적

## 2. 데이터 선택 및 구조

### 2.1 데이터 선택

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
- `FRNR_TURSM_SPND_PRICE`: 외국인 관광 소비 금액 (수정)
- `NATIVE_TURSM_SPND_PRICE`: 내국인 관광 소비 금액 (수정)
- 
#### **주요 변수**
- **기본**: 관광객 수, 내국인 소비 금액, 리뷰 수, 평균 평점
- **SNS**: SNS 빈도수(`BASE_YM_FQ_CO`), 전월 빈도수(`BASE_YEAR_BEFORE_MT_FQ_CO`)

<br>

## 3. 데이터 기초 통계량
<img width="1589" height="166" alt="image" src="https://github.com/user-attachments/assets/742bee4b-aa63-4ec9-98db-650ee1e2546a" />


## 4. 데이터 전처리 및 EDA (탐색적 데이터 분석)
  - `CHNNEL_NM == '채널전체'` 필터링을 통해 채널별 중복 집계 제거
    


### 4.1 데이터 조회
<img width="403" height="365" alt="스크린샷 2026-02-10 201808" src="https://github.com/user-attachments/assets/a48dca90-1ec5-4e7d-b3d3-17b9cad4bd32" />


### 4-2. 그래프 시각화

####  막대그래프


#### 산점도

#### 분포도

#### 히트맵

### 5. 머신러닝 파이프라인

#### - 학습에 사용된 변수
- SNS 언급 빈도 및 증감률
- 구글 리뷰 수, 평점
- 관광객 수
- 이전 시점 소비 데이터 (Lag 변수)
#### - 변수 전처리 과정

#### - 테스트 모델 및 하이퍼파라미터 후보군

- Random Forest : 랜덤 포레스트 회귀 <br>
<img width="562" height="645" alt="image" src="https://github.com/user-attachments/assets/0f3681fb-7cc6-438d-b470-f1faeb750248" />

- Gradient Boosting : 그래디언트 부스팅 회귀 <br>
<img width="516" height="485" alt="image" src="https://github.com/user-attachments/assets/06529e05-8a88-4138-b0fc-f0b5f0a0d2ef" />

- XGBoost : eXtreme Gradient Boosting 회귀 <br>
<img width="495" height="601" alt="image" src="https://github.com/user-attachments/assets/34903874-ef56-4433-bfe2-94860cd85743" />

각 모델별로 다양한 하이퍼파라미터 후보군을 설정하여 성능을 비교함

#### - 최종 변수 결과


#### - 교차 검증 결과
<img width="606" height="161" alt="image" src="https://github.com/user-attachments/assets/77886b2f-2103-463c-a033-2ce51d306454" />


## 6. 최종 인사이트 및 정책적 제언

#### 상관 관계


### 7. 한계점

🌈 **회고록**

김규호:

김수진:

박정은:

이동민:

정석원:
