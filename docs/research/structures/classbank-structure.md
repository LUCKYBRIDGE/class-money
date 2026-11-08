# ClassBank 외부 구조도

검증 범위: 공식 Help Center·설정 가이드·보고서 문서  
제품 성격: 학급은행 + 금융문해력 + 학생운영

## 1. Product Context

~~~mermaid
flowchart LR
  Teacher[Teacher] --> Class[Class]
  Student[Student] --> Class
  CoTeacher[Co-teacher] --> Class
  Helper[Student Helper] --> Class

  Class --> Transactions[Transactions]
  Class --> Jobs[Jobs]
  Class --> Store[Store]
  Class --> Bills[Bills]
  Class --> Savings[Savings]
~~~

C.

## 2. 공개 기능 IA

~~~text
Class
├─ Students
│  ├─ Student profile
│  ├─ Balance
│  └─ Transactions
├─ Bonuses / Fines
├─ Jobs
│  ├─ Job board
│  ├─ Applications
│  ├─ Employees
│  └─ Auto Pay
├─ Bills / Expenses
├─ Store
│  ├─ Items
│  ├─ Purchases
│  └─ Approval / Reject
├─ Savings / Interest
├─ Student Helpers
│  ├─ Banker
│  ├─ HR Representative
│  └─ Store Clerk
├─ Reports / Export
└─ Co-teachers
~~~

C.

## 3. Role / Permission Map

~~~mermaid
flowchart TD
  T[Teacher] --> ALL[전체 설정/거래]
  CT[Co-teacher] --> OPS[운영 권한]
  S[Student] --> SELF[본인 거래/직업/상점/저축]

  B[Student Banker] --> SEND[거래 보내기]
  HR[HR Representative] --> JOB[Job board / jobs]
  SC[Store Clerk] --> STORE[구매 승인 / 상품 편집]
~~~

Student Helper 권한은 공식 문서로 C.

## 4. 거래의 이중 상태 구조

ClassBank의 핵심.

~~~mermaid
sequenceDiagram
  participant T as Teacher
  participant CB as ClassBank
  participant S as Student

  T->>CB: Transaction 발행
  CB->>CB: Teacher Balance에 반영
  CB->>S: Pending 생성
  S->>S: 새 잔액 계산
  S->>CB: Deposit/Withdraw 처리
  CB->>S: Student Balance 갱신
~~~

C.

즉:
- Teacher Balance = 발행된 거래 포함
- Student processed balance = 학생이 처리한 거래 기준
- Pending = 미처리

## 5. Pending State

~~~mermaid
stateDiagram-v2
  [*] --> Sent
  Sent --> Pending
  Pending --> Calculating
  Calculating --> WrongAnswer
  WrongAnswer --> Calculating
  Calculating --> Processed
  Processed --> [*]
~~~

계산 기능 OFF 시 일부 단계가 생략될 수 있음.

## 6. 직업시장

~~~mermaid
flowchart TD
  Job[Job Posting] --> Apply[학생 지원]
  Apply --> Choices[1/2/3지망 + 선택적 Resume]
  Choices --> Review[교사/HR 검토]
  Review --> Hire[채용]
  Review --> Deny[거절]
  Hire --> AutoPay[급여]
  Hire --> Rotation[직업 순환]
~~~

C.

## 7. Store Flow

~~~mermaid
sequenceDiagram
  participant S as Student
  participant Store as Store
  participant T as Teacher/Store Clerk

  S->>Store: 상품 선택
  Store->>S: 잔액/새 잔액 계산
  S->>Store: 구매
  Store->>T: Pending purchase
  T->>Store: 승인 또는 거절
  Store-->>S: 승인 완료 또는 환불
~~~

C.

## 8. Savings

~~~mermaid
flowchart LR
  Checking[Checking] --> Savings[Savings]
  Savings --> Goal[Goal]
  InterestRule[Interest Rule] --> Payout[Interest payout]
  Payout --> Savings
~~~

C. 내부 ledger 구현 U.

## 9. Reports / Export

C로 확인:
- All Transactions
- Student Transactions
- Student Jobs
- Store Purchases
- Student List
- Job Details

이는 ClassBank가 단순 현재 Balance가 아니라 여러 도메인 객체를 독립 데이터로 보유한다는 외부 신호다.

## 10. 핵심 데이터 관계 — 외부 도메인 추론

~~~mermaid
erDiagram
  CLASS ||--o{ STUDENT : contains
  CLASS ||--o{ JOB : defines
  JOB ||--o{ APPLICATION : receives
  STUDENT ||--o{ APPLICATION : submits
  JOB ||--o{ EMPLOYMENT : creates
  STUDENT ||--o{ EMPLOYMENT : holds
  STUDENT ||--o{ TRANSACTION : has
  CLASS ||--o{ STORE_ITEM : offers
  STORE_ITEM ||--o{ PURCHASE : creates
  STUDENT ||--o{ PURCHASE : makes
  STUDENT ||--o{ SAVINGS_GOAL : owns
~~~

I. 내부 DB 스키마가 아님.

## 11. 복잡성 관리

공식 시작 가이드는:
Classes → Students → Bonuses → Store를 먼저 시작하고
Jobs → Bills → Savings → Co-teachers를 추가하도록 안내.

이는 Progressive Disclosure 구조 C.

## 12. Unknown

- 교사 Balance와 실제 회계원장의 내부 관계
- Pending 거래의 서버 원장 처리 시점
- Auto Pay scheduler 내부 재시도
- 동시 Store purchase 처리
- Student Helper의 rate limit/감사로그
- Savings 내부 계좌구조

## 13. Class Money 적용

X:
ClassBank의 학습 마찰은 가져오되 실제 원장과 학생 확인 Activity는 분리하는 방향이 더 안전.

## 근거
- https://help.classbank.com/en/articles/6499058-how-do-i-get-started-with-classbank
- https://help.classbank.com/en/articles/9404212-what-s-the-difference-between-balance-and-pending
- https://help.classbank.com/en/articles/5949828-student-helper-jobs-banker-hr-manager-and-store-clerk
- https://help.classbank.com/en/articles/6827517-how-do-i-download-reports-in-classbank
