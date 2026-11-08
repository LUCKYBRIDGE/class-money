# 경쟁 서비스 공개 사이트 직접 관찰 — 2026-11-08

검색결과 요약이 아니라 공개 URL과 공식 Help/PDF를 실제로 열어 현재 노출되는 구조·순서·상태를 관찰한 기록이다.

로그인 뒤 화면은 별도 표시가 없는 한 L0 미확인이다.

## 1. ClassCoin

대상: https://classcoin.me/

### S1 첫 페이지

Hero가 제품을 바로 두 축으로 정의한다.
- 학급 자동화
- 교실 속 작은 경제

첫 진입도 역할별로 분리한다.
- 교사: Kakao / Google
- 학생: 학급코드

경제 기능 소개에서는 세금, 저축, 투자, 급여, 경매, 창업, 부동산을 한 묶음으로 제시한다.

페이지 설명 순서는 대체로:
제품 정체성 → 교사/학생 진입 → 최근 업데이트 → Kiosk 점수판 → 학급경영 → 경제 기능.

즉 경제기능 자체보다 **교사가 매일 쓰는 수업운영 surface를 먼저 앞세운 뒤 경제 세계를 확장**한다.

### S1 2026-10-26 현재 업데이트에서 확인

- 학생 메뉴 left expand/scroll 개선
- 설정을 학급/활동/소통으로 재구성
- 실험실 메뉴 및 놀이 카드 숨김
- Dashboard 학생선택 개선
- 가계부 최근 3일 우선 + 기간 변경
- 누진세/세제혜택 저장 전 학생별 금액 예시
- 국고 정기지출
- 팜코인과 학급화폐 분리 가능
- 자동 전환하지 않으며 보존/소멸을 안내

### 구조적 판단

ClassCoin은 기능이 많아진 뒤 실제로 **숨김, 재분류, 영향 미리보기, 재화분리**를 UX 해법으로 사용하고 있다.

Class Money는 고급기능을 추가하기 전에 이 네 가지를 먼저 구조에 넣는 편이 좋다.

---

## 2. ClassBank

대상: https://www.classbank.com/

### S1 홈페이지

How ClassBank Works가 먼저 네 가지 행동으로 제품을 압축한다.
- Award Bonuses
- Assign Jobs
- Charge Bills
- Manage your Store

그 뒤 bank account, financial literacy, PBIS, school/district로 확장한다.

기능 총목록을 먼저 보여주지 않고 **네 가지 mental model**로 시작한다.

### D1 Getting Started

2026-08-18 갱신본에서 약 15분 setup을 제안한다.

먼저:
1. Classes
2. Students
3. Bonuses
4. Store

선택적으로:
5. Jobs
6. Bills
7. Savings / Interest
8. Co-teachers

### D1 학생 등록 경로

- Class Code self-signup
- Manual
- Spreadsheet import
- School subscription search

학교마다 roster 환경이 다르다는 문제를 **여러 onboarding path**로 해결한다.

### D1 실제 menu path

- Class → Setup → Bonuses/Fines
- Class → Store → All Items
- Class → Jobs → Add Job
- Setup → Bills
- Blue Panel gear → Edit Class → Savings
- Class → Co-Teacher

### 구조적 판단

Progressive Disclosure가 실제 제품 운영 가이드에 명확하다.

추가로 설정이 중앙 Settings 한 곳에만 있는 것이 아니라 **각 기능 맥락에 분산**되어 있다. Class Money는 기능 내부 설정의 장점은 유지하되 중앙의 '경제 기능 상태' 화면에서 ON/OFF와 바로가기를 한 번에 볼 수 있게 하는 것이 낫다.

---

## 3. Cashroom

대상: https://cashroomapp.com/

### S1 Homepage

Hero 바로 아래에 실제 Math Check 형태의 interactive demo가 있다.

표시되는 핵심:
- Checking Pending
- Paycheck
- 이전 checking
- 새 balance 입력
- Record it

그리고 paycheck, purchase, fine, bill마다 같은 단계를 수행한다고 설명한다.

제품 서술 순서도:
Earn → Pay bills → Spend → Save → Borrow.

교사용 가치는:
- Paydays/bills run themselves
- One bell
- per-student Math Check accommodation
- Undo/history
- Export
로 설명한다.

### D1 Help에서 직접 확인한 상태 규칙

Pending:
- 가장 오래된 항목부터 처리
- Pending이 있으면 store/coupon/bid 제한

Math error:
- penalty 없음
- retry
- 두 번째 오답 뒤 hint
- absent student는 teacher가 대신 record 가능
- 학생별 Math Check OFF 가능

Below zero:
- store/coupon/bid 제한
- teacher alert
- savings→checking 이동 가능

Jobs:
- Student 기본 job
- open job은 두 개 짧은 질문으로 지원
- teacher hire/pass
- term 종료
- job limit

Cart:
- checkout 전 charge 없음
- 오류가 있으면 어떤 것도 charge하지 않음
- signout 시 cart clear

Order:
- cart item별 approve/deny
- deny item은 돈과 coupon 반환
- 일부 item만 deny 가능

Auction:
- winning bid 금액은 checking에서 hold
- outbid 또는 종료까지 hold
- win 시 자동 charge

구매불가 이유도:
- pending
- negative
- insufficient
- winning bid hold
- sold out
- store closed
로 세분한다.

### 구조적 판단

Cashroom의 가장 강한 점은 Math Check만이 아니다. **학생이 왜 지금 어떤 행동을 할 수 없는지를 상태별로 명시하는 것**이다.

Class Money도 silent disabled button을 금지하고 이유를 직접 설명해야 한다.

---

## 4. Banqer Primary

일부 how-it-works URL은 직접 fetch에서 403이 있었으나 공식 Primary 페이지와 Help의 공개 내용을 확인했다.

### S1 / D1

Teacher onboarding:
register teacher → create classroom → add students.

Class Store Help에서:
- Teacher Dashboard에 Class Store widget
- 기본 closed
- Store open으로 전환
- Student Dashboard에서 store 사용

학생 흐름:
Item → Add to cart → Go to checkout → Payment → My Stuff.

### 구조적 판단

Banqer 모듈은 단순 enabled/disabled보다 **운영상의 open/closed state**를 가진다.

Class Money의 상점, 경매, 학생간 거래, 시장 시뮬레이션도 '기능이 존재하는가'와 '현재 수업에서 열려 있는가'를 구분해야 한다.

---

## 5. ClassCents

대상: https://www.classcents.com/

### S1 홈페이지

제품 설명 자체가 사용 순서를 따른다.

교사:
Name money → Payday Jobs → Shop → Transactions.

설명:
1. Name the money and open Shop
2. Pay as the week goes
3. See every Balance

학생:
Earn → Spend → Save.

### S1 공개 UI 문구

구매:
- Current Balance
- Cost
- New Balance

저축 goal:
- $8 of $12
- $4 to go

Login Card:
- 8 cards per page
- username + two words + three digits
- l / 1 / I 혼동을 줄이는 typeface

### S1 핵심 포지셔닝

학생 로그인은 optional이라고 반복적으로 설명한다.

학생 로그인이 없어도 teacher screen에서 Jobs / Payday / Give / Deduct / Redeem 운영 가능.

### D1 setup guide

실제 순서:
1. money
2. jobs
3. pay/payday
4. store
5. bonuses/deductions
6. saving
7. launch

### 구조적 판단

ClassCents의 핵심은 단순 UI라기보다 **학생 앱이 실패하거나 학생 기기가 없어도 경제가 계속 돌아가는 fallback architecture**다.

Class Money의 P0에 Teacher-only 운영을 넣을 가치가 크다.

---

## 6. My Classroom Economy

### D1 Grades 4–5 page

기능별 자료가 별도 문서로 제공된다.
- Program Guide
- Job application / offer / posters / paycheck
- Bank log / slips
- Fine ticket / offense log
- Rental agreement / rent log / unpaid notice / deed
- Auction record / paddle
- saver certificates

### D1 Program Guide PDF 직접 확인

첫 부분은 경제 기능보다 implementation process를 먼저 강조한다.
- 사전 planning/material preparation
- 첫 달 training
- 연중 monitoring

경제 설정 페이지는:
- jobs
- rent
- bonus
- fine
를 중심으로 구성한다.

Loan page는:
- principal
- interest
- term
- minimum payment
를 한 문서 안에서 교육한다.

### 구조적 판단

이 서비스는 복잡한 경제상태를 dashboard 하나로 합치지 않고 **각 경제행위를 별도의 문서와 학생 역할로 externalize**한다.

Class Money도 digital-only로 끝내지 않고 직업카드, 급여명세, 거래명세, 국고보고 같은 printable artifact를 유지할 가치가 있다.

또한 salary만으로 rent를 충당하지 못하고 bonus를 추가로 벌어야 하는 구조, 학업/행동 bonus와 fine은 공정성 측면에서 그대로 복제하면 안 된다.

---

## 7. ClassDojo

### S1 Points page

핵심 메시지는 quick and easy.
- one tap
- custom/PBIS/SEL skill
- reports/trends

### D1 Group help

Web:
Class → Groups tab above student tiles → Add group → student select → Create.

Award:
Group → Award group → Skill.

Group point는 participating student individual reports에 기록되고 별도 group report는 없다.

### 구조적 판단

ClassDojo의 Group은 **공동자산 객체가 아니라 대상 selector**다.

Class Money에서는 반드시:
- StudentGroup — 여러 학생 선택
- GroupAccount — 공동기금
을 별개 객체와 UI로 나눠야 한다.

---

## 8. Greenlight

### D1 Pay-per-chore Help

공개 단계:
Chores tab → Add/Edit chore → Payment → Pay per chore → Amount/allocation → Category Add → percentage 또는 dollar amount → Save.

저장 조건:
- allocation total = 100%
- 여러 아이에게 적용할 때 모두에게 없는 category를 선택하면 incompatible error

### 구조적 판단

복잡한 경제규칙을 저장한 뒤 오류를 알리는 것이 아니라 **설정 단계에서 constraint validation**한다.

Class Money도 allocation, tax, payroll, price/stock, schedule의 잘못된 설정을 save 시점에 잡아야 한다.

---

## 9. Rooster Money

### S1 Chores guide

가장 먼저:
- Allowance chore
- Extra earner
를 구분한다.

그 다음 schedule:
- daily
- weekly
- monthly
- any day
- morning / afternoon / evening

### 구조적 판단

과업 이름보다 먼저 **보상 관계와 반복 주기**를 모델링한다.

Class Money Job/Task 설정도 cron 같은 기술언어가 아니라 교사가 이해하는 일정언어를 사용해야 한다.

---

## 10. 토스 유스

### S1 Teenagers page

Hero: first steps with money.

기능 설명 순서:
1. Youth Card
2. Allowance Tracker / spending habits
3. Goal Pot / Fan Pot
4. jargon 없는 money learning

Youth Card는 'Spend only what you top up'처럼 잔액 경계를 짧은 문장으로 설명한다.

Allowance Tracker는 high-spend days와 places to save를 보여주고, Goal은 단계별 progress를 보여준다.

### 구조적 판단

어린 사용자의 첫 화면/설명은 복잡한 금융메뉴보다:
- 사용가능 경계
- 최근 행동
- 목표
- 학습
순이 적합하다는 강한 사례다.

---

## 11. YNAB

### S1 Guide

예산을 제한 자체보다 priorities와 spending direction으로 설명한다.

### R1 공식 GitHub SDK

공식 ynab/ynab-sdk-js를 직접 확인했다.
2026-11-05까지 push 확인.

공개 API 영역:
- Plans
- Accounts
- Categories
- Months
- Money Movements
- Transactions
- Scheduled Transactions

Category model에는 실제로:
- budgeted
- activity
- balance
- goal_target
- goal_percentage_complete
- goal_under_funded
- goal_overall_funded
- goal_overall_left
가 존재한다.

Transaction에는:
- approved
- cleared
- account
- payee
- category
- transfer pair
- matched transaction
- subtransactions
가 존재한다.

MoneyMovement는 from_category → to_category를 일반 transaction과 별도 객체로 둔다.

### 구조적 판단

YNAB의 '돈의 위치(Account)'와 '돈의 목적(Category)' 분리는 단순 UI 카피가 아니라 공개 API domain model에서도 확인된다.

Class Money에서도 Wallet Account, Allocation/Goal, Transaction, AllocationMovement, ScheduleRule을 무리하게 하나의 객체로 합치지 않는 편이 좋다.

---

# 직접 사이트를 본 뒤 보정된 공통 판단

## A. 사이트의 설명 순서 자체가 제품 mental model의 증거다

- ClassBank: 네 개 core action
- Cashroom: Earn → Bills → Spend → Save → Borrow
- ClassCents: Setup → Pay → Balance / Earn → Spend → Save
- Toss: Card → Review → Goal → Learn

Class Money landing/onboarding도 기능 20개 목록부터 보여주면 안 된다.

## B. 상태가 기능보다 중요하다

실제 사용의 어려움은 기능 유무보다:
- pending
- closed
- held
- approved
- denied
- refunded
- overdue
같은 상태에서 발생한다.

따라서 PRD는 기능별 화면뿐 아니라 **상태별 UI**를 정의해야 한다.

## C. 비활성 이유 설명은 핵심 UX다

Cashroom 사례처럼:
- 상점 닫힘
- 잔액 부족
- 승인 대기
- 아직 처리할 Pending 있음
- 재고 없음
을 버튼 근처에서 설명한다.

## D. 교실에서는 fallback path가 필수다

ClassCents의 teacher-only, Cashroom의 teacher record, Rooster의 bulk review 같은 구조는 정상경로보다 **수업이 꼬였을 때 계속 운영되는가**를 중요하게 본다.

## E. 공개 repository가 없으면 내부기술을 추정하지 않는다

React/Firebase 같은 stack을 외부 UI만 보고 추정해 문서에 사실처럼 기록하지 않는다.