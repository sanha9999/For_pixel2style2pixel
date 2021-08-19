# Pix2Pix

나의 프로젝트를 위해 무엇을 공부해야할지 고민하다가, GAN에서 파생된 논문이 발표한 순대로 논문을 읽고 공부해보기로 하였다. Original GAN을 시작으로 DCGAN을 읽어봤는데, 중간에 있었던 CGAN과 CoGAN은 그렇게 비중이 큰 것 같지 않아서 Pix2Pix를 읽어보기로 하였다. Pix2Pix의 논문 제목은 "Image-to-Image Translation with Conditional Adversarial Networks"이다.

## 읽기전에...

Pix2Pix를 읽기전에 <https://affinelayer.com/pixsrv/> 이 링크를 타고 들어가 한번 체험해보는 것을 추천한다.
![](https://images.velog.io/images/sanha9999/post/d46de5d8-eaeb-46ff-a7c3-229758e4a7f8/image.png)<center><h6>실제로 그린 고양이..</h6></center>
아주 재미있는 체험을 해볼 수 있다.

## 구조

Pix2Pix의 기본 구조는 아래 그림과 같다.
![](https://images.velog.io/images/sanha9999/post/fb786030-8d33-404e-9e84-b646a02976ba/image.png)<center><h6>기본적인 Pix2Pix의 구조</h6></center>

그림에서 알 수 있듯이, Pix2Pix는 generator의 input으로 스케치 그림을 입력하면 완성된 그림이 나오도록 학습할 수 있는 것이다. 기존의 GAN은 noise (예를들면 DCGAN의 noise vector)를 사용하지만 Pix2Pix는 noise 대신 스케치 그림을 입력하여 학습을 하는 것이다.

자세히 살펴보면, input image x와 변환하고자 하는 목표인 y의 쌍 x, y를 이용해서 학습을 하는 것이다. 위의 그림에서 G(x)는 망을 학습시킨 후 망을 통하여 얻은 image중 하나이다.

그리고 Pix2Pix의 generator는 UNet의 구조를 사용하였는데, UNet은 encoder ~ decoder 구조에서 이미지의 크기를 줄였다가 다시 키우는 과정에서 detail이 사라지는 문제를 해결하기 위해 skip connection을 가진다.

![](https://images.velog.io/images/sanha9999/post/b3a734d5-cef9-48f0-a6c3-6f581920b700/image.png)

## 손실 함수

![](https://images.velog.io/images/sanha9999/post/04ca2479-d9dc-41c4-9478-0fc734447629/image.png)<center><h6>loss function에 따른 result</h6></center>

Pix2Pix의 특징은 다른 CNN을 사용하는 GAN과 손실함수가 다르다는 점이다. 대부분의 모델에서는 유클리디안 거리를 최소화되게 진행함으로써 나올 수 있는 결과의 평균을 선택하기 때문에 영상이 blurry한 row-frequency 이미지를 생성한다. 하지만 Pix2Pix는 GAN에 기반하기 때문에 
손실함수를 l1 loss만 사용하는 것보다 훨씬 더 좋은 결과를 얻을 수 있다.



> #### 유클리디안 거리(Euclidean distance)란??
 두 점 사이의 거리를 계산할 때 흔히 쓰는 방법으로, 우리가 아는 피타고라스의 정리를 생각해보면 되는데, 유클리디안 거리는 그보다 더 고차원인 n차원의 공간에서 두 점간의 거리를 알아내는 공식이라고 할 수 있다. 인공지능 분야에서는 두 개체 사이의 유사도를 구할 때 자주 사용한다.
 
 
 ## 결과
 
 ![](https://images.velog.io/images/sanha9999/post/4f3a288f-afcc-4b28-b3d5-04735161da1a/image.png)
 
 ![](https://images.velog.io/images/sanha9999/post/6b80cf4a-bccc-4463-8444-da9576bf9d55/image.png)
 
 
