# Banqer Primary Product Anatomy

기준일: 2026-11-08  
범위: 공식 Primary features, FAQ, Class Store help.  
실측 상태: 공개 설명 기반. 실제 클래스 내부 전체 화면은 미실측.

## 1. 제품 경계와 정체성

**E1 확인**  
Banqer Primary는 금융 리터러시를 ‘기능’보다 **생활경제 시뮬레이션 모듈**로 제공한다.

주요 모듈:
- Basic Income
- Expenses
- Careers and Employment
- Banking
- Interest on Savings
- Term Deposits
- Tax
- Property
- Insurance
- Transport
- 지역별 Superannuation/KiwiSaver
- Class Store
- Videos / Quizzes / Simulated events / Group activities

제품의 핵심은 ‘돈을 주고 쓰는 앱’보다 **개념을 경험하게 하는 학습 환경**에 가깝다.

## 2. 사용자 역할

### Teacher
Class 생성, 학생 추가, 학습모듈/경제환경 운영, store 개폐, teacher item 관리, 학습자료 사용.

### Student
Dashboard에서 income/expenses/bank/store/property 등 활성화된 시뮬레이션에 참여.

### Platform/Curriculum
모듈별 video, quiz, group activity, unit plan을 제공.

## 3. 핵심 도메인 객체

- Classroom
- Student
- Banqer dollars / Account
- Income rule
- Expense rule
- Job / Employment
- Savings
- Interest
- Term deposit
- Tax
- Property / Mortgage / Rent
- Insurance policy / claim
- Transport asset
- Store item / Cart / Purchase / Claim
- Avatar / My Stuff
- Learning module
- Quiz / Activity
- Achievement

## 4. 기능 구조도

~~~mermaid
flowchart TD
  CLS[Class] --> INC[Basic Income]
  INC --> EXP[Expenses]
  INC --> JOB[Employment]
  JOB --> BANK[Banking]
  BANK --> SAV[Savings/Interest]
  SAV --> TD[Term Deposit]
  BANK --> TAX[Tax]
  BANK --> PROP[Property]
  PROP --> INS[Insurance]
  BANK --> TRANS[Transport]
  BANK --> STORE[Class Store]
  LEARN[Videos/Quizzes/Activities] --> INC
  LEARN --> EXP
  LEARN --> JOB
  LEARN --> SAV
  LEARN --> TAX
  LEARN --> PROP
~~~

## 5. 핵심 복잡성 해결: Expansion

Banqer의 구조적 강점은 기능을 한꺼번에 보여주는 대신 **경제 개념의 확장 단계**로 경험하게 한다는 점이다.

학생이 처음부터 Property/Insurance/Transport를 모두 이해할 필요가 없다.

### D Class Money
모듈을 단순 기능 ON/OFF가 아니라:
- 배우는 개념
- 학생에게 추가되는 화면
- 예상 수업시간
- 선행개념
을 포함한 ‘학습 모듈 카드’로 제공.

## 6. Teacher Dashboard / Student Dashboard

**E1 확인**
Class Store는 Teacher Dashboard widget으로 존재하며 기본 Closed 상태다. 교사가 Store open을 켜면 학생 Dashboard에서 사용할 수 있다.

이 구조는 같은 기능을 역할별로 다르게 보여준다.

Teacher:
- open/close
- item creation
- purchased items / claim review

Student:
- browse
- cart
- checkout
- My Stuff / claim

**핵심:** control surface와 consumption surface를 분리.

## 7. Store Flow

공식 학생 흐름:
Item → Add to cart → Go to checkout → Payment details → Make payment → My Stuff → Apply.

Teacher item:
교사가 icon/name/description/price/stock을 생성.

Teacher item을 구매한 학생은 My Stuff에서 claim. 교사는 accept/decline.

중요한 특이점:
공식 도움말상 teacher item claim을 decline해도 자동 환불이 아니라 나중에 re-claim할 수 있게 한다.

### D Class Money
‘결제 취소’와 ‘실물/특전 수령 거절’을 분리해야 함.

상태:
PURCHASED → CLAIMABLE → CLAIM_REQUESTED → FULFILLED  
CLAIM_REQUESTED → DECLINED → CLAIMABLE.

환불은 별도 REFUND 액션.

이 사례는 **상품 소유와 상품 이행(fulfillment)을 분리**해야 한다는 점을 보여준다.

## 8. Basic Income / Expenses

Banqer는 기본소득과 주간 비용을 개별 학습모듈로 다룬다.

좋은 구조:
- 돈이 들어오는 경험과
- 반복비용을 책임지는 경험
을 분리.

### D Class Money
기본 참여소득은 핵심.
Expenses는 기본 OFF 학습모듈.

## 9. Careers and Employment

공식 설명:
CV, classroom job application, paid-job responsibility.

단순 직업배정이 아니라 **취업 과정**을 학습시킨다.

Class Money 학년별:
- 저학년: 희망 직업 선택
- 중학년: 이유 한 문장
- 고학년: 지원서/면접 선택

## 10. Banking / Overdraft / Debt

Banqer Banking은 계좌뿐 아니라 관리 선택의 결과, overdraft/debt를 포함.

장점:
금융상품을 ‘설명’이 아니라 결과로 학습.

위험:
초등 저학년에 과도.

Class Money:
기본 은행 = Spending + Saving.
Debt는 Simulation Lab.

## 11. Savings / Term Deposit

Interest on Savings:
정기 기여와 compound interest.

Term Deposit:
돈을 일정 기간 잠그고 더 높은 이자 개념.

### UX 구조적 의미
단순 ‘저축’ 하나에 모든 개념을 넣지 않고:
- 유동성 높은 저축
- 잠금 저축
을 다른 선택으로 경험.

Class Money 고학년:
‘목표저축’과 ‘잠금저축 실험’으로 단순화 가능.

## 12. Tax

Banqer는 tax brackets/rates와 real-world use를 학습.

Class Money는:
학생 지갑 → Treasury → Public Spending
이라는 추적가능한 흐름으로 구현하는 편이 적합.

세금 화면에 ‘빠져나간 돈’만 보여주면 개념 절반만 경험.

## 13. Property / Insurance / Transport

이 세 모듈의 공통점:
**한 번의 선택이 이후의 반복비용과 위험을 바꾼다.**

Property:
deposit/mortgage/rental income/expenses.

Insurance:
premium/claim/risk.

Transport:
purchase/sale + ongoing budget effect.

Class Money는 실제 물건을 흉내내기보다 선택 구조만 가져올 수 있다.

예:
가상 교통카드 A: 초기 40 / 주당 10  
가상 교통카드 B: 초기 100 / 주당 3

학생이 장기비용을 비교.

## 14. Learning Layer

공식:
- videos
- quizzes
- simulated events
- group activities
- unit plan
- curriculum resources

**핵심:** 제품 기능과 수업자료가 별도 사이트가 아니라 같은 경제개념을 중심으로 연결.

### D Class Money
모듈 화면:
1. 이 개념은?
2. 교사 설정
3. 10분 수업
4. 학생 화면 미리보기
5. 시작
6. 회고

## 15. 모바일/기기

공식 FAQ:
- browser 기반
- native app 없음
- mobile-friendly
- 학생/교사 어떤 기기에서도 로그인
- 첫 class setup 및 student add가 몇 분 수준이라고 설명

Class Money도 PWA/browser-first가 학교환경에 적합할 수 있다.

## 16. 복잡성을 풀어낸 방식

1. 기능이 아닌 개념별 Expansion
2. 역할별 Dashboard
3. 기능 open/close
4. 익숙한 cart/checkout model
5. Learning resources와 simulation 연결
6. 실제 생활 선택을 단계적으로 추가
7. browser-first

## 17. 리스크

- Property/Insurance/Transport가 초등 교실 목표보다 ‘성인생활 재현’에 치우칠 수 있음.
- rewards/auction/store가 금융학습보다 게임 동기가 될 수 있음.
- 실제 자산구조를 지나치게 사실적으로 모방하면 지역제도 차이 발생.
- 일부 보상 예시(자리/특권)는 학습권 형평성 검토 필요.

## 18. Class Money에 가져올 것

**강하게**
- 학습개념별 module
- teacher/student dashboard 분리
- feature open/close
- module + activity + simulation 결합
- 기본소득
- 세금→공공사용
- purchase와 fulfillment 상태 분리

**변형**
- term deposit
- insurance
- transport
- property

**초기 제외**
- mortgage/overdraft 등 고급 금융

## 19. Craft Anything 실측

- 신규 class onboarding
- module enable/disable
- student dashboard 변화
- class store closed/open UI
- cart→checkout→My Stuff
- claim teacher item
- learning video/quiz entry
- mobile responsive
- expansion 추가 시 메뉴 변화
- student financial dashboard의 정보밀도

## 20. 현재 판단

Banqer의 가장 큰 강점은 **기능을 학습 개념 단위로 쪼개고, 그 기능을 수업자료와 결합한다는 것**이다. Class Money의 고급 경제교육 레이어 설계에 가장 좋은 참고 모델이다.

## 공식 근거
- https://banqer.co/au/primary/how-it-works
- https://banqer.co/au/primary/faqs
- https://primary.banqer.co/nz/help/the-class-store
- https://primary.banqer.co/nz/help/spending-what-students-can-buy-with-their-banqer-dollars
