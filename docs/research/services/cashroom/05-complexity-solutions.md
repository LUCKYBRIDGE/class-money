# Cashroom — 얽힌 문제와 해결방식

## 복잡한 문제를 어떻게 풀었는가

| 얽힌 문제 | 서비스의 해결방식 | Class Money에 번역 |
|---|---|---|
| 기능마다 거래 방식이 달라질 수 있음 | Pending + Math Check 공통 grammar | Class Money도 Request→Preview→Confirm→Result 공통화. |
| 왜 구매가 안 되는지 모름 | 상태별 disabled reason | 모든 disabled action에 원인 문구. |
| 교사 승인함 폭증 | One Bell | 위험/처리필요 이벤트만 Teacher Inbox에 수렴. |
| 경매·주문의 자금 중복사용 | winning bid Hold | 예약/hold account 도입. |
| 자동화가 학습을 가림 | 서버는 자동 실행, 학생은 Record | 학습확인 모드를 선택형으로. |
| 공유기기 보안 | 학생/교사 session expiry, lockout | 학생바꾸기·짧은 세션·이전정보 masking. |

## 평가 기준

좋은 해결방식인지 판단할 때:
- 교사 클릭 수만 줄였는가, 아니면 오류복구도 쉬운가?
- 학생에게 필요한 사고까지 자동화해 없애지는 않았는가?
- 다수 학생에게 적용할 때 batch/exception을 처리할 수 있는가?
- 역할/권한/경제상태가 섞여 있지 않은가?
- 정상경로뿐 아니라 실패·취소·환불·정정도 정의돼 있는가?
- 기능이 증가해도 기본 사용자에게 복잡도가 전파되지 않는가?
