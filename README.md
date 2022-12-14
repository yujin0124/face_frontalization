# face_frontalization
영상 처리 기법을 이용한 얼굴 정면화 연구
### 연구 배경
코로나19의 유행으로 인해 화상 회의 프로그램의 사용이 증가하였다. 화상 회의 프로그램을 사용하면 카메라의 위치에 따라 사용자가 정면을 보고있지 않는 것처럼 보일 수 있다. 이때 카메라의 위치에 상관없이 정면을 바라보는 것처럼 만들 수 있다면 더 생생한 경험을 제공할 수 있을 것이라 생각하여 얼굴 정면화에 대해 연구하게 되었다.


### 관련 연구
#### OpenCV
* 오픈소스 컴퓨터비전 라이브러리
* 영상을 다양하게 변환하는 기하 변환 관련 기능을 함수의 형태로 제공
#### Haar Cascade, Dlib library
* 얼굴 감지와 특징점 추정 기능을 제공


### 제안 연구
기존의 얼굴 정면화는 주로 딥러닝 기술을 이용하고 있다. 주로 생성적 적대 신경망을 통해 학습을 진행하여 좋은 결과를 내고 있다. 그러나 딥러닝을 사용하면 시간이 오래 걸리고 학습을 위한 영상 데이터가 많이 필요하다. 따라서 영상 처리 기법을 사용하여 간단하게 얼굴 정면화를 구현해보기로 하였다.


### 연구 내용
#### Solution 1. 정면 영상을 이용하는 방법
정면 영상의 특징점과 돌아간 얼굴 영상의 특징점 간의 변환 행렬을 구해 그것으로 변환하는 가장 간단한 방법이다.
##### 결과
<img width="664" alt="sol1" src="https://user-images.githubusercontent.com/38284326/205492384-9b8c6e64-8fa9-4dea-a8fd-58540fb9fa89.png">

* 결과물이 찌그려져 보이는 문제가 발생
* 정면 영상이 필요함


#### Solution 2. 정면의 일반적인 특징을 이용하는 방법
Solution 1의 문제를 해결하기 위한 방법이다. 이목구비가 코를 중심으로 대칭을 이루고 콧대가 일직선인 정면의 일반적인 특징을 반영하는 점들을 만들어 변환 행렬을 구하고 변환한다.
#### 결과
<img width="665" alt="sol2" src="https://user-images.githubusercontent.com/38284326/205492573-9346eea5-9c83-49b4-b9e2-ea10ed433ede.png">

* 얼굴이 넓어지는 문제가 발생


#### Solution 3. 3차원 회전을 이용하는 방법
Solution 2의 문제를 해결하기 위한 방법이다. 2차원 영상을 3차원으로 매핑, 회전, 2차원으로 변환한다.
#### 결과
<img width="665" alt="sol3" src="https://user-images.githubusercontent.com/38284326/205492678-fbaaa811-0ab6-4eaf-9ecf-93f71dfe0f98.png">

* 완전하진 않으나 전과 비교하여 개선되었음


### 출처
dlib의 특징점 추정에 사용한 shape predictor dat파일
https://osdn.net/projects/sfnet_dclib/downloads/dlib/v18.10/shape_predictor_68_face_landmarks.dat.bz2/
