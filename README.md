# VDSR : https://cv.snu.ac.kr/research/VDSR/

#### <I studied while referring to various sites, but it is not enough. Thanks anytime for feedback.>
### <heejo5@naver.com>

Accurate Image Super-Resolution Using Very Deep Convolutional Network
---------------------------------------------------------------------

* VDSR은 Image-net 분류에 사용된 Vgg-net에서 영감을 받아 깊은 CNN을 사용
* 큰 Receptive  필드를 사용하고자 계산량의 증가를 막기위해 zero padding을 추가하여 사용
* Residual-learning학습 방법을 사용하였고 SRCNN과는 다르게 다양한 scale factor를 사용해 학습시켜 어떤 Scale Factor값도 SR할 수 있게 만듦

SRCNN과 VDSR 비교
----------------
![image](https://user-images.githubusercontent.com/61686244/94897100-f0cf7f00-04c9-11eb-9dc6-13741520d78d.png)

VDSR Architecture
-----------------
![image](https://user-images.githubusercontent.com/61686244/94897171-0e9ce400-04ca-11eb-8883-921b10acfede.png)
* 첫 번째와 마지막 레이어를 제외하고 같은 D레이어, 3x3 64개의 채널을 사용하였으면 
* 첫번째 레이어는 입력 이미지연산, 마지막 레이어는 이미지 재구성에 사용
* 차원을 줄이는 pooling과 같은 방법은 사용하지 않았으며 Residual learning을 위해 skip connection이라는 개념을 도입하였으며 각층마다 출력 이미지가 줄어드는것을 방지하기위해 convolution전에 zero padding을함
* 마지막으로 Network를 거쳐 Residual Img가 생성된것과 입력으로 넣어준 ILR 이미지를 더하여 최종 HR이미지를 생성

Residual Learning
-----------------
![image](https://user-images.githubusercontent.com/61686244/94897841-69830b00-04cb-11eb-82b3-f6d59a639c16.png)

Adjustable Gradient Cliping
---------------------------
![image](https://user-images.githubusercontent.com/61686244/94898037-d0a0bf80-04cb-11eb-9d20-af491af5bf6f.png)

Performance table for residual and non-residual
-----------------------------------------------
![image](https://user-images.githubusercontent.com/61686244/94898091-e9a97080-04cb-11eb-9f04-09036e52008f.png)

Depth VS Performance
--------------------
![image](https://user-images.githubusercontent.com/61686244/94898192-1b223c00-04cc-11eb-9cfc-9a884942c274.png)

Performance curve  for residual and non-residual 
------------------------------------------------
![image](https://user-images.githubusercontent.com/61686244/94898324-56246f80-04cc-11eb-8f35-45a4b6549104.png)

Scale Factor Experiment
-----------------------
![image](https://user-images.githubusercontent.com/61686244/94898443-8bc95880-04cc-11eb-8047-b2f016b4af6a.png)

Average PSNR/SSIM
-----------------
![image](https://user-images.githubusercontent.com/61686244/94898483-9be13800-04cc-11eb-8dde-85d08f95ada7.png)
![image](https://user-images.githubusercontent.com/61686244/94898523-abf91780-04cc-11eb-8772-845bd1a19805.png)

Conclusions
-----------
* VDSR은 image-net 분류에 사용된 vgg-net에 영감을 받아 깊은 CNN을 사용(20 Layers)
* 작은 필터를 깊은 네트워크에 연속적으로 많이 거치면서 효율적으로 유의미한 정보 추출 
* VDSR은 깊은 네트워크의 복잡한 계산 문제를 Residual Learning으로 해결
* Adjustable Gradient Clipping을 이용하여 Learning Rate를 올려 학습 속도 상승
* VDSR은 이전의 방법보다 정확도와 선명도가 높음



