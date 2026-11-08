# ClassCents — 기능·흐름·상태

## 핵심 기능

- Currency config
- Roster import
- Jobs
- Payday
- Give/Deduct
- Reason presets
- Groups
- Shop
- Inventory
- Savings/Goals
- Badges
- Leaderboard
- History/Undo
- Export
- Optional student login

## 주요 상태/흐름

- Job assignment/completion→Payday
- Purchase: balance/cost/new balance→redeem
- Goal: current/target/remaining
- Teacher-only vs Student-self-service mode

## 기능 연결 원칙

학생 로그인이 없어도 교사 혼자 완주할 수 있고, 필요할 때만 학생 self-service를 추가하는 이중 운영모드.

기능을 독립 체크리스트로 보지 않고 다음 질문으로 연결해서 본다.

1. 이 기능이 어떤 객체/상태를 만든다.
2. 그 상태가 다른 기능의 사용 가능 여부를 바꾸는가.
3. 자동화가 실행되면 사용자에게 무엇이 보이는가.
4. 실패하면 어느 화면에서 다시 처리하는가.
5. 정정 시 원래 기록과 연결 상태가 어떻게 유지되는가.
