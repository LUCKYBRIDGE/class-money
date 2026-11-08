# Greenlight 직접 관찰

기준일: 2026-11-08

## 직접 연 페이지
- https://greenlight.com/
- https://help.greenlight.com/hc/en-us/articles/360023614253-How-do-I-set-up-an-allowance-for-my-child
- https://help.greenlight.com/hc/en-us/articles/50527840580379-How-do-I-pay-my-child-per-chore-and-split-the-earnings
- https://help.greenlight.com/hc/en-us/articles/360009173153-How-do-Savings-Goals-work-How-do-I-set-them-up
- https://help.greenlight.com/hc/en-us/articles/45088782307867-How-do-I-manage-my-child-s-account-permissions

## 홈페이지에서 직접 확인한 제품 구조
Family Finance를 Spending / Saving / Investing / Chores & Allowance 등으로 나누면서 Parent guardrail을 전제로 설명한다.

아동에게 완전 자율 또는 완전 통제를 주는 대신 **행동 단위의 권한과 목적별 돈 분리**를 사용한다.

## Allowance Setup
공식 Help에서:
1. child dashboard
2. Set up allowance
3. amount
4. weekly / every two weeks / monthly
5. payout day
6. allocation

Allowance를 Spend Anywhere / General Savings / Giving / Invest 등으로 자동분배할 수 있다.

핵심은 돈을 받은 뒤 나중에 생각하는 것이 아니라 **수입 시점에 목적을 배분**한다는 점이다.

## Allocation Validation
Pay-per-chore에서는:
- category별 percentage 또는 fixed amount
- total allocation must equal 100%
- 여러 child에게 공통 category가 없으면 error
를 저장 전에 검사한다.

Class Money에서 payroll/tax/allocation 설정도 invalid config를 save 이후가 아니라 save 이전에 잡아야 한다.

## Savings Goal
Goal에는 목적, 목표액, progress, round-up, private 설정이 있고 Goal에서 돈을 빼려면 보호자 승인 요청이 필요할 수 있다.

즉 Goal은 장식용 progress bar가 아니라 **money movement permission과 연결된 객체**다.

## Permission
자녀별 toggle:
- shareable savings goal
- transfer out of savings
- sibling transfer
- Paylink

권한을 role 하나로 뭉치지 않고 action별로 분해한다.

## 공개 GitHub 판정
greenlight 이름의 공식 organization에서 현재 소비자 제품 본체 source는 확인하지 못했다.

## Class Money에 가져올 것
- income allocation
- purpose bucket
- Goal과 withdrawal permission 연결
- action-level permission
- save-time validation
- child/teacher view 분리

## 교육적 주의
가정 chores 모델을 그대로 교실에 가져와 모든 공동체 행동을 돈으로 환산하면 안 된다.

Class Money는 무보수 공동책임 / 정기 직업 / 추가 유급 task를 분리해야 한다.