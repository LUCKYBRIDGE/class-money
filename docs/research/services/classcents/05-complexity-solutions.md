# ClassCents — 얽힌 문제와 해결방식

## 복잡한 문제를 어떻게 풀었는가

| 얽힌 문제 | 서비스의 해결방식 | Class Money에 번역 |
|---|---|---|
| 학생기기/로그인 준비가 안 됨 | 학생 로그인 optional | Teacher-only mode를 P0 fallback으로. |
| 25명 반복입력 | CSV/Excel/paste | paste-first roster. |
| 지급 범위마다 다른 화면 | 개인/그룹/전체 공통 selector | Quick Transaction 하나로 통합. |
| 구매 결과를 계산해야 함 | Current/Cost/New Balance | Class Money도 before/change/after. |
| 로그인 정보 배포 | printable card | QR+short PIN/A4 cards. |
| 교사 실수 | whole-class Undo | 즉시 undo + durable reversal. |

## 평가 기준

좋은 해결방식인지 판단할 때:
- 교사 클릭 수만 줄였는가, 아니면 오류복구도 쉬운가?
- 학생에게 필요한 사고까지 자동화해 없애지는 않았는가?
- 다수 학생에게 적용할 때 batch/exception을 처리할 수 있는가?
- 역할/권한/경제상태가 섞여 있지 않은가?
- 정상경로뿐 아니라 실패·취소·환불·정정도 정의돼 있는가?
- 기능이 증가해도 기본 사용자에게 복잡도가 전파되지 않는가?
