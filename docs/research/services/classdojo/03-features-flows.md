# ClassDojo — 기능·흐름·상태

## 핵심 기능

- Student selector
- Group selector
- Skills
- Point events
- Notes
- Reports
- Undo
- Redeem
- Display/privacy controls

## 주요 상태/흐름

- Quick action→feedback event→report
- Recent error→Undo
- Older error→Report correction
- Group award→individual member reports

## 기능 연결 원칙

경제앱은 아니지만 학생/그룹 선택→Skill→즉시 feedback→Undo/Report를 극도로 짧게 만든 교실 입력 benchmark.

기능을 독립 체크리스트로 보지 않고 다음 질문으로 연결해서 본다.

1. 이 기능이 어떤 객체/상태를 만든다.
2. 그 상태가 다른 기능의 사용 가능 여부를 바꾸는가.
3. 자동화가 실행되면 사용자에게 무엇이 보이는가.
4. 실패하면 어느 화면에서 다시 처리하는가.
5. 정정 시 원래 기록과 연결 상태가 어떻게 유지되는가.
