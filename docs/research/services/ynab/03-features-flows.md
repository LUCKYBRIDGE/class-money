# YNAB — 기능·흐름·상태

## 핵심 기능

- Accounts
- Categories
- Targets
- Ready to Assign
- Available
- Auto-Assign
- Transactions
- Money Movements
- Scheduled Transactions
- Reconcile
- Focused views

## 주요 상태/흐름

- RTA: positive/zero/negative
- Category: funded/underfunded/overspent
- Transaction: approved/cleared
- Scheduled: future→due→transaction
- Movement: category→category

## 기능 연결 원칙

돈의 실제 위치(Account)와 목적(Category/Plan)을 분리하고 Ready to Assign·Available·Target·Auto-Assign으로 복잡한 예산을 추상화.

기능을 독립 체크리스트로 보지 않고 다음 질문으로 연결해서 본다.

1. 이 기능이 어떤 객체/상태를 만든다.
2. 그 상태가 다른 기능의 사용 가능 여부를 바꾸는가.
3. 자동화가 실행되면 사용자에게 무엇이 보이는가.
4. 실패하면 어느 화면에서 다시 처리하는가.
5. 정정 시 원래 기록과 연결 상태가 어떻게 유지되는가.
