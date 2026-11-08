# YNAB Product Anatomy

기준일: 2026-11-08  
범위: 공식 Getting Started, Assigning Money, Auto-Assign, terminology.  
목적: 복잡한 예산 모델을 사용자가 쉽게 조작하게 만드는 추상화 분석.

## 1. 제품 경계와 정체성

YNAB은 classroom economy가 아니라 personal spending plan 시스템이다.

핵심 객체/개념:
- Accounts
- Cash balance
- Transactions
- Ready to Assign
- Category / Category Group
- Assigned
- Available
- Target
- Scheduled Transaction
- Auto-Assign
- Underfunded
- Overspending
- Reconcile

기능은 복잡하지만 핵심 질문을:
**“What’s it for?”**
로 압축한다.

Class Money 학생경험에 매우 중요한 benchmark다.

## 2. 사용자 역할

주 사용자 한 명이 자신의 자산을 계획.

Class Money와 다르지만, 사용자의 인지과정은 비슷:
- 돈이 들어옴
- 목적 결정
- 사용
- 결과 확인
- 계획 조정.

## 3. 핵심 객체관계

~~~mermaid
flowchart TD
  AC[Cash Accounts] --> RTA[Ready to Assign]
  IN[Income Transaction] --> RTA
  RTA --> C1[Category]
  RTA --> C2[Category]
  RTA --> C3[Goal Category]
  T[Targets] --> C1
  T --> C2
  T --> C3
  C1 --> AV[Available]
  C2 --> AV
  C3 --> AV
  SP[Spending Transaction] --> AV
  SCH[Scheduled Transactions] --> AA[Auto-Assign]
  T --> AA
  AA --> C1
  AA --> C2
~~~

## 4. 핵심 추상화: Ready to Assign

**E1 확인**
현재 실제로 가진 cash 중 아직 category 목적이 정해지지 않은 돈.

목표:
Ready to Assign을 0으로 만들 때까지 돈을 categories에 배정.

이 개념은:
“통장에 1000 있으니 1000을 쓸 수 있다”
를
“1000 중 실제 자유롭게 쓸 돈이 얼마인가?”
로 바꾼다.

### D Class Money
Payday 후:
“새로 받은 100 중 아직 계획하지 않은 돈 100”

학생이:
- 쓸 돈
- 목표
- 모아둘 돈
- 공동체
로 나누면 ‘계획 안 한 돈 0’.

저학년은 선택적으로 자동추천.

## 5. Available

공식 용어:
category에서 이번 달 실제로 쓸 수 있는 돈.

이는 account balance보다 daily decision에 중요한 숫자다.

### D Class Money
학생 첫 화면 1순위:
총자산 X  
**지금 쓸 수 있는 돈** O.

저축, hold, 국고, reserved amount를 총액과 혼동시키지 않음.

## 6. Categories

Categories는 spending/saving priority를 envelope처럼 표현.

Class Money에는 무제한 category는 과도.

학년별:
- 1–2: 쓸 돈 / 모을 돈
- 3–4: 쓸 돈 / 목표 / 모아둘 돈
- 5–6: 자유사용 / 목표 / 예정지출 / 공동체

**중요:** 내부 ledger account와 학생 UI bucket이 반드시 1:1일 필요는 없다. UI는 교육목표에 맞게 단순화.

## 7. Targets

공식:
category에 얼마가 언제까지 필요한지 목표를 설정.
Target은 Auto-Assign과 Underfunded에 연결.

즉 Target은 단순 progress display가 아니라 **자동화 규칙의 입력값**이다.

Class Money:
Goal이 있다면 추천 저축액/예상기간 계산에 사용.

예:
목표 100 / 현재 40 / 다음 4주.
“현재 설정 기준 매주 15를 넣으면 약 4주.”

확정적인 미래처럼 표현하지 않음.

## 8. Underfunded

Target이 있지만 충분히 자금배정되지 않은 상태.

Class Money에서 ‘부족’은 실패로 표현하지 않는다.

문구:
- 목표까지 30 필요
- 이번 주 10 추가 시 예상기간 변화.

교사용 Economy Health에서는 여러 학생이 지속적으로 목표달성 불가능한지 구조적 문제를 탐지.

## 9. Auto-Assign

**E1 확인**
Target / Scheduled Transaction / 과거패턴 등을 기반으로 자동배분.
중요하게도 preview를 보고 Save Assignment하기 전에 바꿀 수 있다.

### 핵심 UX 원칙
**자동화는 즉시 실행보다 previewable proposal로 만든다.**

Class Money 적용:
- 학생 급여 자동배분 preview
- 교사 일괄 지급 preview
- 세금 적용 preview
- 학기 이월 preview
- pricing change preview.

## 10. Auto-Assign 옵션의 Progressive Disclosure

YNAB은 사용자가 초기에 onboarding prompt를 마치기 전 일부 옵션 접근이 제한될 수 있고, Auto-Assign은 돈이 있을 때 맥락적으로 나타난다.

좋은 원칙:
사용할 수 없는 action을 항상 화면에 남기지 않는다.

Class Money:
- 저축 활성화 전 이자 버튼 숨김
- student transfer OFF면 관련 메뉴 숨김
- 경제모듈 시작 전 menu 숨김.

## 11. Reconcile

공식:
실제 account statement와 YNAB balance를 대조해 기록 신뢰성을 확인.

Class Money에서는 실제 은행대조는 없지만 학습활동으로:
“이번 주 내 거래가 맞는지 확인”
가능.

학생:
- 급여
- 구매
- 저축
- 정정
을 검토하고 모르는 거래 신고.

이는 원장 투명성과 금융리터러시를 동시에 강화.

## 12. 계획 변경 철학

YNAB 구조상 category 간 돈을 옮겨 우선순위를 바꾸는 것이 자연스럽다.

Class Money:
Goal에서 쓸 돈으로 이동한다고 “저축 실패”로 낙인하지 않는다.

대신 trade-off:
“계획을 바꾸면 목표 예상 도착이 1주 늦어집니다.”

## 13. 상태와 시각화

YNAB에는 Ready to Assign, Available, Underfunded, Overspending 등 상태가 있으며 색과 금액을 함께 쓴다.

Class Money 접근성:
- 색만으로 표시하지 않음
- icon + text + amount
- 저학년에도 의미가 읽히는 문구.

## 14. Focus / Filter

복잡한 예산은 모든 category를 항상 볼 필요가 없다.

Class Money 거래장부/교사 dashboard:
- Today
- Needs action
- Paychecks
- Store
- Adjustments
- Failed
같은 focused view를 기본 제공.

## 15. 복잡성을 풀어낸 방식

1. 내부 모델을 ‘What’s it for?’ 질문으로 추상화
2. Ready to Assign
3. Available을 decision number로 사용
4. Targets가 자동화를 구동
5. Auto-Assign preview
6. 맥락적 action 노출
7. Reconcile로 신뢰 유지
8. 계획 변경을 정상행동으로 취급

## 16. Class Money에 가져올 것

**매우 강하게**
- Available 중심 학생홈
- income→purpose allocation
- goal/target
- previewable automation
- goal shortfall
- reconciliation/reflection
- focused views
- plain-language financial state.

**제외**
- 성인 금융용 복잡한 account/import
- credit card budgeting logic
- 무제한 category customization.

## 17. Craft Anything 실측

- Home/Plan의 first fold
- Ready to Assign state
- Assign mode
- category row 정보량
- Target create
- Auto-Assign preview
- Underfunded state
- overspending recovery
- mobile/web navigation 차이
- Undo/plan change.

## 18. 현재 판단

YNAB은 Class Money의 교사 운영보다 **학생이 돈을 바라보는 mental model**을 바꾸는 데 중요하다.

Class Money가 잔액 앱을 넘어서려면:
‘얼마 있지?’보다 ‘이 돈은 무엇을 위해 있지?’를 중심에 둘 가치가 있다.

## 공식 근거
- https://support.ynab.com/en_us/getting-started-assigning-your-money-in-ynab-SyHCkywTZl
- https://support.ynab.com/en_us/getting-started-ynab-basics-and-key-terms-BJCaIHaTZe
- https://support.ynab.com/en_us/auto-assign-a-guide-r1gBNbBJo
- https://support.ynab.com/en_us/the-plan-header-BkmiuJ_C9
