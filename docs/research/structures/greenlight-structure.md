# Greenlight 외부 구조도

검증 범위: 공식 Greenlight Help  
제품 성격: 아동·가족 실제 금융관리

## 1. Product Context

~~~mermaid
flowchart LR
  Parent --> ChildAccount
  Child --> ChildAccount
  ChildAccount --> Spend
  ChildAccount --> Savings
  ChildAccount --> Give
  ChildAccount --> Goals
  Parent --> Chores
  Chores --> Earnings
  Earnings --> Allocation
~~~

C.

## 2. 핵심 외부 기능

~~~text
Child Money
├─ Balance / transactions
├─ Spend controls
├─ Savings
│  ├─ Goals
│  └─ Interest / rewards
├─ Give
├─ Chores
│  ├─ Recurring
│  └─ One-off
├─ Allowance
├─ Earning allocation
└─ Parent permissions / notifications
~~~

C.

## 3. Chore → Earnings → Allocation

~~~mermaid
flowchart TD
  Parent --> CreateChore
  CreateChore --> Complete
  Complete --> Pay
  Pay --> AllocationRule
  AllocationRule --> Spend
  AllocationRule --> Savings
  AllocationRule --> Give
  AllocationRule --> SpecificGoal
~~~

C.

## 4. Allocation State

~~~mermaid
stateDiagram-v2
  [*] --> EarningsCreated
  EarningsCreated --> AllocationValidation
  AllocationValidation --> InvalidTotal
  InvalidTotal --> AllocationValidation
  AllocationValidation --> Distributed
  Distributed --> [*]
~~~

비율 배분은 합계 100%를 요구한다고 공식 도움말에서 확인.

## 5. Goal Flow

~~~mermaid
flowchart LR
  CreateGoal --> FundGoal
  FundGoal --> Progress
  Progress --> GoalReached
  Progress --> WithdrawRequest
  WithdrawRequest --> ParentDecision
~~~

Savings Goal 존재 C. 정확한 모든 인출경로는 기능/플랜별 실측 필요.

## 6. Parent / Child Permission

~~~mermaid
flowchart TD
  Parent --> Configure[Allowance/Chores/Permissions]
  Parent --> Review[Transactions/Notifications]
  Child --> View[Balance/Goals]
  Child --> Earn[Chores]
  Child --> SpendAction[Spend]
  Configure --> Limits[Controls]
  Limits --> SpendAction
~~~

C.

## 7. 외부 도메인 모델

~~~mermaid
erDiagram
  FAMILY ||--o{ CHILD : contains
  CHILD ||--o{ CHORE : assigned
  CHORE ||--o{ EARNING : produces
  EARNING ||--o{ ALLOCATION : splits
  CHILD ||--o{ SAVINGS_GOAL : owns
  CHILD ||--o{ TRANSACTION : has
  PARENT ||--o{ PERMISSION_RULE : manages
~~~

I.

## 8. Class Money가 참고할 구조

X:
- 수입 → 목적배분 → 사용가능액
- 학생이 자신의 allocation rule을 선택
- 목적저축
- 위험도 높은 행동만 교사 승인

실제 금융카드·계좌·투자는 구조 참고 대상에서 제외.

## 9. Unknown

- 실제 금융 ledger
- 모든 plan별 permission 차이
- goal withdraw의 정확한 승인조건
- allocation failure handling

## 근거
- https://help.greenlight.com/hc/en-us/articles/50527840580379-How-do-I-pay-my-child-per-chore-and-split-the-earnings
- https://help.greenlight.com/hc/en-us/articles/360009173153-How-do-Savings-Goals-work-How-do-I-set-them-up
