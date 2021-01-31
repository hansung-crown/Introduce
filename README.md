# Introduce-CROWN

- Google의 Facenet 얼굴 인식 모델, OpenCV 손 제스처 인식 기술, 그리고 MQTT 프로토콜을 활용한 원격 제어 시스템

## System Architecture

<img src="https://user-images.githubusercontent.com/56067179/106384636-3fa50b00-640f-11eb-8542-4987f80248ac.gif" width="600">

- **라즈베리파이**
  - MQTT Mosquitto Broker
  - Video Streaming Server (UV4L)
  - Device Control
  
- **서버PC**
  - Face Recognition
  - Gesture Recognition
  - Download Image From Firebase Storage
  
- **사용자 애플리케이션**
  - Monitoring & Device Control
  - Upload Image To Firebase Storage



## Overview

1. **Upload Image To Firebase Storage (Total 40)**
    - 사용자 애플리케이션을 통해 Known 또는 Danger 그룹을 설정하고 얼굴 이미지 40장을 찍어 Firebase Storage에 업로드한다.

    <br/>
    <img src="https://user-images.githubusercontent.com/56067179/106384634-3caa1a80-640f-11eb-8278-68fbfc6ca7fd.gif" width="190" >
  
    <img src="https://user-images.githubusercontent.com/56067179/106386718-b6df9c80-6419-11eb-9809-c478a30e4e60.gif" width="600" >


2. **Align And Classify Face Data**
    - Firebase Storage로부터 이미지를 다운로드 받아 align한 결과를 output 디렉토리에 저장한다.
    - Pre-trained model(<a href="https://drive.google.com/uc?export=view&id=1akOzzDLc221LFBqVe5k9TYiT5sSNkUuo">20180402-114759</a>)에 output 디렉토리에 저장된 face data를 학습시켜 crown.pkl 모델을 생성한다.
  
    <br/>
    <img src="https://user-images.githubusercontent.com/56067179/106384635-3d42b100-640f-11eb-960d-e850ee371e6f.gif" width="600" >


3. **Start Recognition**
    - crown.pkl을 로드하여 실시간 얼굴 인식을 시작한다.

## Demo

- **Known 그룹** (초록색 이름)

  - 제스처 인식을 성공할 경우 도어락이 제어된다.
  <br/>
  <img src="https://user-images.githubusercontent.com/56067179/106384641-43d12880-640f-11eb-8d45-087cb685d693.gif" width="600" >

- **Danger 그룹** (빨간색 이름)

    <img src="https://user-images.githubusercontent.com/56067179/106384637-416ece80-640f-11eb-8e2b-a440a138b307.gif" width="600" >

- **Unknown 그룹** (하얀색 이름)

    <img src="https://user-images.githubusercontent.com/56067179/106384627-361ba300-640f-11eb-9062-d6e4353979ad.gif" width="600" >

## Other application example
- 전자 출결 시스템

  <img src="https://user-images.githubusercontent.com/56067179/106384633-3a47c080-640f-11eb-8c3c-d0d79b7cae32.gif" width="600" >
