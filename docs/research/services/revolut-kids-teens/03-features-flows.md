# Revolut Kids & Teens — 기능·흐름·상태

## 핵심 기능

- Sub-account
- Parent/Child shells
- Co-parent
- Allowance
- Challenges
- Pockets/Goals
- Recurring transfers
- Analytics
- Payments
- Approval rules
- Age eligibility
- Card controls

## 주요 상태/흐름

- Challenge: requested→approved→active→completed→rewarded
- Pocket transfer: scheduled→posted/skipped insufficient
- Permission: age/role/risk dependent
- Account: owner/admin/co-parent/child

## 기능 연결 원칙

Parent 계정 아래 Child sub-account, 별도 Child App, Co-parent 제한권한, Challenge·Pocket·Analytics를 연령/위험도에 따라 제공.

기능을 독립 체크리스트로 보지 않고 다음 질문으로 연결해서 본다.

1. 이 기능이 어떤 객체/상태를 만든다.
2. 그 상태가 다른 기능의 사용 가능 여부를 바꾸는가.
3. 자동화가 실행되면 사용자에게 무엇이 보이는가.
4. 실패하면 어느 화면에서 다시 처리하는가.
5. 정정 시 원래 기록과 연결 상태가 어떻게 유지되는가.
