---
layout: portfolio_with_preview
tags: [개인 프로젝트, 도구]
thumbnail: BaseballVision.png
summary: "🔧 &#10;🌟 인체구조 시각화&#10;🎮 상태: 진행중"
preview: <iframe frameborder="0" src="https://underhand-lab.github.io" allowfullscreen="" width="300" height="500"></iframe>
social:
  - title: github
    info: Code
    url: https://github.com/Easy-H/BaseballVision
  - title: edge
    info: App
    url: https://underhand-lab.github.io
---

<!-- card:💡 프로젝트 개요 -->

스마트폰으로 촬영한 영상을 기반으로 일반인도 야구 훈련 데이터를 쉽게 얻을 수 있는 웹 애플리케이션 개발 프로젝트입니다. 이 프로젝트는 AI 도구 Gemini를 이용하여 개발하였습니다.

<!-- card: 🔧 기능 (Developments) -->

### 자세 인식
- MideaPipe를 이용하여 영상 속 인물의 자세를 인식합니다.
- 관절의 각도 정보를 추출하여 힘의 사용이 효율적인지 확인을 돕습니다. 
- 관절의 속도 정보를 추출하여 힘의 사용 시작 시점 확인을 돕습니다.
- 관절의 높이 정보를 추출하여 선수에게 적합한 자세 확인을 돕습니다.

<!-- card: 🔧 기능 (Developments) -->
### 공 궤적 인식
- YOLO의 객체 인식을 이용하여 영상에서 공을 추적합니다.
- 지면 대비 공의 이동 각도를 분석합니다.
- 공의 크기를 기반으로 공의 이동 속도를 추측합니다.
- 추출되는 정보는 공이 촬영자 기준으로 전후 운동을 하지 않는다고 가정한 결과입니다.
	- 촬영 환경이 그렇지 않다면 지면 대비 각도는 더 크게, 공의 속도는 더 느리게 출력됩니다.

<!-- card: 🛠️ 기여 -->

### 🔥 리팩토링: 모듈화
- 개선 전: 기존에는 동영상 이미지 추출과 자세 인식, 객체 인식과 인식 내용 기반의 정보 추출이 통합
	- 자세 인식, 객체 인식 라이브러리 수정 시 큰 개발 비용 소모
	- 새로운 정보 추출 개발 시 중복 개발이 필요
- 개선 후: 동영상 이미지 추출, 자세 인식, 객체 인식과 인식 내용 기반의 정보 추출을 모듈화하여 분리
	- github 블로그를 이용한 웹 앱 배포시 Shared Array Buffer를 사용 못하여 오류가 생기던 것을 해결
		- Shared Array Buffer를 사용하지 않고 동영상 이미지 추출을 수행하는 클래스 개발을 통해 배포 성공
		- 기존의 Shared Array Buffer를 이용하는 방법은 다른 플랫폼에 배포 시 사용하여 플랫폼에 적절한 기능 제공이 가능해짐
	- 객체 인식, 자세 인식 라이브러리 수정 시 유연성 확보
	- 새로운 정보 추출 기능을 효율적으로 추가
		- 관절의 속도, 높이 분석 기능 추가
		- 공의 지면 대비 각도 계산 기능 추가