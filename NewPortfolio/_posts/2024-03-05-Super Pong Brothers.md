---
layout: portfolio_game
tags: [개인 프로젝트]
thumbnail: SuperPongBros.png
summary:  "🔧 Unity | Firebase&#10;🌟 벽돌깨기, 슈팅&#10;🎮 상태: 완료"
iframe: <iframe frameborder="0" src="https://itch.io/embed-upload/11887825?color=333333" allow="autoplay; fullscreen" width="220" height="500"><a href="https://easy-h.itch.io/superpongbros">Play Super Pong Bros on itch.io</a></iframe>
social:
  - title: github
    info: Code
    url: https://github.com/Easy-H/Break-Out
  - title: itch-io
    info: Play
    url: https://easy-h.itch.io/superpongbros
---
<!-- card: 개요 -->

## 💡 게임 개요

**✨ 장르**
- 벽돌깨기 + 슈팅

**🛠 사용 도구**
- Unity
- Firebase Realtime Database

**👤 담당**
- 게임 기획
- 프로그래밍

<!-- card: 개요 -->
## 📖 게임 소개
**Super Pong Brothers**는 벽돌깨기와 슈팅 게임을 융합한 아케이드 스타일의 점수 경쟁 게임입니다.  
총알을 쏘는 적을 공으로 맞추어 쓰러뜨리는 것이 기본적인 전투 방식입니다.

- **모든 공을 떨어뜨리면 피해를 입음**  
- 반대로, **피해를 입으면 공이 추가로 발사**되어 전략적으로 피해를 활용할 수 있음  
- 항상 하나 이상의 공이 필드에 있도록 설계된 시스템으로 **공 = 생존 리소스**라는 콘셉트 확립

<!-- card: 시스템 -->
## 🧩 시스템
### 🎯 피해 ↔ 공 리소스 설계

- 체력을 잃을 때마다 공이 하나씩 발사되며, 떨어진 공이 많을수록 생존 리스크가 커짐
- 플레이어가 **일부러 피해를 감수하고 다공 공격을 시도할 수 있는 전략적 설계**

### 📈 점수 기반 페이즈 전환

- 점수가 일정 기준 이상일 경우, 퀘스트가 자동으로 달성되고 다음 페이즈로 전환
- 각 페이즈는 등장하는 적의 종류 및 공격 패턴이 달라지며 난이도가 점진적으로 증가

<!-- card: 시스템 -->

### 🗂 퀘스트 & 페이즈 데이터 관리

- **ScriptableObject**를 이용해 퀘스트 조건과 페이즈 데이터 분리 관리
- 게임 밸런스를 코드 수정 없이 빠르게 조정 가능

### ☁️ Firebase 연동

- 게임 종료 후 Firebase Realtime Database에 **점수 저장**
- 추후 스코어보드 및 랭킹 기능 확장 가능성 확보