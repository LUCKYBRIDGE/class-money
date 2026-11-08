# ClassBank — 기능·흐름·상태

## 핵심 기능

- Roster
- Bonuses/Fines
- Jobs/Applications
- Payroll
- Bills
- Store
- Savings/Interest
- Student Helpers
- Co-teachers
- Reports/Export
- School/SIS integration

## 주요 상태/흐름

- Job: Open→Applied→Hired→Active→Ended
- Purchase: Requested→Approved/Rejected
- Recurring rules: configured→scheduled→executed
- Helper action: actor가 감사대상

## 기능 연결 원칙

처음에는 Classes·Students·Bonuses·Store만 열고 이후 Jobs·Bills·Savings를 추가하는 단계형 교실경제.

기능을 독립 체크리스트로 보지 않고 다음 질문으로 연결해서 본다.

1. 이 기능이 어떤 객체/상태를 만든다.
2. 그 상태가 다른 기능의 사용 가능 여부를 바꾸는가.
3. 자동화가 실행되면 사용자에게 무엇이 보이는가.
4. 실패하면 어느 화면에서 다시 처리하는가.
5. 정정 시 원래 기록과 연결 상태가 어떻게 유지되는가.
