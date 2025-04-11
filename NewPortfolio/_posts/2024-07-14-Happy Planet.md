---
layout: portfolio_game
tags: [개인 프로젝트]
thumbnail: HappyPlanet.png
summary: "🔧 Unity | Firebase&#10;🌟 시뮬레이션 게임&#10;🎮 상태: 완료"
iframe: <iframe frameborder="0" src="https://itch.io/embed-upload/12321361?color=333333" allowfullscreen="" width="300" height="500"><a href="https://easy-h.itch.io/happy-planet">Play Happy Planet on itch.io</a></iframe>
social:
  - title: github
    info: Code
    url: https://github.com/team-prepper/happy-planet
  - title: itch-io
    info: Play
    url: https://easy-h.itch.io/happy-planet
---
<!-- card: 개요 -->

## 💡 게임 개요

**✨ 장르**
- 시뮬레이션
- 시간 조작

**🛠 사용 도구**
- Unity
- Firebase Firestore
- Firebase Realtime Database
- Firebase Authentication

**👤 담당**
- 전체 시스템 설계 및 개발
- UI 설계
- Firebase 연동

<!-- card: 개요 -->
## 📖 게임 소개 

**Happy Planet**은 다양한 유닛을 배치하고 시간의 흐름을 조작하며 자원을 관리하는 시뮬레이션 게임입니다.

행성을 직접 회전시켜 시간을 조작할 수 있으며, 이로 인해 유닛의 행동과 결과가 실시간으로 변화합니다.  

- 정방향 시간: 유닛이 작동하여 자원 생성  
- 역방향 시간: 과거 상태로 회귀하여 모든 행동과 자원이 되돌아감

<!-- card: 시스템 -->
## 🧩 시스템

### 🔧 유닛 관리

- 유닛 설치, 업그레이드, 삭제
- 각 유닛은 수명을 가지며, 수명이 만료되면 자원 생산 정지

### 🪐 행성 구조

- 여러 행성을 보유할 수 있음
- 각 행성은 독립된 유닛, 자원, 시간 상태를 가짐

<!-- card: 시스템 -->
### 🌀 시간 조작 시스템

- **정방향 회전**:
  - 시간 진행
  - 유닛 작동 → 자원 획득
- **역방향 회전**:
  - 시간 되감기
  - 자원 반납, 유닛 행동(유닛 설치, 업그레이드, 제거거) 취소
- 시간을 되돌린 후 새로운 행동이 없으면  
  → 기존 이벤트가 반복되는 리플레이 구조

<!-- card: 시스템 -->
## 🔁 로그 기반 시간 복원 구조

Happy Planet의 시간 시스템은 **데이터베이스 복구 시스템(WAL: Write-Ahead Logging)**에서 착안하여 구현되었습니다.

- **Firestore에는 유닛 이벤트만 기록**됩니다.
  - 기록되는 이벤트: `설치`, `업그레이드`, `삭제`
  - 자원 획득은 로그에 기록되지 않음 → 중복 발생 방지
- **Realtime Database에는 현재 시간과 자원 정보(MetaData)**를 관리합니다.
- 시간이 되감길 경우:
  - Firestore의 유닛 이벤트 로그를 시간 순으로 **재실행**
  - 자원은 MetaData를 기준으로 되감기된 상태를 **계산하여 복원**

<!-- card: 시스템 -->

## ☁️ Firebase 연동 구조

### 🔐 Firebase Authentication

- 유저는 Firebase 인증을 통해 식별됨
- UID를 기반으로 행성 및 데이터 기록

### 📁 Firestore

- 이벤트 로그 저장  
  예: `/Users/{UID}/Planets/{PlanetID}/Logs/{Timestamp}`
- 각 로그는 유닛 변경 이벤트만 포함 (자원 획득 제외)

### 📡 Realtime Database

- `/MetaData`에 현재 게임 시간 및 자원 상태 저장
- 정방향/역방향 시간 흐름, 유닛 상태 요약 정보 관리

<!-- card: 시스템 -->
## 🌐 소셜 기능

### ✈️ 행성 여행

- 다른 유저의 UID를 입력해 해당 유저의 행성을 관람 가능
- 관람 중에는 유닛 설치/삭제/시간 조작 불가능 (읽기 전용)
- Firebase Authentication의 UID를 기반으로 동작