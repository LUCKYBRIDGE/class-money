# YNAB 직접 관찰

기준일: 2026-11-08

## 직접 연 사이트/문서
- https://www.ynab.com/
- https://support.ynab.com/en_us/getting-started-ynab-basics-and-key-terms-BJCaIHaTZe
- https://support.ynab.com/en_us/getting-started-assigning-your-money-in-ynab-SyHCkywTZl
- https://support.ynab.com/en_us/the-plan-header-BkmiuJ_C9

## 공개 UI mental model
공식 Getting Started는 YNAB를 두 주요 장소로 설명한다.
- Home: recent activity, upcoming expenses, overall picture
- Plan: category에 돈을 배정하고 계획

돈의 흐름:
Account / Income → Ready to Assign → Category → Available → Spending.

핵심 질문은 What is this money for?

## Ready to Assign
실제로 가진 cash 중 아직 목적이 정해지지 않은 금액.

상태:
- positive → assign 필요
- hidden/not showing → 모두 배정
- negative → Fix This

상태에 따라 action이 달라진다.

## Auto-Assign
공식 Help에서:
- Underfunded
- Spent Last Month
- Budgeted Last Month
- Average Spending
등을 제공한다.

Web에서는 Auto-Assign을 선택하면 Preview window가 나타나고 확인 후 Assign Money.

자동화가 즉시 실행이 아니라 **proposal → review → commit** 구조다.

## 공개 GitHub source 직접 확인
공식:
- https://github.com/ynab/ynab-sdk-js
- https://github.com/ynab/ynab-api-starter-kit

ynab-sdk-js는 2026-11-05까지 push가 확인되고 Official JavaScript client로 설명된다.

## Public API domain
직접 tree/README에서:
- Plans
- Accounts
- Categories
- Payees
- Months
- Money Movements
- Transactions
- Scheduled Transactions

## Category model
직접 model file에서:
- budgeted
- activity
- balance
- goal_type
- goal_target
- goal_target_date
- goal_percentage_complete
- goal_under_funded
- goal_overall_funded
- goal_overall_left

UI의 Assigned / Available / Target / Underfunded가 실제 domain model과 연결된다.

## Transaction model
직접 model에서:
- date
- amount
- approved
- cleared
- account
- payee
- category
- transfer pair
- matched transaction
- debt type
- subtransactions

## MoneyMovement
별도 객체로:
- from_category_id
- to_category_id
- amount
- performed_by_user_id
- moved_at

중요: **실제 계좌 transaction과 목적별 예산 이동을 분리**한다.

## Scheduled Transaction
미래에 발생할 예정 거래도 실제 transaction과 별도 resource.

## Class Money에 가져올 것
- Account와 Purpose 분리
- Available 중심 student UI
- AllocationMovement
- Goal을 domain object로
- ScheduledRule 분리
- Previewable automation
- Home vs Plan 분리
- reconcile/reflection

## 가져오지 않을 것
- 성인 신용카드/은행 import 복잡도
- 무제한 category customization
- 실제 금융계좌 연결