# 파손 차량 사진을 통한 수리비 예측

#### 프로젝트 소개 

기간 | 2023.03.31 ~ 2023.04.21
------------|---------
인원 | 김도현, 김은성, 김주은, 박진성 
목적 | 객체인식을 이용해 경미한 파손을 당한 차량의 사진을 찍어서 올리는 것 만으로도 수리비 견적을 예측해주는 딥러닝 모델을 이용한 서비스 제시
역할 | **조장**, 전체 일정 조율 및 업무 분담 ,데이터 분석 및 전처리 과정, 모델 성능 개선, 데이터 후처리 과정 전담, PPT제작 및 발표
사용 | Python, Google Colab, Roboflow, Yolo v8, 이미지 전처리(crop, zero-centering, re-size,...)
참고 |  [Yolo v8 github](https://github.com/ultralytics/ultralytics)


상세 내용은 [해당 링크](https://resonant-mapusaurus-297.notion.site/4e3945f73b1d4d078bda4e217114b8fa?pvs=4)에서 확인 가능

**프로젝트 구성도**

> **Input : 차량 손상 부위 사진 → Output : 차량 수리비**

- 사용자가 차량의 손상 부위를 촬영한 사진과 사고 차량 종류 입력
- 이미지 데이터를 각 차량 부위 및 파손 종류를 예측하는 `Yolo v8` 모델에 입력
- 두 모델의 결과값을 후처리
- 후처리 값과 차량 부품가격 정보를 이용하여 최종적으로 예상 차량 수리비 예측
<br>

#### repo 구성

- utils 
    - 이미지 전처리, labeled 데이터 전처리 등 에 필요한 코드

- data
    - 차량 수리비 예측에 사용할 차량 부위 가격 및 차량 종류에 따른 차량 가격 데이터

- yolo_v8_train.ipynb
    - colab 환경에서 yolo v8 train 코드
    - dataset은 roboflow를 통해 aug한 뒤 업로드 하여 사용

- postprocessing_infer.ipynb
    - 학습된 모델을 통하여 수리비를 예측하는 후처리 과정을 담은 코드
