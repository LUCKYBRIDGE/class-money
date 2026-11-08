# YNAB — 얽힌 문제와 해결방식

## 복잡한 문제를 어떻게 풀었는가

| 얽힌 문제 | 서비스의 해결방식 | Class Money에 번역 |
|---|---|---|
| 총계좌잔액이 실제 지출판단에 부적절 | Available | Class Money 학생 Home도 Available 중심. |
| 돈이 들어와도 목적이 없음 | Ready to Assign | Payday→Allocation 단계. |
| 자동배분의 불신 | Auto-Assign Preview | 모든 bulk/scheduled policy에 Preview. |
| 실제거래와 목적변경 혼동 | Transaction vs MoneyMovement | Ledger와 AllocationMovement 분리. |
| 미래예정과 현재돈 혼동 | ScheduledTransaction 별도 | ScheduleRule을 posted transaction과 분리. |

## 평가 기준

좋은 해결방식인지 판단할 때:
- 교사 클릭 수만 줄였는가, 아니면 오류복구도 쉬운가?
- 학생에게 필요한 사고까지 자동화해 없애지는 않았는가?
- 다수 학생에게 적용할 때 batch/exception을 처리할 수 있는가?
- 역할/권한/경제상태가 섞여 있지 않은가?
- 정상경로뿐 아니라 실패·취소·환불·정정도 정의돼 있는가?
- 기능이 증가해도 기본 사용자에게 복잡도가 전파되지 않는가?
