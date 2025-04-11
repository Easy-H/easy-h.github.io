---
layout: portfolio_game
tags: [개인 프로젝트]
thumbnail: CrossNumber.png
summary: "🔧 Unity | Firebase&#10;🌟 퍼즐&#10;🎮 상태: 완료"
iframe: <iframe frameborder="0" src="https://itch.io/embed-upload/11880307?color=333333" allow="autoplay; fullscreen" width="300" height="470"><a href="https://easy-h.itch.io/crossnumber">Play Cross Number on itch.io</a></iframe>
social:
  - title: github
    info: Code
    url: https://github.com/Easy-H/CrossNumber
  - title: itch-io
    info: Play
    url: https://easy-h.itch.io/crossnumber
---

<!-- card: 개요 -->
### ✨ 장르: 수식 기반 퍼즐
### 🛠 사용 도구
- Unity
- Firebase Firestore
### 👤 담당
- 게임 기획
- 프로그래밍

<!-- card: 개요 -->
## 🧠 게임 개요
**Cross Number**는 숫자와 연산 기호를 조작해 올바른 수식을 만드는 퍼즐 게임입니다.  
화면에 주어진 수식들이 모두 올바르게 되도록 퍼즐을 해결하면 클리어됩니다.

- **모든 수식의 오류를 수정하면 스테이지 클리어**
- 직관적 드래그 앤 드롭 인터페이스로 수식 수정
- 레벨 편집 및 공유 기능 탑재

<!-- card: 시스템 -->
## 🧩 시스템 구성

### 🎮 퍼즐 플레이

- 격자 형태로 구성된 수식을 수정하여 완성
- 실시간 오류 검사 및 피드백
- 정답 검증 로직과 시각적 효과 포함

### 🛠 사용자 레벨 제작 및 업로드

- 에디터를 통해 숫자/기호 배치 후 직접 플레이로 검증
- 클리어에 성공한 퍼즐만 업로드 가능
- 현재는 Firestore에 저장된 퍼즐 중 무작위 선택 후 플레이 가능

<!-- card: 데이터 구조 -->
## ☁️ Firebase Firestore 구조

<!-- card: 데이터 구조 -->
### 📁 MapId 컬렉션

- 레벨을 식별하는 외부용 정보
- key-value 쌍으로 MapData의 위치와 이름을 보유

```plaintext
Collection: MapId
 └── Document ID: 랜덤 코드 (예: "X8PQ4")
       ├── key: "ABC123"       ← MapData 문서 ID
       └── name: "곱셈 연습 맵"
```

<!-- card: 데이터 구조 -->
### 📁 MapData 컬렉션
- 실제 퍼즐 구성 데이터 저장
- 각 퍼즐 유닛을 번호(key)로 나열한 구조
```plaintext
Collection: MapData
 └── Document ID: ABC123
       ├── "0":
       │     ├── xPos: 0
       │     ├── yPos: 0
       │     └── Symbol: "*"
       ├── "1":
       │     ├── xPos: 1
       │     ├── yPos: 0
       │     └── Symbol: "5"
       └── ...
```

<!-- card: 추가 계획 -->
### 🔐 유저 시스템 설계 (예정)
- 추후 Firebase Authentication을 도입할 경우:
  - UserData 컬렉션 추가
  - 유저가 만든 MapId 코드 리스트 보관
  - 맵 수정/삭제 권한 부여 가능
  - 즐겨찾기, 추천, 신고 기능 확장 고려

<!-- card: 회고 -->
## 🌱 회고 및 기술 포인트
- 실질적 사용자 제작 콘텐츠(UGC)를 구성하고 검증하는 시스템 설계 경험
- Firebase Firestore의 컬렉션/문서 기반 데이터 구조를 분리 설계하여 확장성 확보
- 익명 사용 환경에서의 데이터 식별 및 공유 흐름 설계