# HexaBlast

## 페이지 구성

- Lobby page
  - Title text
  - Start button
  - Quit button
- Ingame page
  - Ingame UI
    - Score text
    - Timer gauge image
  - GameManager
    - Frame area
        - Frame
    - Block area
        - Block
    - Guide area
        - Guide
- Result popup
  - Result test
  - Restart button
  - Exit button

## 게임 로직

- 게임 전체 로직
  - 타이머 게이지 0 되면 게임 오버
    - [ ] 영상 시청 후 1회 부활 가능
  - 매칭시
    - 타이머 게이지 초기화
    - 스코어 증가
    - 드롭
  - [ ] (진행중)일정 시간 매칭 안할 경우 가이드 보여주기 → 이러면 게임오버 안될듯
  - [ ] 매칭 불가능 상태면 자동 셔플 → 이러면 게임오버 안될듯
  - [ ] 일정 시간마다 쓰레기 생성
- 드롭
  - 아래/좌우로 흘러내리도록 처리
  - 신규 블럭 입구에 설정
  - 신규블럭 랜덤 타입 설정
  - 전체 드랍 종료 후 매칭 체크
- 블럭
  - 기본블럭 : BlockType.Color들
    - 매칭 조건 : 동일 색상 직선 3개 이상 모일 경우
    - 스왑 후 매칭되면 사라짐
    - 스왑 후 매칭 안되면 원래 자리로
  - 쓰레기 : BlockType.Garbage
    - 주변에서 1차 매칭 : 색상 Gray로 변함
    - 주변에서 2차 매칭 : 사라짐
  - 아이템
    - [ ] 방향라인제거 아이템 : 직선 4개
    - [ ] 전체제거 아이템 : 직선 5개
- 기타/예외처리
  - 스왑 막기 : Touchdisabled 일 때
  - 타이머 동작 : Touchdisabled 아니고 게임오버 아닐 떄

## 구현 방법 정리(점검 필요, 업데이트 예정)

- 드롭 알고리즘
  - 제거된 블럭은 큐에 담았다가 드롭시켜 재사용
  - 아래쪽 프레임 인덱스부터 돌면서 아래 셋 중 하나 해당하면 해당 위치로 이동
    - 내 아래쪽 비었음
    - 왼쪽아래 비었음 + 왼쪽위 블럭이 이동불가
    - 오른쪽아래 비었음 + 오른쪽위 블럭이 이동불가

