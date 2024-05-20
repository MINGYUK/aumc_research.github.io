---
title: "Generative models"
excerpt_separator: "<!--more-->"
categories:
  - Blog
tags:
  - generative model
  - machine learning
---

생성형 모델에 대한 관심이 높다. 생성형 모델이란 무엇인지, 어떻게 작동하는지, 수학적으로 어떤 원리를 바탕으로 하는지 살펴보자.

![생성형 모델의 샘플 생성](https://www.altexsoft.com/static/blog-post/2023/11/38a2d58b-265c-49d8-bf58-353da4f6c6ac.jpg){: .align-left}
(출처: https://www.altexsoft.com/static/blog-post/2023/11)

두개의 그룹으로 묶인 샘플들이 있다고 가정하자. 이 분포를 따르는 새로운 샘플을 어떻게 생성할 수 있을까? 우선은 단순히 두개의 분포를 나타내는 확률밀도함수를 기반으로 새로운 시행을 하는 것을 생각해볼 수 있다. 이 확률밀도함수를 추정하는 것이 생성형 모델을 학습하는 과정의 핵심 과제다.

간략하게 생성형 모델의 역사를 들여다보면서, 어떤 모델이 좋은 모델인지에 대해서도 알아보자.

![Diffusion model과 GAN 모델의 비교](https://cdn.neowin.com/news/images/uploaded/2021/05/1621148897_output.jpg){: .align-left}
(출처: https://cdn.neowin.com/news/images/uploaded/2021/05)

위는 이미지 생성 모델의 결과이다. 어떤 결과가 더 좋은 결과일까? 여기서 보여주고자 하는 것은 이미지의 질이 아니다. 오른쪽으로 갈수록, 같은 대상에 대해 다양한 이미지가 생성된다는 것을 볼 수 있다.
왼쪽은 GAN, 오른쪽은 diffusion 모델이다. 더 다양한 이미지를 보여주는 diffusion model이 더 최신의 architecture이고, 생성형 모델에서는 하나의 class에 대해 다양한 이미지가 생성될 수 있는 것이 favorable하다.

explicit, implicit model로 생성형 모델을 분류할 수도 있다. 위에서 언급한 트레이닝 샘플의 분포를 나타내는 확률밀도함수를 직접 수식으로 정의하고 근사하는 종류의 모델들이 explicit model이다. 수식을 명시적으로(explicitly) 정의하기 때문이다. 반면에 수식을 정확히 정의하지는 않으나, 어쨌든 학습 과정에서 확률밀도함수를 추정하게 되는 종류의 모델도 있다. 이를 implicit model이라고 하고, GAN이 이에 해당한다.

생성형 모델을 평가하는 방법은 여러가지가 있을 수 있는데, 우선 생성된 이미지의 품질을 따질 수 있다. 그런데 품질을 어떻게 평가할 수 있을까? 좋은 품질의 이미지라면, 특정 클래스에 속할 확률이 명확하게 높아야 한다. 예를 들어 가방에 대한 이미지를 생성했는데 해당 이미지가 품질이 뛰어나다면 쉽게 가방으로 분류되어야 한다는 뜻이다. 그런데 가방 이미지를 모두 똑같이 생성한다면, 좋은 모델이 아니다. 따라서 클래스 하나에 속하는 이미지에 대해서는 넓은 분포를 가져야 한다. 또 다른 방법으로는 생성된 이미지의 분포와 실제 이미지의 분포 간 유사도를 비교해볼 수도 있다.

이를 정량화하는 여러가지 metric이 있고, inceptrion score나 Frechet inception distnace 등이 그 예시이다.
