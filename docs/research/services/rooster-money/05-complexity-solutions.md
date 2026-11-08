# NatWest Rooster Money — 얽힌 문제와 해결방식

## 복잡한 문제를 어떻게 풀었는가

| 얽힌 문제 | 서비스의 해결방식 | Class Money에 번역 |
|---|---|---|
| 정기 책임과 추가보수 혼동 | Allowance Chore vs Extra Earner | 직업업무/추가 task 분리. |
| 25명 승인업무 폭증 | Bulk approve | Class Money Teacher Inbox batch command. |
| 미완료와 면제가 같은 상태 | Skip/Re-open/Not Done 구분 | Absent/Exempt/NotDone 별도. |
| 관리자 전체목록과 일상실행 혼동 | Master vs Today | 전체관리와 Today view 분리. |
| 공유기기 혼선 | Switch User | 학생바꾸기 1급 기능. |

## 평가 기준

좋은 해결방식인지 판단할 때:
- 교사 클릭 수만 줄였는가, 아니면 오류복구도 쉬운가?
- 학생에게 필요한 사고까지 자동화해 없애지는 않았는가?
- 다수 학생에게 적용할 때 batch/exception을 처리할 수 있는가?
- 역할/권한/경제상태가 섞여 있지 않은가?
- 정상경로뿐 아니라 실패·취소·환불·정정도 정의돼 있는가?
- 기능이 증가해도 기본 사용자에게 복잡도가 전파되지 않는가?
