# Revolut Kids & Teens — 얽힌 문제와 해결방식

## 복잡한 문제를 어떻게 풀었는가

| 얽힌 문제 | 서비스의 해결방식 | Class Money에 번역 |
|---|---|---|
| 학생에게 관리자 UI가 과도 | Parent/Child shell 분리 | TeacherShell/StudentShell 별도 IA. |
| 모든 행동 승인하면 병목 | 위험도 기반 승인 | 고위험 거래만 Teacher approval. |
| 공동관리자 권한이 과도할 수 있음 | Admin parent vs Co-parent | Co-teacher granular permissions. |
| 연령별 자율성 차이 | Age eligibility | 학년별 기본 feature preset + 교사 override. |
| 목표돈을 소비돈과 혼동 | Pocket 분리 | Available/Goal account 분리. |

## 평가 기준

좋은 해결방식인지 판단할 때:
- 교사 클릭 수만 줄였는가, 아니면 오류복구도 쉬운가?
- 학생에게 필요한 사고까지 자동화해 없애지는 않았는가?
- 다수 학생에게 적용할 때 batch/exception을 처리할 수 있는가?
- 역할/권한/경제상태가 섞여 있지 않은가?
- 정상경로뿐 아니라 실패·취소·환불·정정도 정의돼 있는가?
- 기능이 증가해도 기본 사용자에게 복잡도가 전파되지 않는가?
