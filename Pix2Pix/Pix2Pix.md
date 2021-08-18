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
