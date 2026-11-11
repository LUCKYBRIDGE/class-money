# 앱·웹 분석 및 파일·기술 구조 종합 정리

기준일: 2026-11-11  
대상 저장소: `LUCKYBRIDGE/class-money`  
목적: 놀머니 설계를 위해 지금까지 직접 관찰·검증한 서비스의 UI·UX·기능·상태·기술구조·문제해결 방식을 한 문서에 압축한다.

---

## 1. 이 문서의 역할

이 저장소에는 서비스별로 상세한 Canonical 폴더가 존재한다.

- `docs/research/services/<service>/`
- 페이지/내비게이션
- UI·UX/버튼
- 기능/상태/흐름
- 기술/파일구조
- 복잡성 해결방식
- 근거/미확인

이 문서는 그 모든 분석을 다시 나열하지 않고, **놀머니 개발에 직접 연결되는 공통 패턴과 기술적 시사점**을 정리한다.

---

## 2. 증거 등급

### A — 실제 공식 source 직접 확인
- Craft Anything
- YNAB 공식 SDK / Starter Kit
- 현재 Class Money 저장소 자체

### B — 공식 조직의 부분 source 확인
- Banqer
- ClassDojo

### C — 상용 제품 source 비공개
- ClassCoin
- ClassBank
- Cashroom
- ClassCents
- Greenlight
- Rooster Money
- Revolut Kids & Teens
- 토스 유스

### C+ — 일부 실제 path/file/초기 설계 공개
- 반짝 모의투자

원칙:
- 공개 source가 없으면 `src/components`, React, Firebase, DB schema 등을 임의로 만들어내지 않는다.
- 실제 내부구조가 아니면 반드시 logical module / inferred structure로 표시한다.
- 로그인 뒤 화면을 직접 보지 못한 경우 click depth와 screen layout을 확정하지 않는다.

---

## 3. 서비스별 핵심 분석

| 서비스 | 가장 참고할 부분 | 기술·구조적으로 중요한 점 |
|---|---|---|
| ClassCoin | 기능이 많아진 뒤 복잡도 관리 | 기능 숨김, 설정 재분류, 정책 Preview, 게임재화 분리, 실패상태 보존 |
| ClassBank | 단계형 교실경제 시작 | Classes→Students→Bonuses→Store부터 시작, Job과 Permission 분리 |
| Cashroom | 거래를 학습 순간으로 만듦 | Pending, Hold, disabled reason, Math Check, partial order approval |
| Banqer Primary | 경제개념을 모듈화 | Module Enabled와 Activity Open 분리, Purchase와 Fulfillment 분리 |
| ClassCents | 교사 운영마찰 최소화 | Teacher-only fallback, paste roster, Saved Reason, batch Undo |
| My Classroom Economy | 의미 있는 학습마찰 | 종이장부·계약·수표·경매도구가 UI 역할, 월간 cadence |
| ClassDojo | 초고빈도 교사 입력 | Student/Group selector, Skill preset, 즉시 Undo, Report 분리 |
| Greenlight | 수입 목적배분·세밀권한 | Allocation, Goal, action-level permission, save-time validation |
| Rooster Money | 반복 task와 payout 분리 | Task state와 Payment state 분리, Today/Overdue/Approve, bulk |
| Revolut Kids & Teens | Parent/Child shell 분리 | Owner/Co-manager 권한, Challenge request/approval, Pocket |
| 토스 유스 | 한국형 아동 금융 IA | Available 중심, Goal, 거래회고, Simulation 분리 |
| YNAB | 돈의 위치와 목적 분리 | Account / Category / Transaction / MoneyMovement / ScheduledTransaction |
| 반짝 모의투자 | 교실용 실제시장 체험 | QR login, KR/US, KRW/USD, 환전, 매매일지, 접속시간, Dashboard |

---

## 4. UI·UX에서 반복해서 확인된 좋은 패턴

### 4.1 Progressive Disclosure
처음부터 모든 경제기능을 보여주지 않는다.

권장:
1. 기본 경제
2. 저축·직업·상점
3. 세금·공공경제
4. 시장·투자·대출
5. Simulation Lab

비활성 기능은 회색 잠금메뉴로 잔뜩 남기지 않고 숨기는 편이 낫다.

### 4.2 Task-Oriented Teacher Home
교사 첫 화면은 통계보다 오늘 처리할 업무가 우선.

예:
- 구매 승인 4
- 과업 승인 7
- 실패 급여 1
- 다음 급여 25명
- 시장 시나리오 수업 예약 1

### 4.3 Common Interaction Grammar
관리자 action을 다음 흐름으로 통일한다.

```text
Target / Request
→ Preview
→ Confirm
→ Result
→ Undo / Detail
```

### 4.4 Immediate Undo + Durable Audit
화면에서는 빠르게 Undo를 제공하되 내부적으로는 원거래 삭제가 아니라 reversal을 생성한다.

### 4.5 Role-specific Shell
TeacherShell과 StudentShell은 같은 navigation을 공유하지 않는다.

### 4.6 Disabled Reason
버튼을 비활성화할 때 이유를 보여준다.

예:
- 잔액 부족
- 거래시간 아님
- 승인 대기중
- 시장 마감
- 이미 처리됨
- 환전 필요

### 4.7 Preview Before Automation
급여·세금·이자·일괄지급·시나리오 적용은 실행 전:
- 대상
- 금액
- 예상 변화
- 예외
를 보여준다.

### 4.8 Master View와 Today View 분리
전체 설정과 오늘 해야 할 일을 한 화면에 섞지 않는다.

---

## 5. 경제 도메인 구조에서 반복해서 확인된 핵심

### 5.1 Account와 Purpose를 분리
YNAB/Greenlight/Revolut에서 공통적으로 드러난 패턴.

```text
Account = 돈이 어디에 있는가
Purpose/Goal = 왜 그 돈을 남겨두는가
```

놀머니에서는:
- Available
- Savings
- Goal
- Treasury
- Activity Currency
등을 분리한다.

### 5.2 Transaction과 AllocationMovement를 분리
실제 돈 이동과 “목적 재배분”은 다른 사건이다.

### 5.3 Task State와 Payment State를 분리
Rooster/Greenlight/Cashroom에서 중요한 패턴.

```text
Task
TODO → SUBMITTED → APPROVED

Payment
SCHEDULED → POSTED → FAILED → REVERSED
```

### 5.4 Purchase와 Fulfillment를 분리
구매결제와 실제 교실 보상 수령은 다른 상태다.

### 5.5 Group Selector와 Group Account를 분리
ClassDojo Group은 선택집합이지 공동계좌가 아니다.

놀머니에서도:
- StudentGroup
- GroupFund
를 별도 객체로 둔다.

### 5.6 Schedule Rule와 Run을 분리
급여·이자·세금은:
- 언제 실행할지 정한 Rule
- 실제 특정 날짜 실행인 Run
을 분리한다.

---

## 6. 기술 안정성에서 반드시 가져올 구조

### Ledger
잔액을 직접 덮어쓰지 않는다.

```text
Transaction
└─ Entries[]
```

한 transaction의 entry 합은 0.

### Idempotency
같은 급여/승인/주문이 네트워크 재시도로 두 번 실행되지 않게 한다.

### Reversal
삭제 대신 원거래를 참조하는 반대거래를 만든다.

### Hold
주문/경매/예약에서 실제 결제 전 돈을 예약한다.

### Policy Version
급여·세율·상품가가 바뀌어도 과거 거래는 당시 규칙으로 설명 가능해야 한다.

### Classroom Scope
기본 지갑과 모든 핵심 데이터는 학급 단위로 격리한다.

### Audit
누가/언제/누구에게/왜/얼마/어떤 권한으로 처리했는지 남긴다.

---

## 7. 공개 GitHub / 실제 파일구조에서 확인한 것

### Craft Anything

실제 상위 구조:

```text
apps/
├─ craft-anything
├─ craft-anything-cli
└─ craft-anything-web

crates/
├─ engine
├─ engines
├─ analysis
├─ evidence
├─ formats
├─ ai
├─ mcp
└─ platform
```

핵심 파일:
- `crates/engine/src/clean_room.rs`
- `crates/engine/src/tools/website_tools.rs`
- `crates/engine/src/tools/browser_tools.rs`
- `crates/ai/src/rebuild/study.rs`

배울 점:
- 실행 engine과 AI orchestration 분리
- evidence를 1급 객체로 관리
- clean-room rule을 prompt가 아니라 engine에서 강제
- 웹페이지를 screenshot 한 장이 아니라 route/state graph로 분석

### YNAB Starter Kit

실제 확인 tree:

```text
ynab-api-starter-kit/
├─ .github/
├─ bin/
│  └─ start.js
├─ public/
│  └─ index.html
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

확인 stack:
- Vue 3
- JavaScript
- webpack 5
- OAuth
- YNAB SDK

단, 이는 Starter Kit이며 실제 YNAB 소비자 앱 stack으로 단정하지 않는다.

### Banqer 공개 sample

```text
angular_sample/
├─ README.md
├─ simple-quiz.component.html
├─ simple-quiz.component.ts
└─ simple-quiz.styl
```

README가 obsolete Banqer High interview sample이라고 명시하므로 현재 Primary stack 근거로 사용하지 않는다.

### ClassDojo policies

```text
policies/
├─ README.md
├─ child-privacy.md
├─ premium-features.md
├─ privacy.md
├─ security.md
├─ terms.md
└─ ...
```

현재 Points UI source가 아니라 정책 공개 repo다.

### 반짝 모의투자

현재/개발기에서 확인되는 실제 path:

```text
/API/stock/
├─ ad.html
├─ index.php
├─ teacher_login.php
├─ student_login.html
├─ admin.html
├─ student.html
├─ api_update_student.php
└─ api_delete_student.php
```

초기 개발기 DB 설계안:
- users
- stocks
- holdings
- transactions

현재 제품에는 KR/US, KRW/USD, 환전, 매매일지, 접속시간 기능이 추가되어 초기 schema보다 더 많은 domain이 필요하다.

---

## 8. 현재 연구 저장소 구조

Canonical 분석 시작점:

```text
docs/research/services/
├─ CANONICAL.md
└─ <service>/
   ├─ README.md
   ├─ 01-pages-navigation.md
   ├─ 02-ui-ux-controls.md
   ├─ 03-features-flows.md
   ├─ 04-technical-structure.md
   ├─ 05-complexity-solutions.md
   └─ 06-evidence-unknowns.md
```

기술구조 전용:
- `docs/research/technical-structure/`

직접 관찰:
- `docs/research/direct-inspection/`

횡단 패턴:
- `docs/research/synthesis/`

---

## 9. 놀머니 개발에 가장 직접적으로 가져올 20가지

1. TeacherShell / StudentShell 분리
2. 학생 paste-first roster
3. 학생 QR/short-code 로그인
4. Teacher-only fallback
5. 대상→사유→금액의 빠른 지급
6. 학생/모둠/전체 selector 통일
7. Saved Reason
8. Immediate Undo + Reversal
9. Teacher Inbox
10. Task와 Payment 상태 분리
11. Account와 Goal/Purpose 분리
12. Available 중심 학생 Home
13. 자동화 실행 전 Preview
14. save-time validation
15. Hold
16. Module Enabled와 Activity Open 분리
17. Purchase와 Fulfillment 분리
18. shared-device session
19. 시장/투자를 core economy와 분리
20. 선택→이유→결과→회고 학습루프

---

## 10. 그대로 가져오면 안 되는 것

- 개인 자산 공개순위 기본 ON
- 행동점수를 자동으로 돈으로 환산
- 기본 학습권/좌석/휴식의 상품화
- 벌금 중심 운영
- 확률형 뽑기와 경제자산 연결
- 학생간 자유송금 기본 ON
- 실제시장 수익률을 경제학습 성공으로 간주
- 실제 서비스의 디자인/브랜드/원본 코드 복제

---

## 11. 다음 연구 우선순위

1. 로그인 가능한 서비스의 실제 screen inventory
2. 360 / 768 / 1280 viewport 비교
3. 25명 학급 기준 click count
4. shared-device session 전환
5. 자동급여 실패/재시도
6. Store partial approval/refund
7. 시장 quote freshness/market close 처리
8. 환전 Before/After UX
9. 가상시장 시나리오의 학생 이해도
10. 교사 수업시간 통제 UX

---

## 12. 연구 결론

놀머니의 경쟁력은 기능 개수 자체가 아니다.

핵심은:

> **교사에게는 운영 복잡성을 제거하고, 학생에게는 경제적 선택과 그 결과를 이해하는 데 필요한 복잡성은 남기는 것.**

교사에게 제거할 것:
- 반복입력
- 중복 계산
- 학생별 같은 클릭
- 잘못된 설정의 대량위험
- 실패 복구의 번거로움

학생에게 남길 것:
- 선택
- 예측
- 계산
- 근거
- 위험
- 기회비용
- 결과 해석
- 회고

이 원칙이 놀머니 전체 제품 구조의 기준이 되어야 한다.
