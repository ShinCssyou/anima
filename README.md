<div align="center">

# 🫁 ANIMA

### AI 기반 개인 맞춤형 기침 음향 패턴 변화 기록 시스템

**A Normal-Distribution-Based System for Recording Changes in Personalized Cough Acoustic Patterns**

<br>

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![Flutter](https://img.shields.io/badge/Flutter-02569B?style=flat-square&logo=flutter&logoColor=white)
![AI](https://img.shields.io/badge/AI-Cough%20Analysis-6C63FF?style=flat-square)
![Healthcare](https://img.shields.io/badge/Healthcare-Research-2E8B57?style=flat-square)

<br>

> **기침을 기억이 아닌 데이터로.**

</div>

---

## 📌 프로젝트 소개

**ANIMA**는 사용자의 기침 음향을 분석하여  
기침 여부, 녹음 품질, 연구용 참조 분포 대비 음향 패턴의 차이를 기록하고  
시간에 따른 변화를 확인하기 위한 **AI 기반 헬스케어 연구 프로젝트**입니다.

단순히 한 번의 기침을 판별하는 데서 끝나는 것이 아니라,  
같은 사용자의 기침 기록을 지속적으로 누적하여  
**기침 음향 패턴이 시간에 따라 어떻게 변화하는지 확인하는 것**을 목표로 합니다.

---

## 🎯 프로젝트 목표

- 🎙️ 사용자의 기침 음성 기록
- 🔊 녹음 품질 확인 및 전처리
- 🤖 AI 기반 기침 여부 판별
- 📐 연구용 건강 기침 참조 분포와 비교
- 📊 Mahalanobis Distance 기반 이탈도 계산
- 🗓️ 날짜별 기록 저장
- 📈 장기적인 기침 패턴 변화 시각화
- ⌚ 웨어러블 기기와 연동 가능한 구조 설계

---

## 🔍 분석 흐름

```text
사용자 기침 녹음
        ↓
음성 전처리
(16kHz Mono / 잡음 / 클리핑 확인)
        ↓
STFT / Spectrogram 특징 추출
        ↓
AI 기반 기침 여부 판별
        ↓
연구용 건강 기침 참조 분포와 비교
        ↓
Mahalanobis Distance 계산
        ↓
이탈도 및 분석 결과 저장
        ↓
날짜별 히스토리 / 그래프 시각화
```

---

## 🧠 주요 분석 지표

| 지표 | 설명 |
|---|---|
| **Cough Confidence** | AI 모델이 입력 음성을 기침으로 판단한 신뢰도 |
| **Quality Score** | 녹음 길이, 잡음, 클리핑 등을 반영한 입력 음성 품질 지표 |
| **Deviation** | 연구용 참조 분포와 현재 기침 음향 특징 간의 통계적 차이 |
| **Mahalanobis Distance** | 평균과 공분산을 고려하여 참조 분포와의 거리를 계산하는 방식 |

> **주의:** Deviation과 Mahalanobis Distance는 질병 위험도나 중증도를 의미하지 않습니다.

---

## 🗄 데이터 구성

ANIMA는 단순히 AI 분석 결과만 저장하지 않고  
측정 당시의 사용자 및 환경 정보도 함께 기록하는 구조를 목표로 합니다.

- 녹음 날짜 및 시간
- 기침 감지 여부
- 기침 판별 신뢰도
- Quality Score
- Mahalanobis Distance
- 이탈도
- 복약 여부
- 주관적 기침 빈도
- 통증 정도
- PM10 / PM2.5 등 환경 정보
- 사용된 참조 분포 및 모델 버전

---

## 📚 Reference Data

초기 연구 단계에서는 공개 기침 음향 데이터셋인 **COUGHVID**를 활용합니다.

COUGHVID에서 의료진이 검토한 `healthy_cough` 샘플을 기반으로  
연구용 건강 기침 참조 분포를 구성하고,  
사용자의 기침 음향 특징과 비교합니다.

향후에는 국내 사용자 데이터를 축적하여  
한국인 기침 음향 특성을 반영할 수 있도록 데이터셋과 모델을 고도화하는 것을 목표로 합니다.

---

## 🛠 Tech Stack

| 분야 | 기술 |
|---|---|
| 📱 Mobile | Flutter |
| 🖥 Backend | Python, FastAPI |
| 🧠 AI / Audio | STFT, Spectrogram, 2D CNN |
| 📐 Statistics | Mahalanobis Distance |
| 🗄 Database | Relational Database |
| 💾 Storage | Audio File Storage |
| ⌚ Hardware | Seeed Studio XIAO nRF52840 Sense |
| 📡 Communication | BLE |
| 🌐 Project Web | HTML, CSS, JavaScript |

---

## 🏗 System Architecture

```text
User
  │
  ▼
Flutter Mobile App
  │
  ▼
FastAPI Server
  │
  ├── Audio Preprocessing
  │
  ├── Quality Check
  │
  ├── Cough Detection AI
  │
  └── Deviation Analysis
  │
  ▼
Database / Audio Storage
  │
  ▼
History / Graph / Report
```

---

## 👥 Team ANIMA

| 이름 | 역할 |
|---|---|
| **주세희 (팀장)** | 기획, 문서 작업, 데이터 전처리, AI 모델 생성, 학술지 작성, IRB, 하드웨어 구현 |
| **이강민** | 서버 구축, 데이터 라벨링, 웹 제작 |
| **정해서** | UX/UI, DB 설계, Frontend, 웹 제작 |
| **신호철** | 데이터 라벨링, HTML 프로젝트 소개페이지 제작 |
| **임태희** | 웹 디자인, 가이드 제작, 사용성 피드백 |

---

## 🚧 현재 프로젝트 단계

현재 ANIMA는 **연구·교육 목적의 프로토타입** 단계입니다.

### 완료 / 구현 중

- ✅ 모바일 앱과 AI 분석 서버 기본 연동
- ✅ 에뮬레이터 환경에서 시스템 동작 확인
- ✅ 기침 분석 파이프라인 설계
- ✅ 데이터베이스 및 기록 구조 설계
- 🔄 기침 음향 데이터 라벨링
- 🔄 AI 모델 성능 개선
- 🔄 웹 소개페이지 제작
- 🔄 웨어러블 하드웨어 구현
- ⬜ 국내 사용자 기침 음향 데이터셋 확대
- ⬜ 의료기관 협업 및 추가 검증

---

## 🌱 기대 효과

ANIMA는 충분한 검증과 연구 절차를 거친 뒤 다음과 같은 방향으로 확장될 수 있습니다.

- 개인의 장기적인 기침 기록 관리
- 복약 전후 변화 기록
- 비대면 상담 시 참고 가능한 구조화된 기록
- 요양 시설 및 생활 환경에서의 기침 이벤트 기록
- 한국인 기침 음향 데이터 연구 기반 구축
- 웨어러블 기반 일상 음향 모니터링 연구

---

## ⚕️ Medical & Research Notice

> **ANIMA는 현재 특정 질환을 진단하거나 치료하기 위한 의료 서비스가 아닙니다.**

ANIMA에서 제공하는 기침 감지 신뢰도, Quality Score,  
Mahalanobis Distance 및 이탈도는  
기침 음향 패턴을 기록하고 비교하기 위한 **연구용 지표**입니다.

따라서 이탈도가 높다고 해서 특정 질환이 존재하거나  
건강 상태가 나쁘다는 의미는 아닙니다.

지속적이거나 심한 기침, 호흡 곤란, 흉통 등 건강상 이상이 있는 경우에는  
ANIMA의 분석 결과와 관계없이 의료기관을 통한 전문적인 평가가 필요합니다.

---

## 🌐 Project Website

GitHub Pages 배포 후 아래 주소를 실제 프로젝트 주소로 변경하세요.

```text
https://YOUR-GITHUB-ID.github.io/YOUR-REPOSITORY-NAME/
```

예시:

```text
https://example-user.github.io/ANIMA/
```

---

## 📂 Repository Structure

```text
ANIMA/
├── README.md
├── index.html
└── ...
```

---

<div align="center">

### **ANIMA**

**Record · Compare · Accumulate · Review**

<br>

© 2026 ANIMA Team

</div>

