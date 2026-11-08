# Cashroom 외부 구조도

검증 범위: 공식 홈페이지·Help·Pricing  
제품 성격: 중학교 수학 + 교실경제 + 금융문해력

## 1. Product Context

~~~mermaid
flowchart LR
  Teacher --> Classroom
  Student --> Classroom
  Classroom --> Jobs
  Classroom --> Money
  Classroom --> Store
  Classroom --> Savings
  Classroom --> Credit
  Classroom --> Loans
  Classroom --> Alerts
~~~

C.

## 2. 공개 IA

~~~text
Cashroom
├─ Money / Checking
│  ├─ Pending transactions
│  ├─ Math check
│  └─ History / Undo
├─ Jobs
│  ├─ Student job
│  ├─ Open jobs
│  ├─ Applications
│  └─ Payday
├─ Bills
├─ Store
│  ├─ Orders
│  ├─ Coupons
│  └─ Auctions
├─ Savings
│  ├─ Transfers
│  ├─ Goal
│  └─ Interest
├─ Credit
├─ Loans
├─ Alerts
└─ Export
~~~

기능 C.

## 3. 핵심 거래 흐름

~~~mermaid
sequenceDiagram
  participant Sys as System
  participant S as Student
  participant Ledger as Money State

  Sys->>S: Paycheck/Bill/Purchase/Fine Pending
  S->>S: 새 Balance 계산
  alt 정답
    S->>Ledger: Record
    Ledger-->>S: Balance 갱신
  else 오답
    S->>S: 다시 시도
    S->>S: 두 번째 실패 후 Hint
  end
~~~

C.

Pending이 있으면 Store/Coupon/Auction 사용이 제한된다고 공식 Help에서 확인.

## 4. Jobs

~~~mermaid
flowchart TD
  StudentJob[기본 Student Job] --> BasePay[기본 참여급여]
  OpenJob[추가 Job] --> Apply[두 개의 짧은 질문]
  Apply --> TeacherReview[교사 검토]
  TeacherReview --> Hire
  Hire --> ScheduledPayday[예약 Payday]
~~~

C.

## 5. 자동화

~~~mermaid
flowchart TD
  PayrollRule --> Scheduler
  BillRule --> Scheduler
  InterestRule --> Scheduler

  Scheduler --> PaycheckPending
  Scheduler --> BillPending
  Scheduler --> Interest

  PaycheckPending --> StudentMath
  BillPending --> StudentMath
~~~

로그인 없이 payday/bill 실행 C. scheduler 내부 구현 U.

## 6. Teacher Alert Bell

~~~mermaid
flowchart LR
  JobApp[Job applications] --> Bell[One Bell]
  LoanReq[Loan requests] --> Bell
  StoreOrder[Store orders] --> Bell
  Negative[Below-zero students] --> Bell
  Bell --> TeacherDecision[교사 처리]
~~~

C.

## 7. Store Flow

~~~mermaid
stateDiagram-v2
  [*] --> Order
  Order --> MoneyRecorded
  MoneyRecorded --> WaitingApproval
  WaitingApproval --> Approved
  WaitingApproval --> Rejected
  Rejected --> Refund
  Refund --> [*]
  Approved --> [*]
~~~

쿠폰 사용 시 거절되면 돈과 쿠폰이 돌아옴 C.

## 8. Savings / Goal

~~~mermaid
flowchart LR
  Checking <--> Savings
  Savings --> Goal[Goal progress]
  InterestSchedule --> InterestCredit
  InterestCredit --> Savings
~~~

C.

## 9. Credit / Loan

~~~mermaid
flowchart TD
  Bills --> PaymentHistory
  PaymentHistory --> CreditScore[300-850 Credit Score]
  CreditScore --> LoanApplication
  LoanApplication --> InterestMath[I = P r t]
  InterestMath --> TeacherApproval
  TeacherApproval --> Loan
  Loan --> WeeklyRepayment
~~~

C.

## 10. Undo 구조

공식 Help의 외부 동작을 기준으로 기능마다 복구 위치가 다름.

~~~text
일반 지급/차감 → History → Undo
Store → Store order에서 취소/환불
Loan → Loan 영역에서 처리
Auction → Auction 영역에서 처리
~~~

이 차이는 복합 거래가 연결 상태를 가진다는 신호 C/I.

## 11. Shared Device / Security

C:
- 학생 5회 비밀번호 오류 후 15분 제한
- 학생 세션 약 3시간
- 교사 세션 약 12시간
- 최신 브라우저/Chromebook/Phone
- 학생 이메일 불필요
- first name + last initial 중심

## 12. 외부 도메인 모델

~~~mermaid
erDiagram
  CLASS ||--o{ STUDENT : contains
  STUDENT ||--o{ JOB_APPLICATION : submits
  JOB ||--o{ JOB_APPLICATION : receives
  STUDENT ||--o{ PAYCHECK : receives
  STUDENT ||--o{ BILL : owes
  STUDENT ||--o{ PENDING_MONEY_ITEM : records
  STUDENT ||--o{ ORDER : places
  STUDENT ||--o{ SAVINGS_GOAL : owns
  STUDENT ||--o{ LOAN : borrows
  LOAN ||--o{ REPAYMENT : has
~~~

I.

## 13. Unknown

- Pending 이전 실제 원장 반영시점
- Order의 자금 hold 여부
- 동시구매/경매 원자성
- scheduler 재시도
- credit score 정확한 계산규칙
- reversal 내부 transaction 방식

## 14. Class Money 시사점

X:
- Teacher Inbox 공통 객체
- 자동화와 학생 사고를 분리
- 기능별 reversal policy
- 기본 참여소득
- 학생별 math friction 설정
- shared-device session을 핵심 요구로

## 근거
- https://cashroomapp.com/
- https://cashroomapp.com/help
