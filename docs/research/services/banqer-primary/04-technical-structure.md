# Banqer Primary — 파일·폴더·기술 구조

**증거 수준:** B — 공식 조직 부분 source는 확인, 현재 Primary 본체 source는 비공개

## 공식 GitHub organization

- github.com/Banqer

## 직접 확인한 공개 repository

### Banqer/angular_sample

실제 확인한 파일:

```text
angular_sample/
├─ README.md
├─ simple-quiz.component.html
├─ simple-quiz.component.ts
└─ simple-quiz.styl
```

README가 이 코드를:
- 과거 Banqer High의 obsolete code
- interview discussion용 sample

이라고 명시한다.

따라서 **현재 Banqer Primary의 source tree가 아니다.**

simple-quiz.component.ts에서 확인되는 과거 sample 패턴:
- Angular Component
- Input questions
- Output completion event
- BrowserStorage로 question index 저장
- correct / incorrect callback
- question validation

### Banqer/ui-select-banqer

Angular 1.5용 historical working copy. 현재 Primary stack 근거로 쓰지 않는다.

## 현재 제품에서 외부로 확인되는 logical module

```text
Banqer Primary
├─ Teacher Dashboard
├─ Student Dashboard
├─ Module / Expansion Registry
├─ Classroom Module State
├─ Banking
├─ Savings
├─ Tax
├─ Property / Insurance / Transport
├─ Class Store
│  ├─ Inventory
│  ├─ Cart
│  ├─ Checkout
│  └─ Fulfillment / Claim
└─ Learning Content
   ├─ Video
   ├─ Quiz
   └─ Group Activity
```

이 tree는 실제 내부 폴더명이 아니라 공개 동작에서 확인되는 모듈 경계다.

## 기술적으로 중요한 상태 분리

- Module Enabled / Disabled
- Activity Open / Closed
- Payment Completed
- Fulfillment Pending / Claimed / Declined

## Class Money 기술 대응

```text
domain/
├─ modules/
├─ classroom-module-state/
├─ store/
├─ inventory/
├─ orders/
├─ fulfillment/
└─ learning-content/
```

## 현재 확인 불가
- 현재 frontend framework
- backend/runtime
- database
- API topology
- scheduler/queue
- hosting
