# Cashroom — 기능·흐름·상태

## 핵심 기능

- Pending transaction
- Math Check
- Jobs/Paydays
- Bills
- Store/Cart/Orders
- Coupons
- Auctions/Hold
- Savings/Goals
- Loans/Credit
- Badges
- Teacher Inbox
- History/Undo
- Export
- Shared-device sessions

## 주요 상태/흐름

- Pending→Calculating→Recorded
- Order: Cart→Checkout→Waiting→Approved/Denied→Refund
- Auction: Bid→Winning Hold→Outbid/Win→Release/Capture
- Login: active→failed attempts→temporary lock
- Balance restriction: pending/negative/insufficient/store closed/sold out

## 기능 연결 원칙

급여·청구·구매·벌금 같은 서로 다른 돈 이동을 Pending→Math Check→Record라는 공통 상호작용으로 통일.

기능을 독립 체크리스트로 보지 않고 다음 질문으로 연결해서 본다.

1. 이 기능이 어떤 객체/상태를 만든다.
2. 그 상태가 다른 기능의 사용 가능 여부를 바꾸는가.
3. 자동화가 실행되면 사용자에게 무엇이 보이는가.
4. 실패하면 어느 화면에서 다시 처리하는가.
5. 정정 시 원래 기록과 연결 상태가 어떻게 유지되는가.
