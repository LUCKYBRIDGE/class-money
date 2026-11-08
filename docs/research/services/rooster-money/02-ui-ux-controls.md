# NatWest Rooster Money — UI·UX·버튼/컨트롤

## 확인된 주요 컨트롤

| 버튼·컨트롤·행동 | 역할 |
|---|---|
| Add Chore | task 생성 |
| Allowance Chore / Extra Earner | 보상유형 선택 |
| Schedule | daily/weekly/monthly/one-off |
| Approve | 완료 승인 |
| Select all / Bulk | 일괄처리 |
| Re-open | 재작업 |
| Skip | 면제 |
| Not Done | 미완료 |
| Switch User | 공유기기 전환 |

## UI·UX 관찰 포인트

- Primary action이 어느 사용자 역할에 속하는지 구분한다.
- 버튼 이름 자체보다 **행동 전 조건 → 클릭 → 처리중 → 성공/실패 → 복구**를 본다.
- Disabled 상태가 있다면 가능한 한 이유를 사용자에게 설명하는지 본다.
- 대량작업은 대상 수·총액·영향범위를 확정 전에 보여주는지 본다.
- 수업 중 고빈도 작업과 저빈도 설정 작업의 UI 밀도를 다르게 본다.

## 아직 실측이 필요한 것

- 현재 app framework
- backend/DB
- push stack
- scheduler
