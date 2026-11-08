# Cashroom — 파일·폴더·기술 구조

정확도: **C — 현재 제품 source 비공개**

## 공개 source 여부
Cashroom 제품의 공식 public source repository를 확인하지 못했다.

## 외부에서 확인되는 delivery
- browser-based
- Chromebook/phone 지원
- teacher account
- student account
- Help Center

## 핵심 technical domains
- classroom
- student identity
- jobs/applications
- payroll
- recurring bills
- pending transactions
- math-check state
- checking
- savings/goals
- store/cart/order
- coupons
- auction/bids
- hold
- loans/credit
- badges
- teacher alert inbox
- history/undo
- export

## 중요한 상태/데이터 경계
Cashroom은 외부 행동만 봐도 다음 객체를 분리해야 동작을 설명할 수 있다.
- PendingMoneyItem
- PostedTransaction
- Order
- Bid/Hold
- Loan
- SavingsGoal

즉 모든 경제행위를 Transaction 한 종류로만 처리하는 구조는 아닐 가능성이 높다. 실제 내부 schema는 미확인.

## automation boundary
- scheduled paydays
- scheduled bills
- interest

로그인하지 않아도 실행되는 것으로 설명되므로 client-local timer가 아니라 server-side scheduled processing이 필요하지만 실제 기술은 미확인.

## auth/session boundary
공개 Help에서:
- starter code
- password creation
- failed login lockout
- student/teacher session expiry
를 확인.

실제 identity provider/session store 구현은 미확인.

## consistency requirement exposed by product
- cart checkout atomicity
- partial order approve/deny
- bid amount hold
- reversal
- teacher records on behalf of student

Class Money 기술설계에서 직접 테스트해야 할 영역.

## Class Money 대응 모듈
X 제안:
- auth
- classroom
- jobs
- scheduler
- ledger
- pending-learning-events
- accounts
- store
- holds
- auctions
- loans
- inbox
- reversal
- export

## 미확인
- frontend/backend frameworks
- database
- scheduler technology
- queue
- transactional DB boundaries
- hosting