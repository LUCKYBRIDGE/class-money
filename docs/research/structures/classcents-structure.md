# ClassCents 외부 구조도

검증 범위: 공식 홈페이지·설정 가이드  
제품 성격: 저마찰 교실경제 운영

## 1. Product Context

핵심 특징:
학생 로그인 없이도 교사만으로 경제운영 가능.

~~~mermaid
flowchart LR
  Teacher --> Economy[Class Economy]
  Student -. optional login .-> Economy
  Economy --> Jobs
  Economy --> Payday
  Economy --> GiveDeduct[Give/Deduct]
  Economy --> Rewards
  Economy --> Savings
  Economy --> Transactions
~~~

C.

## 2. 운영 IA

~~~text
Classroom
├─ Students / Roster
│  ├─ CSV
│  ├─ Excel
│  └─ Paste
├─ Currency / Points mode
├─ Jobs
│  └─ Payday
├─ Give / Deduct
│  ├─ Individual
│  ├─ Group
│  └─ Whole class
├─ Shop / Rewards
├─ Savings / Goals
├─ Badges
├─ Leaderboard
├─ Transaction History
├─ CSV / Printable reports
└─ Student Dashboard (optional)
~~~

C.

## 3. 사용자 모드

~~~mermaid
flowchart TD
  ClassCents --> TeacherOnly[Teacher-only]
  ClassCents --> SharedDevice[학생 shared device]
  ClassCents --> StudentLogin[학생 개인 login card]

  TeacherOnly --> FullOps[경제 운영 가능]
  SharedDevice --> BalanceView
  StudentLogin --> StudentDashboard
~~~

Teacher-only 완전운영 C.

## 4. Roster / Identity

~~~mermaid
flowchart LR
  Spreadsheet --> Import
  CSV --> Import
  Paste --> Import
  Import --> Students
  Students --> LoginCard[선택적 Username/Password Card]
~~~

학생 이메일 불필요 C.

## 5. Payday

~~~mermaid
flowchart TD
  Job --> PayRate
  Job --> Frequency[Daily/Weekly/Monthly]
  Job --> OptionalDone[Job done 조건 선택]
  Frequency --> Payday
  OptionalDone --> Payday
  Payday --> StudentBalance
~~~

C.

## 6. Quick Transaction

~~~mermaid
sequenceDiagram
  participant T as Teacher
  participant UI as ClassCents
  participant S as Student(s)

  T->>UI: 개인/그룹/전체 선택
  T->>UI: 저장 Reason 선택
  T->>UI: Give/Deduct
  UI->>S: Balance 반영
  UI-->>T: History / Undo
~~~

C.

## 7. Spend

C로 공개된 Student UX:
Current Balance / Cost / New Balance를 함께 표시.

~~~mermaid
flowchart LR
  Balance --> Reward
  Reward --> Cost
  Cost --> NewBalance
  NewBalance --> Redeem
~~~

## 8. Savings

~~~mermaid
flowchart TD
  Balance --> Savings
  Balance --> NamedGoal[학생이 이름 붙인 Goal]
  Class --> ClassGoal[학급 공동 Goal]
~~~

C.

## 9. Multi-class Balance

C:
동일 학생이 여러 classroom에 있으면 하나의 login과 Balance를 공유한다고 설명.

~~~mermaid
flowchart TD
  Student --> SharedBalance
  ClassA --> SharedBalance
  ClassB --> SharedBalance
  ClassA --> JobsA
  ClassB --> JobsB
~~~

Class Money에서는 기본 채택하지 않음.

## 10. 외부 도메인 모델

~~~mermaid
erDiagram
  STUDENT ||--o{ CLASS_MEMBERSHIP : joins
  CLASS ||--o{ CLASS_MEMBERSHIP : has
  STUDENT ||--|| BALANCE : shares
  CLASS ||--o{ JOB : defines
  JOB ||--o{ JOB_ASSIGNMENT : assigns
  STUDENT ||--o{ TRANSACTION : receives
  CLASS ||--o{ REWARD : offers
  STUDENT ||--o{ SAVINGS_GOAL : owns
~~~

I. 특히 Shared Balance 내부구조는 U.

## 11. 운영 철학

공식 가이드는:
- 초기 설정 약 한 prep period
- 익숙해진 뒤 낮은 일일 운영 부담
- 작은 reward ≈ 하루 급여
- medium ≈ 주급
- large ≈ 수주 급여
같은 상대 가격설계를 제안.

C.

## 12. Unknown

- balance의 실제 원장 방식
- undo 내부 구현
- simultaneous reward redemption
- payroll failure/retry
- 로그인카드 인증 저장방식
- multi-class balance의 transaction scope

## 13. Class Money 적용

X:
- Teacher-only를 정식 운영모드로
- wallet은 기본 classroom scope
- 로그인카드 + shared-device 최적화
- 가격을 ‘몇 번의 급여’로 진단
- Quick UI와 strict ledger 분리

## 근거
- https://www.classcents.com/
- https://www.classcents.com/guides/how-to-set-up-a-classroom-economy
