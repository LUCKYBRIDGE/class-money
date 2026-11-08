# ClassCents Product Anatomy

기준일: 2026-11-08  
범위: 공식 홈페이지, setup guide, standards pages, privacy/terms.  
실측 상태: 공개 설명 기반. 로그인 후 실제 전수 화면 미실측.

## 1. 제품 경계와 정체성

**E1 확인**  
ClassCents는 교사가 짧은 준비시간으로 교실경제를 만들고 이후 자동 Payday와 간단한 Give/Deduct로 유지하는 web-based classroom economy다.

공개 기능:
- Currency name / symbol / Points mode
- Roster import: CSV / Excel / paste
- Jobs
- Payday: daily / weekly / monthly
- Job Done requirement
- Give / Deduct
- Saved Reasons
- Groups / Whole Class
- Shop / Rewards / inventory
- Savings / Goals
- Badges
- Leaderboard
- Transaction history / Undo
- CSV export / printable statements
- Optional student login
- Printable Login cards
- Student dashboard: phone/tablet/Chromebook
- Curriculum worksheets / standards activities

## 2. 사용자 역할

### Teacher
Class 설정, 학생 등록, 직업/Payday, 지급/차감, Shop, reward redemption, transaction history, export.

### Student — optional
자기 Balance, Job, Shop, Savings/Goal 등 self-service.

**가장 중요한 구조**
학생 self-service가 없어도 핵심 경제는 돌아간다.

이것은 기능이 아니라 **두 가지 운영모드**다.

### Mode A — Teacher-operated
교사 화면 하나로 경제 운영.

### Mode B — Student self-service
학생이 직접 잔액/직업/구매/저축을 사용.

Class Money가 학교 기기환경에 대응하는 데 매우 유용한 패턴.

## 3. 핵심 도메인 객체

- Teacher
- Classroom
- Student
- Login credential
- Currency configuration
- Balance
- Transaction
- Reason preset
- Group
- Job
- Job assignment
- Payday rule
- Job completion
- Reward / stock
- Redemption
- Savings
- Goal
- Badge
- Leaderboard
- Statement / Export

## 4. 기능 구조도

~~~mermaid
flowchart TD
  CL[Classroom] --> ST[Students]
  CL --> CU[Currency]
  ST --> BA[Balance]
  JO[Jobs] --> PR[Payday]
  PR --> BA
  GD[Give/Deduct] --> BA
  GD --> RS[Saved Reason]
  BA --> SH[Shop]
  BA --> SV[Savings]
  SV --> GO[Goal]
  BA --> TR[Transaction History]
  SH --> TR
  PR --> TR
  GD --> TR
  TR --> UN[Undo]
  TR --> EX[CSV/Statements]
  LG[Optional Student Login] --> BA
  LG --> SH
  LG --> SV
~~~

## 5. Setup Flow

공식 setup guide:
1. money name
2. jobs
3. pay/payday
4. store
5. bonuses/deductions
6. savings
7. launch

또 실제 제품에서는:
- starter set of jobs/rewards
- spreadsheet roster import/paste
- starting balance
- login cards
를 지원.

### 복잡성 해소
빈 화면에서 모든 것을 창작시키지 않는다.
- starter list
- grade ideas
- suggested cadence
를 제공한다.

### D Class Money
“추천으로 5분 시작 / 직접 만들기” 두 경로.

## 6. Roster UX

**E1 확인**
CSV/Excel import 또는 spreadsheet paste.

이것은 학교 앱에서 매우 중요한 실제 업무 절감이다.

### D Class Money
paste-first:
1. 표 붙여넣기
2. 열 자동인식
3. preview
4. 중복/빈 번호 경고
5. 확정

학생 25명 폼 반복입력 금지.

## 7. Give / Deduct 공통 모델

공식:
- one student
- Group
- whole class
- saved Reason

복잡한 지급 범위를 **대상 selector 하나**로 통합.

예:
Helping Others $2 → 24 students.

### D Class Money
Quick Transaction:
대상 → Reason → 금액 → preview → 확정.

Reason preset은:
- 이름
- 기본금액
- 분류
- 최대금액/기간
을 가질 수 있음.

## 8. Payday

Job에 pay amount와 cadence를 연결:
- daily
- weekly
- monthly

학생이 Job done을 표시해야 지급되도록 선택 가능.

### 구조
Job definition → Assignment → Completion requirement → Payday → Transaction.

### 좋은 점
시간기반 지급과 수행기반 지급을 하나의 payroll model 안에서 처리.

### D Class Money
조건:
- 자동
- 학생 완료 제출
- 교사 확인
을 job마다 선택.

## 9. Student Login Card

공식:
- 이메일 불필요
- 교사가 username/password 생성
- 8장/letter page 출력
- password 예: 두 단어 + 3자리 숫자
- l / I / 1이 헷갈리지 않는 typeface

이것은 실제 교실환경에 매우 구체적인 UX다.

### D Class Money
- QR + short code 병행
- O/0/I/1 회피
- 8장/A4
- 재발급 시 이전 code revoke
- 학생 바꾸기
- 자동 session timeout

## 10. Student Purchase

공개 예:
- Current Balance
- Cost
- New Balance

구매 전에 세 숫자를 보여준다.

이 UI는 매우 강하다.
학생이 ‘가격’만 보지 않고 결과잔액을 즉시 본다.

### D Class Money
표시:
지금 쓸 수 있는 돈 24  
이 상품 -20  
사고 나면 4

Goal과 연결:
“이 구매를 하면 목표까지 2주 더 걸릴 수 있어요.”

## 11. Savings / Goals

공식:
- Savings
- named Goal
- 예: $8 of $12 / $4 to go

좋은 점:
progress %만 보여주지 않고 **남은 금액을 직접 말한다.**

Class Money:
현재액/목표액/남은액/예상기간.

## 12. One Balance across Classrooms

**E1 확인**
같은 학생은 여러 classroom에서도 하나의 Balance를 공유하고 Jobs/Rewards/Badges는 classroom-specific.

### 장점
학교 전체 economy로 확장하기 쉬움.

### 구조적 문제
- 어느 반에서 벌었나?
- 다른 반 상점에서 쓸 수 있나?
- 교사 A/B의 가격정책 충돌
- 반 이동/학기변경

### D Class Money
기본: Wallet은 Classroom scope.  
School wallet은 명시적으로 별도 활성화.

## 13. Transaction / Undo / Export

모든 거래 기록.
Give/Deduct는 전체반 지급도 Undo 가능.
CSV export, printable statement.

**핵심**
오류수정이 숨겨진 관리 기능이 아니라 주요 제품 기능.

Class Money:
- 직후 snackbar undo
- 이후 transaction detail에서 reversal
- 원본 기록 보존.

## 14. Curriculum Layer

공식 Standards pages와 96 worksheets:
- 실제 class transaction
- balances
- paydays
- goals
- store purchases
를 수학 활동 데이터로 사용.

예:
Grade 1: +10/-10 예측  
Grade 4: multi-step real transactions  
Grade 6: savings goal milestones.

**중요 구조**
제품 데이터가 곧 학습문제의 소재.

### D Class Money
학생 자신의 경제 데이터를 활용한:
- 익명 class dataset
- 예상잔액
- 그래프
- 비율/통계
활동을 만들 수 있다.

단, 개인 재산을 공개하지 않는다.

## 15. Privacy / Data

공식:
- student email/phone 불필요
- teacher-created student account
- 이름, credentials, balance/jobs/rewards/badges/transactions 저장
- export/delete 가능
- actual currency has no real-world value

Class Money도 데이터 최소수집을 강하게 적용.

## 16. Leaderboard

공식 기능에는 class leaderboard가 있다.

### 비판
경제 잔액은 능력/성실도를 뜻하지 않는다.
공개 ranking은:
- 자산 낙인
- 경쟁 강화
- 보상 기회 차이 공개
문제가 있다.

Class Money는 개인 자산 leaderboard 기본 제외.

대안:
- 공동저축 목표
- 학급 경제 참여율
- 전체 국고
- 개인 자기목표.

## 17. 복잡성을 풀어낸 방식

1. 학생 로그인 선택
2. roster import/paste
3. starter set
4. 개인/그룹/전체 공통 지급
5. saved reason
6. simple payday cadence
7. Login card
8. Current/Cost/New Balance
9. full transaction history
10. curriculum layer using real data

## 18. Class Money에 가져올 것

**최우선**
- Teacher-only mode
- Student self-service optional
- paste roster
- quick transaction
- Payday
- Job done condition
- Login card
- Current/Cost/New
- undo/export

**변형**
- Savings/Goals
- curriculum activities
- schoolwide wallet

**제외**
- public balance leaderboard
- automatic cross-class balance
- unrestricted negative balance

## 19. Craft Anything 실측

- teacher home layout
- student tile density
- paste roster
- currency configuration
- Give/Deduct actual click count
- whole class payment preview
- payday setup
- mark-job-done
- Login card print
- purchase flow
- savings goal
- transaction undo
- phone/tablet/Chromebook responsiveness

## 20. 현재 판단

ClassCents는 기능의 깊이보다 **교사가 실제로 계속 쓸 수 있게 하는 운영 마찰 최소화**에서 강하다.

Class Money가 가장 우선적으로 참고해야 할 operational benchmark 중 하나다.

## 공식 근거
- https://www.classcents.com/
- https://www.classcents.com/guides/how-to-set-up-a-classroom-economy
- https://www.classcents.com/standards
- https://www.classcents.com/privacy
- https://www.classcents.com/terms
