---
title: "[AI] [이론] 혼동 행렬과 성능측정 지표 정리"
excerpt: "혼동 행렬과 성능측정 지표 정리"
categories: [AI, 이론]
tags: [AI, 인공지능, ML, 머신러닝, 성능측정, 혼동행렬, 정확도, 정밀도, 민감도, 재현율, F1-Score]
---

# [AI] [이론] 혼동 행렬과 성능측정 지표 정리

---

# I. 혼동 행렬

## 1. 혼동 행렬(Confusion Matrix)

- 지도학습으로 훈련된 분류 알고리즘의 성능을 시각화할 수 있는 행렬이다. 행렬의 각 행은 예측된 클래스의 인스턴스를 나타내며, 각 열은 실제 클래스의 인스턴스를 나타낸다. 분류해야 할 클래스가 N개일 때의 혼동 행렬의 사이즈는 N * N이 된다.

<br>

![1](https://github.com/user-attachments/assets/fdca752a-90b8-4d89-8214-6325b07b408f)
> example confusion matrix(2 * 2) of a binary classifier.

![2](https://github.com/user-attachments/assets/0228a99f-b973-46e9-8720-58615190683d)
> 프로젝트 진행 시 실제 성능평가를 위해 활용한 4 * 4 Confusion Matrix. acne, acne_scar, hyperpigmentation은 각각 여드름, 여드름 흉터, 색소침착을 의미하며 수치는 0 ~ 1로 정규화하였다. 

<br>

## 2. 관심 범주

- 분석가가 더 관심이 있는 범주를 의미한다. 모델이 특정한 클래스를 더 잘 예측하는 것이 중요할 때, 이 특정한 클래스를 말한다. 분석가의 의도에 따라 달라진다.

<br>

## 3. TP, TN, FP, FN

- True Positive(TP) : 
관심 범주를 정확하게 분류함. 
= 모델이 참으로 예측 & 실제 클래스가 참이어서 최종 결과가 참인 경우.
- True Negative(TN) : 
관심 범주가 아닌 것을 정확하게 분류함. 
= 모델이 거짓으로 예측 & 실제 클래스가 거짓이어서 최종 결과가 참인 경우.
- False Positive(FP) : 
관심 범주로 잘못 분류함. 
= 모델이 참으로 예측 & 실제 클래스가 거짓이어서 최종 결과가 거짓인 경우. 
= 제 1종 오류.
- False Negative(FN) : 
관심 범주가 아닌 것으로 잘못 분류함. 
= 모델이 거짓으로 예측 & 실제 클래스가 참이어서 최종 결과가 거짓인 경우. 
= 제 2종 오류.

⇒ True / False는 최종 결과를 의미하며, Positive / Negative는 관심 범주 여부를 의미한다.

---

# II. 혼동 행렬로부터 파생되는 4가지 성능측정 지표

<br>

![3](https://github.com/user-attachments/assets/d1318a95-c9e0-4580-8a30-b81e11855d78)
> 당뇨 환자 / 정상인 혼동행렬 예시

<br>

## 1. 정확도(Accuracy)

- 예측 모형의 전체적인 정확도를 평가한다. 위 예시에서의 관심범주는 당뇨환자일 때, 당뇨환자를 당뇨환자로 예측하고, 정상인을 정상인으로 예측한 비율을 의미한다.
  
![4](https://github.com/user-attachments/assets/0eb8527b-21bf-44bf-bd8b-cf50b7cef45b)

> 계산 공식 및 결과 예시

- 문제점 : 모델 전체의 정확도는 92%로 굉장히 높은 수준이나, 당뇨환자만 따져보면 성능이 좋지 못하다. 예시에서 당뇨환자는 실제로 10명(3 + 7) 존재하는데, 3명만 당뇨환자로 예측했기 때문에 모델의 관심범주 예측 정확도는 30%로 절반도 예측하지 못했음을 알 수 있다. 

이러한 이유 때문에 Accuracy 이외 또다른 모델 성능평가 수치가 요구된다.

<br>

## 2. 정밀도(Precision)

- 예측 품질에 대한 수치이며, 정밀도가 높은 예측 알고리즘은 높은 안정성을 가졌다고 인정된다.

![5](https://github.com/user-attachments/assets/84099a2c-2fb8-4a0a-b5ae-51cf52f08f4a)
> 계산 공식 및 결과 예시

<br>

## 3. 민감도 = 재현율(Recall)

- 예측 모델이 실제 데이터에서 존재하는 관심범주 중 몇 개를 관심범주로 정확히 예측했는지에 대한 수치이다.

![6](https://github.com/user-attachments/assets/40cec54f-2dbb-4459-b797-1cb1af83d291)
> 계산 공식 및 결과 예시

<br>

## 4. F1-Score

- 좋은 예측 모델은 정밀도 및 민감도가 동시에 좋아야 한다. 어느 한 쪽의 수치를 높이기 위해 다른 한 쪽의 수치의 질을 희생시켜서는 안 된다. 정밀도 및 민감도의 성능평가를 동시에 수행하기 위해 F1-Score라는 조화평균 값을 이용한다. 계산 결과는 0 ~ 1 사이의 값으로 나타난다.

![7](https://github.com/user-attachments/assets/179d05a7-1d00-4a4f-af69-7641d0e7af07)
> 계산 공식 및 결과 예시

<br>

## 성능측정 지표 산출예시

![8](https://github.com/user-attachments/assets/30046508-a6ee-40b2-b9a2-254aeddcb06d)

- 필자는 프로젝트 진행 시 각 클래스별로 Precision, Recall, F1-Score 값을 산출함으로써 모델의 성능평가에 활용하였다. 색소침착인 hyperpigmentation 클래스의 Recall 값은 0.7(70%) 미만으로 다른 클래스들과 비교했을 때 예측성능이 그다지 좋지 않음을 확인하였다. 성능측정 지표를 산출하여 모델의 성능평가를 측정하는 데 많은 도움이 되었으며 보완점을 캐치할 수 있었다.

---

# III. 요약정리

요약하면 범주형 변수 예측 모형의 성능은 혼동행렬표 상의 정확도 / 정밀도 / 민감도 / F1-Score로 측정하며, 예측하려는 변수의 특징과 문제 상황에 따라 네 가지 성능평가 수치를 적절하게 활용해야 한다.

<br>

전통적으로 혼동행렬은 의학 분야에서 맹렬히 연구되어 왔다. 최근 코로나19와 같은 감염병이 있을 때 해당 질병에 걸린 것이 실제로 맞는지 검사키트의 성능평가를 하는 데 사용되기도 한다. 건강분야에서는 검사의 정확성이 생명과 직결되기에 검사의 성능평가 수요가 매우 크다.

<br>

또한 기계학습 분야, 그 중 지도학습에 있어서 혼동행렬은 성능평가 기준으로 필수적으로 활용된다. 

---


> ### 📑 References : 틀린 설명을 포함할 수 있습니다. <br><br> 1. [위키백과 혼동행렬](https://ko.wikipedia.org/wiki/%ED%98%BC%EB%8F%99_%ED%96%89%EB%A0%AC) <br> 2. [[Pytorch] Performance Evaluation of a Classification Model-Confusion Matrix](https://yeseullee0311.medium.com/pytorch-performance-evaluation-of-a-classification-model-confusion-matrix-fbec6f4e8d0) <br> 3. [혼동행렬(confusion matrix)](https://diseny.tistory.com/entry/%ED%98%BC%EB%8F%99%ED%96%89%EB%A0%ACconfusion-matrix)