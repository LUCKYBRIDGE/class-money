# My Classroom Economy 외부 구조도

검증 범위: 공식 Grades 4–5 페이지 및 공개 자료  
제품 성격: 종이·교실운영 중심 classroom economy 프로그램

## 1. Product Context

~~~mermaid
flowchart LR
  Teacher --> Rules[경제 규칙]
  Student --> Job[직업]
  Job --> Paycheck
  Paycheck --> Bank
  Bank --> Rent
  Bank --> Auction
  Bank --> Fines
  Bank --> Savings
  Teacher --> Reflection
  Student --> Reflection
~~~

C.

## 2. 공개 자료 구조

공식 Grades 4–5 페이지에서 제공:

~~~text
Intro
├─ Program Guide
├─ Parent Letter
└─ Administrator Letter

Employment
├─ Payday video
├─ Job application
├─ Job offer
├─ Job posters
└─ Paycheck

Banking
├─ Bank log
└─ Bank slips

Fines
├─ Fine tickets
└─ Offense log

Cash
├─ Bills
└─ Cash materials

Rent & Deeds
├─ Rental agreement
├─ Rent log
├─ Unpaid rent notice
└─ Deed to desk

Auctions
├─ Auction video
├─ Auction record
└─ Auction paddle

Year-end
└─ Saver certificates
~~~

C.

## 3. 월간 경제 Cadence

~~~mermaid
flowchart LR
  JobWork[직업 수행] --> Payday
  Payday --> Banking
  Banking --> RentFines[Rent / Fines]
  RentFines --> Auction
  Auction --> Review[기록/회고]
  Review --> NextMonth[다음 주기]
  NextMonth --> JobWork
~~~

C/I.

## 4. Employment

~~~mermaid
stateDiagram-v2
  [*] --> JobApplication
  JobApplication --> JobOffer
  JobOffer --> Employed
  Employed --> Paycheck
  Paycheck --> Employed
  Employed --> Rotation
  Rotation --> [*]
~~~

C.

## 5. Banking — 이중 기록

~~~mermaid
flowchart LR
  Paycheck --> StudentBankLog
  Paycheck --> BankerRecord
  StudentBankLog --> Reconcile[대조]
  BankerRecord --> Reconcile
  Reconcile --> Correct[오류 수정/확인]
~~~

C/I.

종이 환경의 이중기록 자체가 학습활동.

## 6. Rent / Desk Ownership

~~~mermaid
flowchart TD
  Salary --> Cash
  Cash --> Rent
  Rent --> Paid
  Rent --> Unpaid
  Paid --> AuctionEligibility
  Unpaid --> Notice
  Auction --> DeskPurchase[Desk deed / ownership]
~~~

공식 프로그램 구조 C. Class Money 적용 시 실제 좌석 권리와 분리 필요.

## 7. Auction

~~~mermaid
flowchart TD
  Item --> AuctionStart
  Students --> Bids
  Bids --> HighestBid
  HighestBid --> Winner
  Winner --> Payment
  Payment --> AuctionRecord
~~~

C.

## 8. 학생 운영기관

종이 프로그램 특성상 학생 직업 자체가 경제기관의 운영을 일부 담당.

I 역할지도:

~~~mermaid
flowchart TD
  Teacher --> EconomyRules
  BankerStudent --> Banking
  OtherJobs[학생 직업] --> ClassroomOps
  Students --> Transactions
  Transactions --> PaperRecords
~~~

정확한 직업 목록은 프로그램 자료별 추가 확인 필요.

## 9. 물리 산출물 구조

~~~mermaid
flowchart LR
  AppFuture[Class Money] -. digitalize .-> PaycheckPDF
  AppFuture -.-> StatementPDF
  AppFuture -.-> JobCard
  AppFuture -.-> PricePoster
  AppFuture -.-> AuctionSheet
  AppFuture -.-> EconomyRules
~~~

X: Class Money 적용안.

## 10. 교육적으로 남겨야 할 마찰

자동화 대상:
- 합산
- 반복 지급
- 오류검색
- 장부 보존

학생에게 남길 것:
- 예상
- 선택
- 기록확인
- 목표
- 경매 판단
- 회고

## 11. Unknown

- 프로그램 전체 학년별 운영 세부 차이
- 모든 student job 목록
- 실제 교사별 변형운영
- 종이 장부 reconciliation의 실제 빈도

## 12. Class Money 적용

X:
디지털화 목표는 ‘모든 종이를 없애기’가 아니라 교사 반복노동만 줄이는 것.

경제기간 종료와 학기말 회고를 제품 기능으로 포함.

## 근거
- https://myclassroomeconomy.org/en/grades4-5
