# YNAB 공식 공개 repository 직접 분석

기준일: 2026-11-08

## 직접 확인한 repositories
- https://github.com/ynab/ynab-sdk-js
- https://github.com/ynab/ynab-api-starter-kit

## ynab-sdk-js
공식 JavaScript API client.
2026-11-05까지 push 확인.

API 영역:
- Plans
- Accounts
- Categories
- Payees
- Months
- Money Movements
- Transactions
- Scheduled Transactions

Category model에서 goal과 funding 상태가 명시적 필드로 존재하고, Transaction에는 approval/clearing/transfer/matching/subtransaction이 존재한다.

MoneyMovement를 별도 resource로 둬 실제 account transaction과 목적별 budget movement를 구분한다.

## ynab-api-starter-kit tree
- src/App.vue
- src/components/Budgets.vue
- src/components/Transactions.vue
- OAuth config
- Vue 3
- webpack
- ynab SDK
- GitHub Pages deployment

README는 초보 개발자가 browser에서 template을 복제하고 OAuth client를 만든 뒤 YNAB API를 사용하는 구조를 설명한다.

## Starter Kit 실제 flow
App.vue 직접 확인:
1. access token 없음 → OAuth authorize
2. token 있음 + budget 미선택 → budgets load
3. budget 선택 → transactions fetch
4. error → Try Again/reset token

즉 example UI도 auth state / selection state / data state / error state로 분기한다.

Transactions.vue:
- Account
- Date
- Payee
- Category
- Memo
- Amount
를 표로 표시.

## 주의
Starter Kit는 YNAB 본체 frontend source가 아니다.

다만 공식 API를 실제로 어떻게 소비하도록 설계했는지와 public domain model을 확인하는 근거로 유효하다.

## Class Money 설계 시사점
- domain model을 UI 문구와 분리하지 말 것
- transaction과 allocation movement 분리
- scheduled rule 별도 resource
- auth/loading/error/selection 상태를 명시
- external integration을 만들더라도 core ledger와 adapter를 분리