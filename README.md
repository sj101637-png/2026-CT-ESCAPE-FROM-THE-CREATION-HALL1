# 2026-CT-ESCAPE-FROM-THE-CREATION-HALL1
option
컴퓨팅 사고 수업의 팀 프로젝트로 제작한 텍스트·이미지 기반 탈출 게임입니다.
플레이어는 창조관 내부를 탐색하며 선택지, 입력 문제, 가위바위보 미니게임 등을 통해 탈출을 시도하게 됩니다.

본 프로젝트는 HTML / CSS / JavaScript 만을 사용하여 구현되었으며,
장면(Scene) 기반 게임 엔진 구조를 직접 설계한 것이 특징입니다.

📁 프로젝트 구조
📦 창조관-탈출게임
 ┣ 📄 index.html     # 게임 화면의 기본 구조 (무대)
 ┣ 📄 style.css      # 게임 UI 및 레이아웃 디자인
 ┣ 📄 game.js        # 게임 시나리오 및 로직 (엔진)
 ┣ 📂 assets
 ┃   ┣ 📂 images     # 장면 이미지 (1.png, 2.png, ...)
 ┃   ┗ 📂 sounds     # BGM 및 효과음(mp3)
 ┗ 📄 README.md

1️⃣ index.html – 게임의 뼈대

index.html은 게임의 기본 무대(Stage) 역할을 하는 파일입니다.

주요 기능

게임 화면 이미지를 출력하는 영역

입력창 / 선택지 / 가위바위보 UI 영역 구성

JavaScript와 CSS 파일 연결

핵심 구성 요소

#game-container : 게임 화면 전체 영역

#game-screen : 장면 이미지 출력

#input-area : 텍스트 입력 문제 UI

#choice-area : (a)/(b) 선택지 UI

#rps-area : 가위바위보 미니게임 UI

<img id="game-screen" src="1.png" alt="게임 화면">


게임 진행 상황에 따라 각 UI는 JavaScript에서 동적으로 표시/숨김 처리됩니다.

2️⃣ style.css – 게임의 디자인

style.css는 게임의 전체적인 화면 구성과 분위기를 담당합니다.

디자인 특징

상단 85% : 게임 화면

하단 15% : 입력 및 컨트롤 패널

어두운 테마로 탈출 게임 분위기 강조

버튼 Hover 효과로 인터랙션 강화

핵심 포인트

Flexbox를 활용한 반응형 레이아웃

.hidden 클래스를 이용한 UI 제어

버튼별 색상 차별화로 직관적인 선택 유도

#input-area, #choice-area, #rps-area {
    position: fixed;
    bottom: 0;
    height: 15vh;
}

3️⃣ game.js – 게임의 두뇌 (시나리오 & 엔진)

game.js는 게임의 모든 흐름과 규칙을 제어하는 핵심 파일입니다.

⭐ Scene 기반 시나리오 구조

게임은 sceneConfig 객체를 중심으로 구성되어 있으며,
각 숫자(또는 문자열)는 하나의 장면(Scene) 을 의미합니다.

const sceneConfig = {
  1: { type: 'key', next: 2 },
  12: { type: 'input', choices: { 'no': 13, 'yes': '35-0' } },
  79: { type: 'choice', nextA: 80, nextB: 90 },
  110: { type: 'rps' },
  120: { type: 'end', message: "이젠 미래관을 탈출해보세요!" }
};

🎮 지원하는 Scene 타입
타입	설명
key	Enter 키 입력으로 다음 장면 이동
time	일정 시간 후 자동 전환
input	텍스트 입력 문제
choice	(a)/(b) 선택지
rps	가위바위보 미니게임
end	게임 종료 장면
🔊 사운드 시스템

BGM 재생 / 정지 / 페이드 인·아웃

효과음(SFX) 동시 재생

장면별 사운드 제어 가능

playBgm('hallway.mp3');
fadeOutBgm(2000);
playSfx('ban.mp3');

🧠 게임 엔진 특징

장면 번호에 따라 자동으로 이미지 변경

키보드 / 버튼 입력 통합 처리

히든 분기 및 힌트 루트 구현

미니게임 상태 저장 (가위·바위·보)

🚀 실행 방법

프로젝트 전체를 다운로드

이미지 및 사운드 파일 경로 확인

index.html 파일을 브라우저에서 실행

※ 크롬 브라우저 권장

🏫 제작 목적

컴퓨팅 사고 수업 팀 프로젝트

문제 해결 과정의 논리적 구조화

조건문·상태 관리·이벤트 처리 학습
