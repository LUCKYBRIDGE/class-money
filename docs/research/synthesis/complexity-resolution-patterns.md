# 복잡한 기능을 풀어내는 제품 패턴 — 서비스 횡단 분석

기준일: 2026-11-08

이 문서는 서비스별 기능을 다시 나열하지 않는다. **복잡한 시스템을 사용자가 쉽게 이해하고 조작하게 만든 방법**을 패턴 단위로 추출한다.

## 1. 복잡성에는 서로 다른 종류가 있다

| 복잡성 | 의미 | 대표 서비스 |
|---|---|---|
| 기능 복잡성 | 메뉴/기능 수가 많음 | ClassCoin, Banqer |
| 거래 복잡성 | 같은 돈 이동이 여러 기능에서 발생 | Cashroom, YNAB |
| 운영 복잡성 | 교사가 많은 학생을 반복 관리 | ClassCents, ClassDojo |
| 권한 복잡성 | 관리자/학생/보조역할의 가능 행동이 다름 | ClassBank, Greenlight, Revolut |
| 시간 복잡성 | 급여/과업/청구가 반복 스케줄로 실행 | Rooster, ClassCents, Cashroom |
| 학습 복잡성 | 기능을 이해하는 것과 개념을 배우는 것이 다름 | Banqer, Cashroom |
| 상태 복잡성 | 대기/승인/완료/실패/환불 상태 | Cashroom, Rooster |
| 경제 복잡성 | 소득/지출/저축/세금/자산이 상호영향 | ClassCoin, Banqer, YNAB |

Class Money는 이 모든 복잡성을 동시에 다뤄야 한다.

---

## 2. Pattern A — Progressive Disclosure

### 문제
기능이 많다고 처음부터 전부 보여주면 사용자는 시작하지 못한다.

### 확인된 사례
- ClassBank: Class/Students/Bonuses/Store부터 시작하고 Jobs/Bills/Savings를 나중에 추가.
- Banqer: 경제개념별 Expansion.
- ClassCoin: 실험실/놀이 카드 숨김.
- YNAB: 사용 가능한 맥락에 따라 Auto-Assign 노출.

### Class Money
세 단계:
1. Starter: 학생/지급/상점/장부
2. Economy: 직업/급여/저축
3. Simulation: 세금/시장/대출 등

**규칙:** 비활성 기능은 메뉴에 회색 잠금으로 잔뜩 남기지 않는다.

---

## 3. Pattern B — Task-Oriented Home

### 문제
기능별 메뉴는 “어디에 있는지”는 알려주지만 “오늘 무엇을 해야 하는지”는 알려주지 않는다.

### 확인된 사례
- Cashroom: One Bell.
- Rooster: Today’s Chores.
- Greenlight: Chores Progress / Pending Review.
- ClassCoin: 실패알림 재조회 같은 actionable notification.

### Class Money Teacher Home
**오늘 처리할 것**
- 구매승인 4
- 과업승인 7
- 직업지원 2
- 실패 급여 1
- 금요일 지급예정 25

통계는 그 아래.

---

## 4. Pattern C — Common Interaction Pattern

### 문제
기능별로 다른 UI를 만들면 학습비용이 계속 증가.

### 확인된 사례
Cashroom은 paycheck/bill/purchase/fine을:
Pending → Math Check → Record
로 통일.

ClassCents는 개인/그룹/전체 지급을:
Target → Reason → Amount
로 통일.

### Class Money 공통 명령 흐름
Request/Action → Preview → Confirm → Result → Undo/Detail.

가능한 모든 관리자 action에 재사용.

---

## 5. Pattern D — 목적을 중심으로 돈을 나눔

### 문제
총잔액은 자산상태를 보여주지만 선택을 돕지 못한다.

### 확인된 사례
- YNAB: Ready to Assign / Available / Targets.
- Greenlight: Spend / Savings / Give / Goal.
- Revolut: spending money와 Goal 분리.
- 토스: 사용가능액 + 저금통.

### Class Money 학생 Home
- 지금 쓸 돈
- 모아둔 돈
- 목표
- 공동체
- 아직 계획하지 않은 돈

총자산은 secondary.

---

## 6. Pattern E — Preview Before Automation

### 문제
자동화는 편하지만 잘못된 설정이 여러 학생에게 대량 영향을 미친다.

### 확인된 사례
- ClassCoin: 누진세/세제혜택 저장 전 학생별 예시.
- YNAB: Auto-Assign Preview.
- ClassCents: 전체 대상 지급이 명확한 total context.
- Greenlight: allocation 100% validation.

### Class Money
대량/자동 action:
- 대상 학생 수
- 1인 금액
- 총액
- 전/후 상태
- 실패예상
- 적용 날짜
를 preview한 뒤 실행.

---

## 7. Pattern F — Immediate Undo + Durable Audit

### 문제
빠른 업무는 실수가 자주 발생.

### 확인된 사례
- ClassDojo: 최근 point 즉시 Undo, 과거는 Reports.
- ClassCents: Give/Deduct Undo.
- Cashroom: plain transaction vs connected object 복구 분리.

### Class Money
직후:
snackbar Undo.

내부:
원 거래 삭제 X.
reversal transaction.

연결 거래:
구매 → refund + stock.
급여 → reversal.
대출 → schedule correction.

---

## 8. Pattern G — 역할별 Shell

### 문제
같은 시스템을 교사와 학생에게 같은 Navigation으로 보여주면 한쪽은 불필요한 기능이 많아진다.

### 확인된 사례
- Revolut: parent app vs Kids & Teens app.
- 토스: Youth-specific experience.
- Banqer: Teacher vs Student Dashboard.
- ClassBank: Helper별 영역.
- Greenlight: parent/child/shared Hub.

### Class Money
TeacherShell과 StudentShell을 별도 IA로 설계.

같은 컴포넌트를 재사용할 수 있지만 navigation과 primary action은 별도.

---

## 9. Pattern H — 위험 기반 승인

### 문제
모든 행동을 교사 승인하면 Inbox가 폭발. 전부 자율이면 사고 위험.

### 확인된 사례
- Revolut: 일부 payment/연령조건에 승인.
- Greenlight: savings transfer 등 permission별 승인.
- Banqer: teacher item claim.
- Cashroom: store/loan application.

### Class Money
자동:
- 자기 지갑→자기 저축
- 저가 기본상점(설정 시)

승인:
- 학생간 송금
- 고액구매
- helper transaction
- 대출/경매.

---

## 10. Pattern I — Task State와 Payment State 분리

### 문제
“업무 완료”와 “돈 지급 완료”를 한 boolean으로 쓰면 오류 복구 불가.

### 확인된 사례
- Rooster: To Do / Submitted / Re-open / Not Done / Skip + allowance payout.
- Greenlight: To Do / Pending Review / Paid.
- Cashroom: job/application/paycheck/pending 별도.

### Class Money
Task:
TODO → SUBMITTED → APPROVED.

Payment:
PENDING → POSTED → REVERSED.

Task approved지만 payment failed인 상태를 표현 가능해야 한다.

---

## 11. Pattern J — 전체 관리 View와 Today View 분리

### 확인된 사례
- Rooster: Master Chores vs Today.
- Cashroom: full functions vs One Bell.
- YNAB: full plan vs focused action.
- ClassCoin: 가계부 기간조회.

### Class Money
Manager screen:
전체 Jobs / Store / Ledger.

Home:
오늘/이번주 action만.

---

## 12. Pattern K — 학습에 필요한 마찰만 남김

### 확인된 사례
- My Classroom Economy: ledger/은행절차 자체가 학습.
- Cashroom: 잔액 계산.
- Banqer: 기능마다 학습활동.

### Class Money
자동화할 것:
- 합계
- 중복방지
- 스케줄 실행
- 잔액 검증

학생에게 남길 것:
- 예상
- 선택
- 계획
- 이유
- 회고.

---

## 13. Pattern L — Shared Device를 1급 요구사항으로

### 확인된 사례
- ClassCents: email 없는 Login Card.
- Cashroom: student/teacher session expiry.
- Rooster: switch user.
- Banqer: browser/mobile-friendly.

### Class Money
- 개인 이메일 필수 X
- student switch
- 자동 잠금
- QR+PIN
- 이전학생 정보 masking
- 교사 단독 운영 fallback.

---

## 14. Pattern M — 물리적 인터페이스와 출력물

My Classroom Economy는 앱이 없기 때문에 오히려:
- paycheck
- job card
- bank log
- auction paddle
가 역할을 명확히 만든다.

### Class Money
Printable:
- 로그인 카드
- 직업 카드
- 월급명세
- 경제 규칙
- 상점표
- 국고 보고서
- 학기결산.

웹만으로 수업을 닫지 않는다.

---

## 15. Pattern N — 경제와 게임의 재화 경계

ClassCoin에서 일부 게임재화 분리가 확인되고, Rooster도 stars/money를 구분한다.

### Class Money
경제학습 화폐와 cosmetic/game reward를 가능하면 분리.

게임 참여가 student purchasing power를 과도하게 결정하지 않도록 한다.

---

## 16. Pattern O — 행동점수와 경제자산 경계

ClassDojo는 행동피드백에 매우 효율적이지만 이것을 경제화폐와 동일하게 두면 평가가 자산으로 변한다.

### Class Money
기본:
경제소득 = 참여 + job + task.

Behavior:
feedback/badge 별도.

Bonus-to-money는 선택형이며 상한/편중 경고.

---

# Class Money UI 시스템으로 번역

## Teacher UX primitives
- StudentSelector
- GroupSelector
- ReasonPreset
- MoneyInput
- BatchPreview
- ApprovalQueue
- SchedulePicker
- TransactionDetail
- ReversalFlow
- EconomyHealth
- ModuleToggle

## Student UX primitives
- AvailableBalanceCard
- IncomeEvent
- BeforeAfterMoney
- GoalCard
- TaskCard
- PurchasePreview
- PendingAction
- Receipt
- WeeklyReflection
- TransactionTimeline

## 공통 상태표현
- 예정
- 해야 함
- 확인 중
- 승인됨
- 처리됨
- 실패
- 취소됨
- 환불됨
- 정정됨
- 만료됨

## 설계의 최종 기준

**교사에게서 제거할 것:** 반복 계산, 반복 입력, 메뉴 탐색, 중복 확인.  
**학생에게 남길 것:** 선택, 예상, 결과 이해, 목표, 회고.

이 원칙이 서비스들에서 반복해서 확인되는 가장 강한 공통점이다.
