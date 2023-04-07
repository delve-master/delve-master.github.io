---
layout: post
title: "오버피팅 문제"
categories: ["computer science"]
tags: ["machine learning", "machine learning specialization", "coursera"]   # TAG names should always be lowercase!
published: false
---

# 개요      

귀하가 머신 러닝 모델을 학습시키려 한다고 가정하자. 귀하의 모델이 거듭된 학습끝에 주어진 학습 데이터에 완벽히 들어맞게되었다. 그럼 이 모델이 새로 추가된 데이터도 잘 예측할 수 있을까? 꼭 그런건 아닐 수 있다. 

왜 그런지 **오버피팅** 또는 **과적합**의 개념을 통해 알아보자[^1]. 


## 오버피팅(overfitting) 문제

머신러닝을 배울 때 흔히 사용하는 예시인 집값 예측을 해보자. x를 집의 크기로, y를 가격으로 둔 training data가 있다고 하고 이를 각기 다른 회귀(regression)로 학습시킨 모델 3가지를 보도록 하자. 

![Comparing different performance of linear regression models](overfitting_1.JPG)

첫번째 모델은 단순한 선형 회귀로 학습되었다. 딱 봐도 데이터에 잘 들어맞지는 않는 모습을 보여준다. 

두번째 모델은 확실히 첫번째보다는 나은 모습을 보여준다. $x^2$과 가중치(weight) w이 추가되며 

```python
print("Hello, world!") 
```

```java
public static void main(String[] args) {
    Console.log.printf("GoGart :>")
}
```

### Photo Example

![nani](https://upload.wikimedia.org/wikipedia/commons/thumb/b/b6/Image_created_with_a_mobile_phone.png/640px-Image_created_with_a_mobile_phone.png)

---

[^1]: 본 포스팅은 Coursera 플랫폼에서 스탠포드 대학교가 주관하는 *Machine Learning Specialization* 온라인 강의에서 발췌한 내용을 포함합니다. 