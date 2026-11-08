# Cashroom — UI·UX·버튼/컨트롤

## 확인된 주요 컨트롤

| 버튼·컨트롤·행동 | 역할 |
|---|---|
| Record it | 새 잔액 계산 후 거래 기록 |
| Retry / Hint | 오답 재시도와 반복 오류 힌트 |
| Hire / Pass | 직업 지원 처리 |
| Approve / Deny Item | 주문 일부 승인/거절 |
| Undo | plain transaction 정정 |
| Savings Transfer | Checking↔Savings |
| Bell | 교사 처리요청 진입 |

## UI·UX 관찰 포인트

- Primary action이 어느 사용자 역할에 속하는지 구분한다.
- 버튼 이름 자체보다 **행동 전 조건 → 클릭 → 처리중 → 성공/실패 → 복구**를 본다.
- Disabled 상태가 있다면 가능한 한 이유를 사용자에게 설명하는지 본다.
- 대량작업은 대상 수·총액·영향범위를 확정 전에 보여주는지 본다.
- 수업 중 고빈도 작업과 저빈도 설정 작업의 UI 밀도를 다르게 본다.

## 아직 실측이 필요한 것

- 실제 Dashboard layout
- 원장 반영과 Pending의 정확한 시점
- Hold 내부 계정구조
- scheduler retry/idempotency
