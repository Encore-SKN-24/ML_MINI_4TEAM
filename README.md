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

### 1.1 프로젝트 주제 선정 배경

### 1.2 프로젝트 목적

## 2. 데이터 선택 및 구조

### 2.1 데이터 선택

**데이터 출처**
문화 빅데이터 플랫폼 : https://www.bigdata-culture.kr/bigdata/user/data_market/detail.do?id=265dad48-d0bd-46ec-a8a4-a93b227d0b42#!

---

### 2.2. 데이터 구조

#### **분석 타겟 컬럼**
- `FRNR_TURSM_SPND_PRICE`: 외국인 관광 소비 금액
- `NATIVE_TURSM_SPND_PRICE`: 내국인 관광 소비 금액
- 
#### **주요 변수**
- **기본**: 관광객 수, 내국인 소비 금액, 리뷰 수, 평균 평점
- **SNS**: SNS 빈도수(`BASE_YM_FQ_CO`), 전월 빈도수(`BASE_YEAR_BEFORE_MT_FQ_CO`)

<br>

## 3. 데이터 기초 통계량


## 4. 데이터 전처리 및 EDA (탐색적 데이터 분석)
  - `CHNNEL_NM == '채널전체'` 필터링을 통해 채널별 중복 집계 제거
    


### 4.1 데이터 조회


### 4-2. 그래프 시각화

####  막대그래프


#### 산점도

#### 분포도

#### 히트맵

### 5. 머신러닝 파이프라인

#### - 학습에 사용된 변수

#### - 변수 전처리 과정

#### - 테스트 모델 및 하이퍼파라미터 후보군

- Linear Regression : 선형 회귀 <br>
- Ridge Regression : 릿지 회귀 (L2 정규화) <br>
- Lasso Regression : 라쏘 회귀 (L1 정규화) <br>
- Decision Tree : 결정 트리 회귀 <br>
- Random Forest : 랜덤 포레스트 회귀 <br>
- Gradient Boosting : 그래디언트 부스팅 회귀 <br>
- SVR : 서포트 벡터 회귀 <br>
- KNN : K-최근접 이웃 회귀 <br>
- XGBoost : eXtreme Gradient Boosting 회귀 <br>

각 모델별로 다양한 하이퍼파라미터 후보군을 설정하여 성능을 비교함

#### - 최종 변수 결과


#### - 교차 검증 결과


## 6. 최종 인사이트 및 정책적 제언

#### 상관 관계


### 7. 한계점

🌈 **회고록**

김규호:
김수진:
박정은:
이동민:
정석원:
