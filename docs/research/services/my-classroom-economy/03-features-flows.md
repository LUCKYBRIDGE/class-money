# My Classroom Economy — 기능·흐름·상태

## 핵심 기능

- Jobs
- Paychecks
- Banking
- Rent
- Bonuses/Fines
- Loans
- Auctions
- Desk ownership
- Student roles
- Monthly cadence
- Year-end reflection
- Printables

## 주요 상태/흐름

- Job application→offer→work→paycheck
- Transaction→student ledger→banker ledger reconciliation
- Rent due→paid/unpaid
- Loan application→active→installment→paid off
- Auction item→bids→winner

## 기능 연결 원칙

웹앱보다 Job Application·Paycheck·Bank Log·Rent Agreement·Auction Paddle 같은 물리적 인터페이스로 경제 절차를 분해.

기능을 독립 체크리스트로 보지 않고 다음 질문으로 연결해서 본다.

1. 이 기능이 어떤 객체/상태를 만든다.
2. 그 상태가 다른 기능의 사용 가능 여부를 바꾸는가.
3. 자동화가 실행되면 사용자에게 무엇이 보이는가.
4. 실패하면 어느 화면에서 다시 처리하는가.
5. 정정 시 원래 기록과 연결 상태가 어떻게 유지되는가.
