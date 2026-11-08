# YNAB — 파일·폴더·기술 구조

**증거 수준:** A/B — 공식 SDK와 Starter Kit 공개, 소비자 앱 본체는 비공개

## 공식 공개 repository

### 1. ynab/ynab-sdk-js
공식 JavaScript API client이며 2026-11-05까지 push를 확인했다.

공개 API domain:
- Plans
- Accounts
- Categories
- Payees
- Months
- Money Movements
- Transactions
- Scheduled Transactions

직접 확인한 model:
- Category
- TransactionDetail
- MoneyMovement
- PlanDetail

### 2. ynab/ynab-api-starter-kit

실제 tree:

```text
ynab-api-starter-kit/
├─ .github/
│  ├─ CODEOWNERS
│  ├─ dependabot.yml
│  └─ workflows/
├─ bin/
│  └─ start.js
├─ public/
│  ├─ index.html
│  └─ works_with_ynab.svg
├─ src/
│  ├─ App.vue
│  ├─ config.json
│  ├─ main.js
│  └─ components/
│     ├─ Budgets.vue
│     ├─ Footer.vue
│     ├─ Nav.vue
│     └─ Transactions.vue
├─ package.json
└─ webpack.config.js
```

## 확인된 Starter Kit 기술

package.json 직접 확인:
- Vue 3
- JavaScript
- webpack 5
- ynab SDK
- OAuth
- GitHub Pages deployment

> 이 stack은 Starter Kit의 기술구조다. 실제 YNAB 소비자 앱 frontend stack이라고 단정하지 않는다.

## App.vue에서 확인한 상태 흐름

```text
No Token
→ OAuth Authorization
→ Plans Load
→ Plan Select
→ Transactions Load

각 단계에:
Loading
Error
Retry / Reset
상태 존재
```

## Domain model에서 확인한 분리

### Account
실제 돈의 위치.

### Category
돈의 목적. goal_target, goal_under_funded, goal_percentage_complete 등 Goal 상태 포함.

### Transaction
실제 account money event.
approved, cleared, account, payee, category, transfer pair, matched transaction, subtransactions 등.

### MoneyMovement
Category → Category 목적 이동. 실제 account transaction과 별도.

### ScheduledTransaction
미래 예정 거래. posted transaction과 별도 resource.

## Class Money 기술 대응

```text
domain/
├─ accounts/
├─ allocations/
├─ goals/
├─ ledger/
│  ├─ transactions
│  └─ reversals
├─ allocation-movements/
└─ schedules/
```

핵심 원칙은 YNAB 코드를 복제하는 것이 아니라 **돈의 위치·목적·실제 이동·미래 규칙을 같은 객체에 합치지 않는 것**이다.

## 현재 확인 불가
- 실제 YNAB consumer frontend tree
- backend services
- DB
- internal event processing
