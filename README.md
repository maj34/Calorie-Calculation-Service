# 1일 권장섭취량 기준 AI 식단관리

음식 칼로리 자동 계산 서비스

<br/>

## 1. 배경 & 목적

- 사용자가 사진을 찍어 업로드하면 1일 권장섭취량을 기준으로 칼로리 계산
- 부족한 영양정보를 바탕으로 새로운 음식을 추천해주는 서비스를 추가해 논문 작성 예정

<br/>

## 2. 주최/주관 & 팀원

- 주최/주관: 국내 최초 빅데이터 연합동아리 BOAZ
- 팀원: 타대생 3명

<br/>

## 3. 프로젝트 기간

- 2022.03. ~ 2022.05. (3개월)

<br/>

## 4. 프로젝트 소개

<img src='https://user-images.githubusercontent.com/75362328/212490413-bec8a077-b588-4d0e-808b-bec592dad31f.png' width='100%' height='80%'>

&nbsp;&nbsp;&nbsp;&nbsp; 코로나19 장기화로 인해 체중관리와 식습관에 대한 관심이 증폭됨에 따라 ‘**AI를 활용한 간편하고 지속 가능한 음식 탐지와 영양 성분 분석 서비스**’를 제안한다. 이는 전문가가 아닌 일반인도 음식의 종류와 영양 성분 및 칼로리를 알 수 있으며 다이어트나 체중 관리를 하는 사람들에게 유용한 서비스를 제공할 수 있다. 

&nbsp;&nbsp;&nbsp;&nbsp; AI Hub의 ‘건강 관리를 위한 영양분석 및 식이관리 음식 이미지’ 데이터 셋 중 사람들이 주로 많이 먹는 **12가지 Category의 라벨을 선정**했다. 본 데이터 셋은 원천 데이터, 라벨링 데이터, 에너지 테이블로 이루어져 있어 탄수화물과 단백질과 지방을 통해 총 에너지(kcal)를 구할 수 있었다. 또한 ‘통합 식품 영양성분 DB’의 영양성분을 활용하여 1인 1회 분량에 대한 총 8개의 영양성분 메타 정보를 계산하여 구축하였다.  

&nbsp;&nbsp;&nbsp;&nbsp; Detector에서 Bounding Box는 잘 잡지만 Multi Food를 Classification 하는 부분의 성능이 좋지 않았기 때문에 **Classifier를 먼저 학습시킨 뒤, Detector에서 Classifier를 Backbone으로 가져와 학습**시키고자 하였다. 따라서 음식 Image가 Input으로 들어왔을 때 **Inception v3 model을 Pre-training 한 Backbone 모형**을 개발하였다. 즉, Food Image Classifier에서 학습한 모형을 Pre-trained 모형으로 활용해 분류기를 학습시켰다. 

&nbsp;&nbsp;&nbsp;&nbsp; Food Detection은 다양한 크기의 음식을 잘 탐지해 주기 위해 **Fast R-CNN 모델을 사용**하였다. 이를 통해 탐지된 음식은 칼로리를 계산해 식약처의 영양성분 표시 기준을 바탕으로 출력해 내게 된다. 그 과정에서 과적합을 방지하기 위해 성능이 낮은 클래스에만 데이터 증강을 하는 **Partial Augmentation(특정 Class만 Augmentation) 방법을 제안**하였고 이 방법은 시간/메모리 상 효율적인 것을 확인할 수 있었다. 음식의 양을 추정하여 **음식량의 맞춤형 영양정보를 제공**하는 서비스를 추가해서 논문 작성 예정이다.

<br/>

## 5. 프로젝트 담당 역할

- 통합식품영양성분DB 기반 데이터 셋 구축 & 전처리
- Inception Block을 사용한 Pre-trained Model 개발
- UFC(Food Detection) 모델 학습 및 최적화
- Partial Augmentation 등의 새로운 방법론을 사용해 성능 비교 및 실험

<br/>

## 6. 발표 자료

[식단관리 최종 발표자료](https://drive.google.com/file/d/1WHLYcqsBX77WnHvQ3lNthGz2nd195Wj3/view)
