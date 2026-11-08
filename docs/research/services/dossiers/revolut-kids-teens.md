# Revolut Kids & Teens Product Anatomy

기준일: 2026-11-08  
범위: 공식 Parents & Guardians 페이지와 Kids & Teens Terms.  
목적: 역할분리·연령별 자율성·Challenges/Goals·보호자 승인 모델 분석.

## 1. 제품 경계와 정체성

Revolut Kids & Teens는 성인 Revolut 계정 아래에서 자녀가 독립 앱과 카드를 사용하는 실제 금융서비스다.

공식 기능:
- Kids & Teens app
- parent/guardian approval
- add money / allowance
- Challenges
- Goals
- spending analytics
- card/payment
- 일부 연령별 P2P 기능
- Co-Parent
- 기능별 연령 제한

Class Money가 참고할 것은 실제 결제기능이 아니라 **아동 자율성의 단계화와 관리자/사용자 화면 분리**다.

## 2. 사용자 역할

### Parent / Guardian
계정 생성/승인, 자금 제공, 일부 기능 승인, Co-Parent 관리.

### Kids & Teens user
자기 앱에서 spending, analytics, goal, challenge 등 사용.

### Co-Parent
limited secondary management:
- 돈 전송
- spending track
등 일부 권한.
주 소유자와 동일권한이 아니다.

**핵심:** administrator도 owner/co-manager로 계층화된다.

## 3. 핵심 객체

- Parent account
- RKT sub-account
- Child user
- Co-Parent
- Card
- Payment
- Approval
- Challenge
- Challenge reward
- Goal
- Savings amount
- Analytics
- Age eligibility rule

## 4. 기능 구조도

~~~mermaid
flowchart TD
  PA[Parent] --> AC[RKT Account]
  CP[Co-Parent] --> AC
  AC --> CH[Child App]
  PA --> AL[Money/Allowance]
  AL --> AC
  PA --> CA[Challenge]
  CA --> RW[Reward]
  RW --> AC
  CH --> GO[Goal]
  AC --> GO
  AC --> AN[Analytics]
  AC --> PY[Payment/Transfer]
  AP[Approval Rules] --> PY
  AGE[Age Rules] --> PY
  AGE --> AC
~~~

## 5. Parent App와 Child App 분리

공식 구조:
부모는 자기 Revolut 앱에서 child account를 만들거나 승인.
아이는 별도 Kids & Teens 앱.

이것은 단순히 메뉴를 숨기는 것이 아니라 **서로 다른 제품 shell**을 제공하는 방식이다.

### D Class Money
Teacher shell:
- Today
- Students
- Economy operations
- Audit
- Settings

Student shell:
- My Money
- Job/Tasks
- Goal
- Shop
- My History

동일 navigation을 role별로 disable하는 방식보다 명확하다.

## 6. Age-based Progressive Access

공식:
- 특정 연령 미만은 parent가 계정을 생성
- 더 높은 연령은 child가 시작하고 parent approve
- 일부 transfer/payment 기능도 연령조건

### 구조적 의미
자율성을 한번에 주지 않는다.

Class Money는 법적 age rule이 아니라 학년 preset으로:
- 1–2: wallet/goal/shop
- 3–4: +job/savings
- 5–6: +tax/market/approved transfer
를 제공.

교사가 override 가능.

## 7. Challenges

공식 Terms:
parent가 task/chore를 만들고 child가 완료하면 extra pocket money.

구조:
Challenge definition → completion → reward.

Class Money:
Task:
- title
- description
- due
- reward policy
- status
- approval requirement

과업과 transaction을 한 record로 덮어쓰지 않고 reward transaction은 별도로 생성.

## 8. Goals

공식:
parent app 또는 child app에서 goal을 만들고 진행률 추적.
Goal savings는 spending money와 분리.

**중요**
목표는 단순 progress bar가 아니라 **spending money와 구조적으로 분리된 돈**.

Class Money:
사용가능 / 저축 / 목표를 UI와 ledger account에서 분리.

## 9. Analytics

공식:
아이도 자신이 돈을 어디에 쓰는지 trends를 본다.

### D Class Money
통계를 교사 감시화면으로만 만들지 않는다.

학생용:
- 이번 주 수입
- 지출
- 저축
- 목표 변화
- 거래분류

개인 ranking은 없음.

## 10. Approval Model

공식 Terms에는 특정 지급에서 최초 상대에 대한 approval, 일정 금액 이상 추가 approval 등 **risk-dependent approval** 개념이 나타난다.

핵심은 모든 transaction에 parent approve를 요구하지 않는 것.

### D Class Money
Low risk:
- own wallet→own savings
- standard low-price store

High risk:
- student-to-student transfer
- high-value purchase
- helper sending money
- loan
- auction

승인 Queue를 위험도에 따라 줄인다.

## 11. Co-Parent

공식:
Co-Parent는 limited access.
모든 owner action을 할 수 없음.

Class Money Co-teacher:
- View
- Award
- Approve store
- Manage jobs
- Edit policy
- Export
를 별도 permission.

‘교사’라는 이유로 모든 권한 자동부여하지 않을 수 있다.

## 12. 관리자 복잡성을 학생에게 숨김

Child에게:
- permission rule editor
- co-parent
- account ownership
같은 개념은 필요 없다.

학생은 결과 문구만:
“이 요청은 선생님의 확인이 필요합니다.”

### UX 원칙
**규칙을 이해할 만큼만 설명하고, 규칙을 설정하는 UI는 숨긴다.**

## 13. Goal / Challenge의 제품 언어

금융상품 이름보다:
- Goal
- Challenge
처럼 목적/행동 단어를 사용.

Class Money 저학년:
‘정기급여 규칙’보다 ‘다음 월급’.
‘allocation bucket’보다 ‘쓸 돈 / 모을 돈’.

## 14. 복잡성을 풀어낸 방식

1. parent/child app separation
2. age-based progressive access
3. limited Co-Parent
4. Challenges as task+reward
5. Goals separated from spending
6. child-facing analytics
7. risk-based approvals
8. user-friendly domain language

## 15. Class Money에 가져올 것

**강하게**
- 별도 teacher/student shells
- 학년별 feature preset
- risk-based approval
- Goal separation
- Challenge→reward
- student analytics
- co-teacher granular permission

**제외**
- 실제 card/payment/P2P
- real money ownership/legal flow.

## 16. Craft Anything 실측

- parent home vs child home
- child onboarding by age
- approval notification
- Challenge create/complete
- Goal create/progress
- analytics visual
- Co-Parent UI
- restricted feature presentation
- mobile bottom navigation

## 17. 현재 판단

Revolut Kids & Teens의 가장 큰 가치가 있는 설계는 **아동의 자율성을 기능별·연령별로 단계적으로 주는 것**이다. Class Money의 학생 권한과 교사 승인 시스템에 강한 참고가 된다.

## 공식 근거
- https://www.revolut.com/revolut-kids-and-teens-parent-and-guardians/
- Revolut Kids & Teens Terms PDF — Challenges, Goals, Co-Parent, approval sections
