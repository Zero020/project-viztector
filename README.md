# Viztector: 키포인트 기반 객체 탐지 모델을 이용한 데이터 시각화 왜곡 탐지 및 교정 시스템 개발

> 2024.04-2024.06

<br>

## Index

1. [Overview](#-overview)
2. [How to Run](#-how-to-run)
3. [Flow](#-flow)
4. [Tech Stack](#-tech-stack)
5. [Member](#-member)
6. [Publication](#-publication)

<br>

## 🔎 Overview

오늘날 데이터 시각화는 빅데이터 분석에서 중요한 의사결정 도구로 활용되며, 광고, 마케팅, 뉴스 보도 등 다양한 분야에서 사용되고 있다. 그러나 그래프는 제작자의 의도에 따라 쉽게 변형될 수 있어 왜곡의 위험이 존재하며, 이는 소비자나 사용자에게 잘못된 정보를 제공해 오해를 초래할 수 있다. 본 연구에서는 이러한 문제를 해결하기 위해 왜곡된 차트를 탐지하고 교정된 차트를 제공하는 시스템을 제안하였다. 제안된 시스템은 Hourglass 네트워크 기반의 keypoint 객체 탐지 모델을 활용하여 막대, 선, 원 그래프 유형에서 시각적 요소의 위치를 추출하고, 이를 바탕으로 왜곡을 탐지하고 교정하는 알고리즘을 적용하였다. 실험 결과, 그래프 탐지 검증 정확도는 98%의 우수한 성능을 보였다. 구현 결과 다양한 웹 시각 자료에서 높은 정확도로 왜곡을 탐지하고 교정된 결과를 제공하여 데이터 시각화의 신뢰성을 크게 높일 수 있을 것으로 기대한다.

<br>

<img width="541" height="385" alt="화면 캡처 2026-01-07 180057" src="https://github.com/user-attachments/assets/12194465-76f4-43ab-82e1-f0844a54a486" />

<br>
<br>

## 🚀 How to Run

[ChartReader](https://github.com/zhiqic/ChartReader), [korean_ocr_using_pororo](https://github.com/black7375/korean_ocr_using_pororo)
기반 그래프 왜곡탐지 모델

### 콘다 가상환경 설정

~~~
conda create -n Viztector python=3.7.13
conda activate Viztector
~~~

### 패키지 및 Pororo 설치

~~~
pip install -r .\requirements.txt
git clone https://github.com/kakaobrain/pororo.git
cp ./pororo_setup.py ./pororo/setup.py
cd pororo
pip install -e .
~~~

cache/nnet/KPGrouping 안에 KPGrouping_best.pkl 파일 설치  
https://drive.google.com/file/d/11Z6cNl-5dcpbuDq9N_ZrB7rPUoJvAH_u/view?usp=drive_link  
  
### 모델 테스트  

img/images/val 안에 테스트 이미지 복사후  
detection_test.ipynb 실행  
  
### 왜곡 탐지  

correction_test.ipynb 실행  

### 익스텐션 사용
서버 실행  
~~~
python server.py  
~~~
크롬 익스텐션 설치  
~~~
확장 - 확장 관리 - 압축 풀린 파일 로드 - Viztector_CE 폴더 선택
Image and Video Capture Extension
Start 버튼 클릭후 이미지 클릭
~~~

<br>

## 🏴 Flow

<img width="1920" height="1080" alt="" src="https://github.com/user-attachments/assets/f7288dad-e025-42cd-8cd3-8427b45edac0" />
<img width="1920" height="1080" alt="" src="https://github.com/user-attachments/assets/af18d079-9af9-4f47-b1e7-88813d4d0d90" />
<img width="1920" height="1080" alt="" src="https://github.com/user-attachments/assets/60caa2e0-d518-4ae1-bca2-abc2f2cb9de5" />
<img width="1920" height="1080" alt="" src="https://github.com/user-attachments/assets/0b4610c4-d4f5-4960-bf35-da314cdc28e6" />

---

### Chrome extension 기능
1. **Start 버튼** 이미지 클릭시 서버로 이미지 전송  
2. **Capture 버튼** Start 버튼 클리후 활성 웹페이지내 Video 화면을 이미지 데이터로 변환하여 서버로 전송
3. **Reset 버튼** 이벤트 리스너 및 저장된 CSV 데이터 삭제  
4. **Download 버튼** 서버에 업로드된 데이터 CSV파일로 다운로드  

<br>

## 🔧 Tech-Stack
- MobileNetV2: 각 1500개씩 이루어진 그래프와 그 외 사진들
- ChartReader: 약 11만개의 그래프 데이터로 이루어진 EC400K
- Azure OCR: 그래프 이미지 내 글자 인식
- Algorithm: 그래프 왜곡 탐지 및 교정
- Data Preprocessing:  MicrosoftOCR
- Chrome Extension: Visual studio Code , 소켓통신 서버
- Model: Jypyter , Google Colab
- Communicationm&Task Share : Canvas, Notion
- Total Project Result : Github

<br>

## 👥 Member
> 7명

<br>

### My task
 1. 크롤링
 2. 파이 그래프, 끊긴 물결 막대 그래프의 교정 알고리즘 개선 시도
 3. 이전 데이터셋의 전처리
 4. 크롬 익스텐션 구현

<br>

## 📄 Publication

**Title:** Development of a Data Visualization Distortion Detection and Correction System using a Keypoint-based Object Detection Model

**Journal:** Journal of the Korean Institute of Information Technology (KIIT), Vol. 23, No. 1, pp. 177-190, Jan 2025

**Role:** 3rd Author (최영 / Young Choi)

**Status:** Published

#### [논문 바로가기](https://www.ki-it.com/_PR/view/?aidx=43812&bidx=3952)
