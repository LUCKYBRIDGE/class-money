# ClassBank — 얽힌 문제와 해결방식

## 복잡한 문제를 어떻게 풀었는가

| 얽힌 문제 | 서비스의 해결방식 | Class Money에 번역 |
|---|---|---|
| 처음부터 기능이 많음 | Classes→Students→Bonuses→Store부터 시작 | Class Money 첫 설정도 4개 이하 과업. |
| 학교마다 명부 입력 방식이 다름 | Class Code/Manual/Spreadsheet/School Search 다중 경로 | paste-first + code join + import 병행. |
| 학생 직업과 실제 권한 혼동 | Job과 Helper Permission 별도 | Class Money도 Job과 RBAC/permission 분리. |
| 경제 밸런스 설정 어려움 | 학년별 추천 salary/expense | 입력 중 수입·고정비·여유액 실시간 계산. |
| 학생 운영의 오용 위험 | helper action을 transaction/report에서 추적 | self-action 금지·한도·감사로그 추가. |

## 평가 기준

좋은 해결방식인지 판단할 때:
- 교사 클릭 수만 줄였는가, 아니면 오류복구도 쉬운가?
- 학생에게 필요한 사고까지 자동화해 없애지는 않았는가?
- 다수 학생에게 적용할 때 batch/exception을 처리할 수 있는가?
- 역할/권한/경제상태가 섞여 있지 않은가?
- 정상경로뿐 아니라 실패·취소·환불·정정도 정의돼 있는가?
- 기능이 증가해도 기본 사용자에게 복잡도가 전파되지 않는가?
