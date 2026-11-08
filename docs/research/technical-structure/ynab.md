# YNAB — 파일·폴더·기술 구조

정확도:
- **A**: 공식 JavaScript SDK / API model
- **B**: 공식 Starter Kit
- **C**: 실제 YNAB 소비자 앱 본체 source는 비공개

## 공식 공개 repositories

### ynab/ynab-sdk-js
공식 JavaScript client.

공개 API domain:
- Plans
- Accounts
- Categories
- Payees
- Months
- Money Movements
- Transactions
- Scheduled Transactions

직접 확인한 model 예:
- Category
- TransactionDetail
- MoneyMovement
- PlanDetail

### ynab/ynab-api-starter-kit
공식 API 학습/시작용 web app.

## Starter Kit 실제 tree

- .github/
  - CODEOWNERS
  - dependabot.yml
  - workflows/
- bin/
  - start.js
- public/
  - index.html
  - works_with_ynab.svg
- src/
  - App.vue
  - config.json
  - main.js
  - components/
    - Budgets.vue
    - Footer.vue
    - Nav.vue
    - Transactions.vue
- package.json
- webpack.config.js

## 확인된 Starter Kit stack

package.json 직접 확인:
- Vue 3
- webpack 5
- JavaScript
- ynab SDK
- GitHub Pages deployment
- OAuth

중요: 이 stack은 **Starter Kit의 stack**이며 실제 YNAB 본체 frontend stack이라고 단정하지 않는다.

## App.vue 상태구조

1. token 없음 → OAuth authorization
2. token 있음 / plan 미선택 → Plans 목록
3. plan 선택 → Transactions fetch
4. loading
5. error → reset token / retry

즉 공개 sample도 Auth / Loading / Selection / Data / Error 상태를 분리한다.

## Domain model에서 확인된 기술적 분리

### Account
돈이 실제 위치한 곳.

### Category
돈의 목적/계획.
goal_target, goal_under_funded, goal_percentage_complete 등 goal 상태 포함.

### Transaction
실제 account money event.
approved, cleared, account, payee, category, transfer pair, matched transaction 등.

### MoneyMovement
category → category 예산 이동.
실제 account transaction과 분리.

### ScheduledTransaction
미래 transaction rule/resource.

## Class Money 기술구조에 직접 유용한 점

- Account와 Allocation/Goal 분리
- Transaction과 AllocationMovement 분리
- ScheduledRule 분리
- status를 boolean 하나로 뭉치지 않음
- API domain과 UI mental model을 연결