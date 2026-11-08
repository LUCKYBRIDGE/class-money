# My Classroom Economy Product Anatomy

기준일: 2026-11-08  
범위: 공식 Grades 4–5 페이지와 Program Guide PDF.  
특징: 앱보다 **교실 운영 프로토콜 + 종이 인터페이스**에 가깝다.

## 1. 제품 경계와 정체성

**E1 확인**  
My Classroom Economy는 학급 안에서 실제 경제활동을 반복하도록 설계된 classroom management / experiential financial literacy 프로그램이다.

Grades 4–5 핵심:
- 직업
- 월급
- Bank log / slips
- Rent
- Fines / Bonuses
- Loans
- Auctions
- Desk ownership
- Year-end reflection

운영 방식은 디지털 앱보다 물리적 자료와 역할에 의존한다.

## 2. 사용자 역할

### Teacher
경제규칙 설계, job/rent/bonus/fine 결정, 학생 지도, offense log 관리, auction 운영.

### Student
job 수행, paycheck, bank log, rent, auction, saving, loan, 기록.

### Banker
4–6명 client의 bank record, deposit/withdrawal 관리.

### Police Officer
교사 offense log를 기반으로 fine ticket 작성.

### Loan Officer
loan slip, interest, repayment 관리.

### Clerk / Messenger / Store Clerk 등
실제 학급 업무 수행.

**핵심:** 학생 역할이 단순 title이 아니라 **실제 서비스 프로세스의 일부**다.

## 3. 핵심 도메인 객체

디지털로 변환한다면 최소:
- Student
- Job / Salary
- Paycheck
- Bank ledger
- Deposit / Withdrawal
- Rent contract / Payment
- Desk asset / Deed
- Bonus
- Fine / Offense
- Loan / Interest / Installment
- Auction / Bid / Item
- Reflection / Certificate

## 4. 전체 구조

~~~mermaid
flowchart TD
  J[Job] --> P[Paycheck]
  P --> BL[Bank Log]
  B[Bonus] --> BL
  F[Fine] --> BL
  R[Rent] --> BL
  L[Loan] --> BL
  A[Auction] --> BL
  BL --> S[Saving/Financial Plan]
  S --> A
  S --> D[Desk ownership]
  BL --> REF[Reflection]
~~~

모든 경제행위가 Bank Log로 수렴한다.

## 5. 가장 중요한 구조: 종이가 상태를 들고 있다

공식 자료:
- Job application
- Job offer
- Paycheck
- Bank log
- Bank slips
- Fine tickets
- Offense log
- Rental agreement
- Rent log
- Unpaid rent notice
- Deed to desk
- Auction record
- Auction paddle

이 프로그램은 거대한 단일 화면 대신 **업무마다 별도의 문서/물리적 객체**를 제공한다.

### UX 해석
복잡한 사회 시스템을 “경제 대시보드 하나”로 압축하지 않고:
- 취업할 때 지원서
- 급여 받을 때 수표
- 은행할 때 slip/log
- 임대할 때 계약서
- 경매할 때 paddle
처럼 **행동 맥락에 맞는 인터페이스**를 준다.

## 6. 초기 설정과 운영 Cadence

공식 Program Guide:
- 학기 전 planning/material preparation: 수 시간
- 첫 달 학생 introduction/training: 수 시간
- 월간 ongoing activity: 약 1–2시간
- year-end reflection: 약 1시간

월간 반복:
paychecks → bonuses/fines → rent → auction.

**핵심:** 경제는 특별 이벤트가 아니라 반복되는 학급 루틴.

### D Class Money
Daily / Weekly / Monthly / Term cadence를 UI에 명시.

학생 홈:
- 오늘 할 일
- 다음 payday
- 이번 달 activity
- 학기 목표.

## 7. Job System

공식:
모든 학생이 job 필요.
core job 예:
- Banker
- Police Officer
- Messenger
- Clerk

직무 책임에 따라 salary 차등.
책임 큰 job에는 recommendation 요구 가능.

Banker가 4–6명 학생의 기록을 담당하는 등 student-to-student service 구조가 강하다.

### 장점
실제 역할 수행과 학급운영 효율이 연결.

### 위험
- 권한 남용
- 학생 간 감독관계
- 인기/책임 직업의 위계
- 추천제의 편향

### D Class Money
직업과 system permission을 분리.
학생은 raw balance 편집권 대신 ‘승인 대기 작업’을 처리.

## 8. Bank Log — 학습의 중심 UI

학생과 Banker가 각각 ledger를 유지하고 서로 balance를 맞춰야 한다.

교육적 의미:
- 기록
- 계산
- 대조
- 오류 발견
- 정확성

디지털화하면 이 과정이 자동으로 사라지기 쉽다.

### D Class Money
자동 원장은 유지하되 학생용:
- 예상 잔액
- 주간 거래검토
- “이 거래가 맞나요?”
- reconcile mini activity
를 남긴다.

## 9. Rent Model — 가장 비판적으로 볼 부분

공식 Program Guide는 salary가 rent를 완전히 충당하지 못하도록 설정하고 bonus로 차액을 벌게 하는 방식을 권고한다.

예:
- monthly rent 1000
- desk purchase 3000
- salary alone insufficient
- rent 미납 시 auction 참여 제한

### 교육의도
- 계획
- 추가소득
- 책임
- delayed gratification.

### 구조적 위험
- 학생이 bonus를 받아야 ‘정상 상태’를 유지.
- bonus가 학업/행동에 연결되면 구조적 자산격차 발생.
- 경제적 실패가 privilege loss와 연결.

### D Class Money
기본 경제에서는 정기소득 ≥ 필수지출.
의도적인 deficit simulation은 별도 lesson에서만.

## 10. Bonus / Fine System

공식 bonus에는 test score, reading, extracurricular, compliments 등 학업/행동 요소가 포함된다.

Fine에는 dishonesty, rudeness, missing work, off-task, tardiness 등이 포함.

Program Guide는 “punishment 목적이 아니다”라고 설명하지만 실제 경제 상태에 직접 영향을 준다.

### Class Money 비판
행동/성취 → 자산의 직접 연결은 기본 경제로 삼지 않는 편이 낫다.

추천:
- 기본 참여수입
- job income
- task income
이 경제의 중심.

Behavior feedback은 별도 badge/feedback layer.

## 11. Loan

공식:
- principal
- fixed interest
- front-loaded interest
- term
- minimum payment
- 1–3 months
- missed payment consequence.

디지털화 시 필요한 상태:
APPLICATION → APPROVED → ACTIVE → INSTALLMENT_DUE → PAID_OFF / DELINQUENT.

초등 Class Money에서는 고급 Simulation으로 제한.

## 12. Auction

Auction은 supply/demand, opportunity cost를 매우 강하게 체험시키는 구조.

물리적 paddle은:
- 참여상태를 전체가 봄
- 현재 경쟁을 즉시 이해
- 별도 앱 조작이 필요 없음

### D Class Money
디지털 auction을 만든다면 shared projection mode 필요:
- item
- current price
- timer
- bids count
- 개인자산은 비공개.

학생개인 화면에는:
- 내 사용가능액
- 최대 입찰 계획
만.

## 13. Desk Ownership

Desk rent/purchase는 임대와 소유 개념을 체험시키지만 실제 좌석과 경제력을 결합한다.

**Class Money에서는 그대로 도입하지 않는 것을 권고.**

대체:
- 가상 workspace
- virtual business stall
- virtual asset.

## 14. Year-end Reflection

Program Guide는 year-end wrap-up과 certificates를 별도 단계로 둔다.

Class Money에서 학기 종료는 단순 reset이 아니라:
- 총수입 출처
- 가장 큰 지출
- 가장 오래 유지한 목표
- 선택에 대한 회고
- 공정성 의견
- 다음번 규칙 제안
을 기록하는 event가 되어야 한다.

## 15. 디지털화하면서 없앨 것 / 남길 것

### 없앨 반복 마찰
- 손계산 합산
- 중복 ledger
- 급여 반복계산
- 수기 거래누락
- 교사의 총합 확인

### 남길 학습 마찰
- 예상
- 선택
- 기록 확인
- 계획
- opportunity cost
- 회고

이 구분이 My Classroom Economy 분석의 가장 큰 가치다.

## 16. 물리적 출력물의 가치

Class Money가 웹앱이어도 다음 printable을 제공할 가치가 있다.
- Job card
- Pay statement
- Student statement
- Store price poster
- Class economy rules
- Treasury report
- Auction paddle
- End-of-term reflection

디지털 앱이 교실 공간을 대체하는 것이 아니라 확장.

## 17. Class Money에 가져올 것

**강하게**
- 반복 cadence
- transaction record의 학습가치
- job application
- student roles
- auction as lesson
- printable artifacts
- term reflection

**변형**
- rent → 가상 expense
- desk ownership → virtual asset
- banker → 제한된 helper role
- loan → high-grade simulation

**제외**
- 기본 salary보다 높은 강제 rent
- 성적/행동 bonus 의존
- 실제 학습환경 privilege deprivation
- student policing economy

## 18. Craft Anything / 자료 실측

앱 화면보다 document flow를 분석:
- Job application
- Paycheck
- Bank log
- Bank slip
- Rental agreement
- Fine ticket
- Loan slip
- Auction record
- Auction paddle

각 양식에서:
입력필드 / 누가 작성 / 누가 검증 / 다음 단계 / 보관기간을 추출.

## 19. 현재 판단

My Classroom Economy는 Class Money에게 **무엇을 자동화해야 하는지보다 무엇을 자동화하면 안 되는지**를 알려준다.

교사의 불필요한 반복마찰은 제거하고, 학생의 의미 있는 사고과정은 남겨야 한다.

## 공식 근거
- https://myclassroomeconomy.org/en/grades4-5
- https://myclassroomeconomy.org/assets/printables/en/4-5/Program_Guide_4-5.pdf
