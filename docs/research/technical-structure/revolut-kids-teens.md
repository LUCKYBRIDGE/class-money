# Revolut Kids & Teens — 파일·폴더·기술 구조

정확도: **C — 실제 금융제품 source 비공개**

## 공개 source 여부
Revolut 소비자 앱 본체의 공식 public source를 이 조사에서 확인하지 않았다.

## 외부 product hierarchy
- Parent personal account
- Kids & Teens sub-account
- Child app
- Parent management surface
- Co-parent limited management
- card/payment infrastructure

## 논리적 모듈
- parent account link
- child account
- co-parent permissions
- money/top-up
- challenges
- challenge requests
- recurring challenge rules
- rewards
- pockets/goals
- recurring transfers
- analytics
- payment/transfer
- approval rules
- age eligibility
- card controls

## 중요한 technical boundaries

### Account hierarchy
child account가 parent account 아래 sub-account.

### Role hierarchy
Admin parent와 Co-parent 권한 차등.

### Challenge workflow
definition → request → approval → completion → reward.

### Pocket
main spending balance와 분리된 money container.
direct payment availability가 다르다.

### Scheduled transfer
insufficient funds면 skip되는 별도 state가 존재.

## Class Money 대응 모듈
X 제안:
- teacher-owner
- co-teacher-permission
- student-account
- task-request
- approval
- goals/accounts
- scheduled-transfers
- analytics
- feature-eligibility

## 미확인
- native framework
- shared backend architecture
- banking core
- DB/event bus
- payment processor integration
- deployment