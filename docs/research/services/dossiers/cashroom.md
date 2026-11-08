# Cashroom Product Anatomy

기준일: 2026-11-08  
범위: 공식 홈페이지·Help Center·Pricing.  
대상: middle school 중심 classroom economy.  
실측 상태: 공개 화면 설명 기반, 실제 계정 전수 실측은 미완료.

## 1. 제품 경계와 정체성

**E1 확인**  
Cashroom은 ‘교실경제를 자동화하는 앱’이면서 동시에 거래 순간마다 학생이 새 잔액을 계산하게 하는 수학·금융 학습 도구다.

주요 기능:
- Student job
- Job applications
- Paychecks
- Bills
- Bonuses / Fines
- Store
- Coupons
- Auctions
- Checking
- Savings / Goals / Interest
- Loans / Credit score
- Badges
- Transaction history / Undo
- Export
- Teacher notification bell
- Per-student math check accommodation

제품의 독특한 핵심은 **돈이 움직이기 전에 학생이 결과 잔액을 계산**한다는 점이다.

## 2. 사용자 역할

### Teacher
경제 규칙 설정, job/payday/bills, 보너스/벌금, 상점·대출·경매 승인, math check 개별 설정, 거래 정정.

### Student
직업지원, pending transaction 계산/기록, 상점 구매, 쿠폰, 경매, 저축, 목표, 대출 신청, badges 확인.

**I 추론**
Cashroom은 교사와 학생의 업무를 ‘관리’와 ‘기록’으로 명확히 분리한다.
- 시스템/교사: 사건을 만든다.
- 학생: 사건을 계산하고 기록한다.

## 3. 핵심 도메인 객체

- Class
- Student
- Job / Student default job
- Job application
- Paycheck
- Bill
- Bonus / Fine
- Pending transaction
- Checking account
- Savings account
- Savings goal
- Interest rule
- Store item
- Order
- Coupon
- Auction
- Bid
- Loan
- Credit score / payment status
- Badge
- Notification
- History entry

## 4. 전체 기능 구조

~~~mermaid
flowchart TD
  J[Jobs] --> P[Paychecks]
  B[Bills] --> PN[Pending]
  P --> PN
  BF[Bonus/Fine] --> PN
  ST[Store Purchase] --> PN
  PN --> MC[Math Check]
  MC --> CH[Checking]
  CH --> SV[Savings]
  SV --> GL[Goal]
  CH --> AU[Auction]
  CH --> LO[Loan]
  LO --> CR[Credit]
  CH --> HI[History]
  SV --> HI
  AU --> HI
  LO --> HI
  N[Teacher Bell] --> J
  N --> ST
  N --> LO
  N --> CR
~~~

## 5. Cashroom의 핵심 추상화: Pending

**E1 확인**
Paycheck, bill, purchase, fine 등 돈이 들어오거나 나가는 사건은 바로 최종잔액이 되지 않고 Pending으로 나타날 수 있다. 학생은 가장 오래된 항목부터 새 잔액을 계산해 기록한다.

Pending이 남아 있으면 store/coupon/bid 같은 일부 소비 기능이 제한된다.

### 왜 중요한가
복잡한 기능들을 하나의 공통 UX로 통합:
경제 이벤트 → Pending → 계산 → Record → Balance.

기능마다 완전히 다른 입력화면이 필요하지 않다.

### 리스크
결석 학생에게 pending이 쌓이면 인지 부담이 커질 수 있다.

### D Class Money
Math Check는 수업모드/학생별 설정으로 선택.
교사는 absent student의 pending을 대신 record 가능.

## 6. Math Check UI

공식 공개 예:
- Checking was 41.25
- Paycheck +5.00
- “What is it now?”
- 입력
- Record it

오답:
- 불이익 없음
- 다시 시도
- 두 번째 miss 이후 hint

**UX 강점**
- 한 화면 한 문제.
- +/− 방향이 명확.
- 오류를 벌하지 않음.
- 금융 이벤트를 실제 산수문제로 변환.

### D Class Money 학년별
- 1–2: 보기 선택
- 3–4: 직접 계산
- 5–6: 직접 계산 + 식/이유
- 지원학생: OFF 또는 guided

## 7. 교사 Bell — Task-oriented IA

**E1 확인**
Job applications, loan requests, store orders, students below zero 등이 한 bell에 모인다.

이것은 기능별 dashboard가 아니라 **교사가 지금 처리할 일**을 중심으로 한 IA다.

### D Class Money
교사 Home 상단:
- 구매 승인
- 과업 승인
- 직업지원
- 실패 거래
- 예정 급여
를 하나의 Work Queue로.

## 8. Jobs

Student job:
- 모든 학생이 자동으로 가질 수 있음
- teacher가 금액 설정/비활성화

Additional job:
- 공개 job 선택
- 2개 짧은 질문 답변
- 교사가 hire/pass
- job limit 설정

### 구조적 장점
기본 참여소득과 추가 직업소득이 분리된다.

Class Money에서 매우 적합:
Base Participation Income + Job Income.

## 9. Payday / Bills 자동화

**E1 확인**
Paydays와 bills는 정해진 스케줄에 자동으로 실행되고 아무도 로그인하지 않아도 동작한다.

자동화가 학생의 학습을 없애지는 않는다. 결과는 Pending으로 남아 학생이 기록한다.

**핵심 원칙**
Backend는 자동화, 학생의 이해는 자동화하지 않는다.

## 10. Store / Order

공개 Help:
- 학생 구매
- 교사 approve
- 승인결과 message
- 거절 시 돈과 coupon 반환
- receipt

상태 모델 추론:
REQUESTED → RESERVED/PENDING → APPROVED → FULFILLED  
REQUESTED → REJECTED → REFUNDED.

### D Class Money
주문 요청 시 사용가능액 hold를 권장.
승인 시 settlement.
거절/취소 시 release.

## 11. Undo / Reversal

**E1 확인**
- bonus/fine/plain transaction: History에서 undo
- purchase/loan/auction: 해당 화면에서 reverse

이 구분이 매우 중요하다.

연결된 객체가 있는 거래는 잔액만 되돌려서는 안 된다.

### D Class Money
History의 ‘정정’은 transaction type에 따라:
- 지급 → reversal
- purchase → refund + stock restore
- auction → winning/bid state restore
- loan → repayment schedule correction
으로 라우팅.

## 12. Savings / Goal

- checking↔savings 이동
- goal 이름/금액
- progress bar
- teacher가 savings interest 설정 가능

Class Money:
Savings는 ‘총잔액에서 숨기는 돈’이 아니라 목적/선택을 보이는 공간.

## 13. Loans / Credit

Cashroom:
- credit score 300–850
- on-time payment
- loan request
- I = Prt 계산
- weekly repayment

### 교육적 가치
신용·이자·채무를 실제 흐름으로 경험.

### 초등 Class Money 위험
- 점수가 학생 정체성/평가처럼 보일 수 있음.
- 부채를 게임으로 받아들일 가능성.
- 수학 난도 과다.

따라서 5–6학년 선택 Simulation Lab으로만 검토.

## 14. Badges

자동 badge 예:
- first paycheck
- saving amount
- math check streak
- loan payoff

좋은 게임화:
랜덤 reward보다 **경제적 행동의 milestone**을 시각화.

Class Money badge 후보:
- 첫 저축
- 첫 예산계획
- 첫 국고투표
- 거래오류 스스로 발견
- 4주 목표 유지

## 15. 인증 / 공유기기

공식 Help:
- starter code
- teacher password reset
- 5회 오류 후 15분 잠금
- 학생 3시간, 교사 12시간 session expiry
- Chromebook/phone browser 지원

**구조적 장점**
공유기기를 실제 사용환경으로 고려.

Class Money:
- 학생 바꾸기 항상 노출
- 수업 종료 일괄 logout
- 짧은 개인 PIN
- previous student info 즉시 가림

## 16. 오류·예외 처리

공개된 예:
- wrong math → retry/hint
- student absent → teacher record
- below zero → spending restrictions + teacher alert
- rejected order → refund
- wrong award → undo
- password guessing → timed lockout

Cashroom은 정상경로뿐 아니라 **실패 이후 다음 행동**을 비교적 명확히 정의한다.

## 17. 복잡성을 풀어낸 핵심 패턴

1. 서로 다른 돈 이동을 Pending/Math Check로 통일
2. 여러 요청을 One Bell로 통합
3. 학생별 accommodation
4. plain vs connected transaction의 복구 경로 분리
5. 자동화와 학생 확인단계 분리
6. shared-device session 설계
7. 상태 기반 기능 제한

## 18. Class Money에 가져올 것

**가장 강하게**
- Teacher Inbox
- transaction before/after
- optional math check
- Student base income
- connected reversal
- receipt
- per-student support
- shared-device safety

**추후**
- coupons
- auctions
- badges

**P3**
- credit score
- loans

## 19. Craft Anything 실측

- Student Home 전체 IA
- Pending card 밀도
- Math Check 오답/힌트
- math-check OFF 학생 비교
- order approval 실제 화면
- History undo
- Bell 우선순위
- savings/goal 화면
- mobile 360px
- shared Chromebook login/logout
- failure state visual language

## 20. 현재 판단

Cashroom의 가장 큰 장점은 기능수가 아니라 **다른 종류의 경제 사건을 하나의 학습 인터랙션으로 통일한 것**이다. Class Money의 transaction UX를 설계할 때 가장 중요한 비교 대상이다.

## 공식 근거
- https://cashroomapp.com/
- https://cashroomapp.com/help
- https://cashroomapp.com/pricing
