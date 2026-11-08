# ClassDojo — 얽힌 문제와 해결방식

## 복잡한 문제를 어떻게 풀었는가

| 얽힌 문제 | 서비스의 해결방식 | Class Money에 번역 |
|---|---|---|
| 수업 중 입력이 너무 느리면 안 씀 | 대상→Skill의 짧은 흐름 | Class Money Quick Award도 1–3 actions. |
| 최근 실수와 오래된 실수의 복구비용 차이 | 즉시 Undo + Reports | Snackbar Undo + Ledger reversal. |
| Group 의미 혼동 | Group은 대상 selector | StudentGroup과 GroupAccount 분리. |
| 행동점수와 경제자산 혼합 위험 | 원래는 feedback event | Class Money에서 Behavior와 Money domain 분리. |

## 평가 기준

좋은 해결방식인지 판단할 때:
- 교사 클릭 수만 줄였는가, 아니면 오류복구도 쉬운가?
- 학생에게 필요한 사고까지 자동화해 없애지는 않았는가?
- 다수 학생에게 적용할 때 batch/exception을 처리할 수 있는가?
- 역할/권한/경제상태가 섞여 있지 않은가?
- 정상경로뿐 아니라 실패·취소·환불·정정도 정의돼 있는가?
- 기능이 증가해도 기본 사용자에게 복잡도가 전파되지 않는가?
