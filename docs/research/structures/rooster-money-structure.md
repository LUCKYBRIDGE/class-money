# NatWest Rooster Money 외부 구조도

검증 범위: 공식 Chores Guide·Tracker Guide  
제품 성격: 용돈·과업·저축 루틴

## 1. Product Context

~~~mermaid
flowchart LR
  Parent --> Child
  Parent --> Allowance
  Parent --> Chores
  Chores --> AllowanceChore
  Chores --> ExtraEarner
  Child --> Complete
  Complete --> Approval
  Approval --> Wallet
~~~

C.

## 2. Chore Taxonomy

~~~mermaid
flowchart TD
  Chore --> AllowanceChore[Allowance chore]
  Chore --> ExtraEarner[Extra earner]
  AllowanceChore --> AllowancePolicy
  ExtraEarner --> Reward[Money or Stars]
  ExtraEarner --> DueDate
~~~

C.

## 3. Allowance Policy

공식 도움말에서 미완료 chores가 있을 때:
- Full allowance
- No allowance
- Percentage based on completed chores
- Prompt parent to decide
같은 정책을 제공.

~~~mermaid
flowchart TD
  PeriodEnd --> CompletionCheck
  CompletionCheck --> Full
  CompletionCheck --> None
  CompletionCheck --> Percentage
  CompletionCheck --> ManualDecision
  Full --> Wallet
  Percentage --> Wallet
  ManualDecision --> Wallet
~~~

C.

## 4. Extra Earner

~~~mermaid
stateDiagram-v2
  [*] --> Available
  Available --> InProgress
  InProgress --> Submitted
  Submitted --> Approved
  Submitted --> Rejected
  Approved --> Paid
  Paid --> [*]
~~~

학생 완료 제출·보호자 승인 C. 정확한 상태명은 I.

## 5. Scheduling

C:
- weekly
- monthly
- one-off
- no specific day
등 반복/기한 설정.

## 6. Tracker / Card의 두 층

공식 Tracker 가이드는 virtual money tracker와 실제 Rooster Card를 구분.

~~~mermaid
flowchart TD
  Rooster --> VirtualTracker
  Rooster --> RealMoneyCard
  VirtualTracker --> Allowance
  VirtualTracker --> Pots
  RealMoneyCard --> Spending
  RealMoneyCard --> Chores
~~~

C.

Class Money는 Virtual Tracker 쪽 구조만 참고.

## 7. 외부 도메인 모델

~~~mermaid
erDiagram
  FAMILY ||--o{ CHILD : contains
  CHILD ||--o{ ALLOWANCE_RULE : has
  CHILD ||--o{ CHORE : assigned
  CHORE ||--o{ CHORE_COMPLETION : tracks
  CHORE_COMPLETION ||--o| REWARD : may_create
  CHILD ||--o{ WALLET_EVENT : has
~~~

I.

## 8. Class Money 적용

X:
활동을 네 종류로 분리:
- 기본 공동체 책임
- 정기 직업
- 추가 퀘스트
- 비금전 공동체 기여

모든 행동을 돈으로 보상하지 않도록 도메인부터 분리.

## 9. Unknown

- allowance engine 내부처리
- approval retry
- stars와 money의 실제 데이터관계
- child session/security

## 근거
- https://roostermoney.com/feature/chores-guide/
- https://roostermoney.com/feature/chore-app-rooster-money/
- https://roostermoney.com/feature/getting-started-with-roostermoney-tracker/
