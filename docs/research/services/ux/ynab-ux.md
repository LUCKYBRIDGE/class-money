# YNAB — 목적 기반 예산·정보구조·UI·UX 심층 분석

기준일: 2026-11-08  
증거 수준: 공식 최신 Help/Features 기반. 교실경제 앱이 아니므로 원리를 초등 수준으로 재해석.

## 1. 복잡성의 원천
YNAB는 계좌, 거래, Categories, Category Groups, Targets, Ready to Assign, Available, Auto-Assign, Scheduled Transactions, Reports를 다룬다.

성인에게도 복잡한 구조인데 핵심 개념 하나로 정리한다:
돈을 받으면 그 돈의 목적을 정한다.

## 2. Accounts와 Categories를 분리
공식 Help는:
Account = 돈이 실제로 있는 곳
Category = 그 돈의 목적
이라고 명확히 구분한다.

Class Money에서 이 차이는 매우 중요하다.

지갑은 돈의 위치.
목표/계획은 돈의 목적.

데이터 모델과 UI를 분리해야 한다.

## 3. Ready to Assign
아직 목적을 정하지 않은 돈을 별도 상태로 보여준다.

이 UX는 Class Money 급여 수령 직후 매우 유용하다.

급여 +100
아직 정하지 않은 돈 100
→ 지금 쓸 돈 / 목표 / 공동체로 나누기

단 학생에게는 Ready to Assign 같은 용어 대신 아직 정하지 않은 돈처럼 설명한다.

## 4. Available을 가장 중요한 숫자로
공식 정의에서 Available은 실제 일상 지출 결정을 안내하는 금액이다.

Class Money에서도 총자산보다:
지금 쓸 수 있는 돈
을 첫 화면에서 크게 보여주는 편이 낫다.

## 5. Targets
목표는 얼마를 언제까지 준비할지를 알려주고 상태를 색으로 표시한다.

Class Money는 색만으로 상태를 표현하지 않고:
잘 가고 있어요
목표까지 20 부족
같은 텍스트를 함께 제공.

## 6. Auto-Assign Preview
2026 최신 Help에서 Auto-Assign은 실행 전 어느 category에 얼마가 들어갈지 preview하고 Save Assignments로 확정한다.

이 패턴은 Class Money의 모든 자동화에 강하게 적용할 수 있다.

자동배분, 세금, 급여, 가격변경:
결과 미리보기 → 수정 → 확정

자동화가 결과를 숨기지 않게 한다.

## 7. Inspector/Contextual Control
웹에서는 선택한 category의 관련 옵션을 오른쪽 Inspector에서 보여준다.

복잡성을 풀어내는 좋은 방식:
전체 화면에 모든 설정을 노출하지 않고 현재 선택한 객체의 세부도구만 보인다.

Class Money 데스크톱 교사 UI:
왼쪽 목록 / 가운데 주요 내용 / 오른쪽 선택 상세 패널
구조를 일부 화면에서 활용할 수 있다.

## 8. 색상 상태의 위험과 번역
YNAB는 목표 상태를 색상으로 빠르게 표현하지만 초등 접근성을 위해 Class Money는 아이콘+문구를 함께 사용해야 한다.

예:
✓ 충분해요
△ 조금 더 필요해요
! 계획을 확인해요

## 9. Plan 변경을 실패로 보지 않기
예산은 고정 약속이 아니라 계속 조정하는 계획이다.

Class Money 목표에서 돈을 옮길 때:
실패/깨뜨림
대신
계획 변경 → 목표 예상기간 변화
를 보여준다.

## 10. Reconcile 사고
거래기록과 실제 상태가 맞는지 확인하는 개념은 금융문해력 활동으로 활용 가능하다.

Class Money 주간 활동:
이번 주 내역에서 이상한 거래를 찾아보세요.
학생이 오류를 발견하면 교사에게 신고.

## 11. UX 위험
- Categories를 무제한 만들게 하면 초등학생에게 과도.
- 성인 금융용어를 그대로 쓰면 학습장벽.
- 세밀한 월예산 UI를 복제하면 Class Money의 핵심이 흐려짐.

## 12. Class Money 적용
강하게:
- 위치와 목적 분리
- 아직 정하지 않은 돈
- Available 중심
- 목표
- 자동화 Preview
- 문맥형 상세패널
- 계획 변경의 trade-off
- 거래 확인 활동

단순화:
1~2학년 2개 목적
3~4학년 3개
5~6학년 3~4개

## 13. Craft Anything 실측 항목
- Ready to Assign 시각적 위치
- Category/Group 계층
- Target 상태 표현
- Auto-Assign preview
- Inspector 문맥변화
- 모바일에서 assign 흐름
- overspending 피드백
- Undo

## 공식 근거
- https://support.ynab.com/en_us/getting-started-categories-in-ynab-rkWG3rp6x
- https://support.ynab.com/en_us/getting-started-targets-in-ynab-r1FTiSaTbe
- https://support.ynab.com/en_us/auto-assign-a-guide-r1gBNbBJo
- https://support.ynab.com/en_us/getting-started-ynab-basics-and-key-terms-BJCaIHaTZe
