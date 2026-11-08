# ClassBank Product Anatomy

기준일: 2026-11-08  
범위: 공식 홈페이지, Help Center, Pricing, lesson plans.  
실측 상태: 실제 계정 내부의 전체 클릭 경로와 반응속도는 미측정.

## 1. 제품 경계와 정체성

**E1 확인**  
ClassBank는 K-12 대상의 디지털 classroom economy 플랫폼이며, 학급경영·재무교육·긍정행동 전략을 결합한다.

핵심 구성요소:
- Bonuses / Fines
- Jobs / Job Applications
- Paychecks / Auto Pay
- Bills / Auto Expense
- Store
- Checking / Savings / Interest
- Student Helpers
- Co-teachers
- Reports / Data
- Schoolwide controls / SIS / attendance automation

개별 교사에서 학교 단위까지 확장 가능한 구조다.

## 2. 사용자 역할

### Teacher
학급과 학생, 보너스/벌금, 상점, 직업, 청구서, 저축, 공동교사를 설정하고 거래를 운영.

### Student
계좌 잔액/거래 확인, 직업 지원, 상점 구매, 저축 사용.

### Student Helper
- Store Clerk: 구매 승인, 상품 편집
- HR Representative: 직업 게시판/직업 관리
- Banker: 거래 전송

### Co-teacher
교사 협업.

### School/District Admin
학교 공통 설정, SIS roster, 데이터 대시보드 등.

**핵심:** 서비스가 classroom→schoolwide로 확장되면서 역할계층이 늘어난다.

## 3. 핵심 도메인 객체

- Organization / School
- Class
- Student
- Teacher / Co-teacher
- Account
- Transaction
- Bonus / Fine reason
- Job
- Job application
- Paycheck
- Bill
- Store item / Inventory
- Purchase
- Savings
- Interest rule
- Helper role / Permission
- Attendance event
- Report / Analytics

## 4. 기능 구조도

~~~mermaid
flowchart TD
  ORG[School/District] --> CLS[Class]
  CLS --> ST[Students]
  CLS --> TB[Teacher/Co-teacher]
  ST --> AC[Bank Account]
  BO[Bonuses/Fines] --> AC
  JB[Jobs] --> PA[Paychecks]
  PA --> AC
  BI[Bills] --> AC
  AC --> SV[Savings]
  AC --> SH[Store]
  APP[Job Applications] --> JB
  HEL[Student Helpers] --> SH
  HEL --> JB
  HEL --> AC
  ATT[Attendance] --> PA
  AC --> RP[Reports/Data]
  ORG --> RP
~~~

## 5. 온보딩 구조

**E1 확인**  
공식 시작 가이드는 약 15분 설정을 목표로 하며, 대부분의 교사에게 먼저:
1. Classes
2. Students
3. Bonuses
4. Store
를 권한다.

그 뒤:
5. Jobs
6. Bills
7. Savings / Interest
8. Co-teachers
를 선택적으로 추가.

이 구조의 핵심은 **전체 시스템을 완성해야 시작되는 것이 아니라, 최소 경제를 먼저 작동시키는 것**이다.

### D Class Money 적용
온보딩 완료 기준을 ‘설정 끝’이 아니라 **첫 거래 성공**으로 둔다.

예:
반 만들기 → 학생 붙여넣기 → 지급 사유 하나 → 상품 하나 → 테스트 지급/구매.

## 6. 정보구조와 Navigation

공식 가이드에 드러난 경로:
- Dashboard의 blue panel에서 Class
- Class → Setup → Bonuses/Fines
- Class → Store
- Class → Jobs
- Setup → Bills
- Class gear/Edit Class → Savings
- Class → Co-teacher

**I 해석**
기능별로 사용 맥락 안에 설정이 배치되어 있다. 다만 Settings가 기능별로 분산되면 초보자는 위치를 기억해야 한다.

### D 개선안
Class Money는:
- 기능 내부 상세설정
- 중앙 ‘경제 설정’에서는 상태/요약/바로가기
두 층을 병행.

## 7. 학생 등록 구조

공식 가이드에 4개 경로:
- Class Code self sign-up
- 교사 수동 등록
- spreadsheet import
- School subscription search

**복잡성 해소 방식**
사용 환경에 따라 onboarding path를 바꾼다.

Class Money:
- 붙여넣기/CSV
- 교사 직접생성
- 학생 code join
을 지원하되, 초등 기본은 교사 생성 + 간편학생입장.

## 8. Jobs / Auto Pay

Job:
- suggested job 또는 custom
- 학생 hire
- weekly / biweekly / monthly auto pay
- 모든 학생이 직업을 못 가질 경우 Student job을 만들어 기본소득 가능

**중요 구조**
Job은 단순 라벨이 아니라:
Job definition → assignment → payroll rule → transaction.

### 상태 제안
OPEN → APPLIED → HIRED → ACTIVE → ENDED  
ACTIVE + payday → PAYCHECK POSTED.

## 9. Bills / Auto Expense

Bills는 정기적인 budgeting 경험을 제공.

공식 구조:
Bill definition → schedule → recurring deduction.

**UX 위험**
자동청구는 교사가 잊어도 실행되어 편하지만 학생이 ‘왜 돈이 줄었는지’ 모를 수 있음.

### D Class Money
자동 실행 뒤 학생에게:
- 청구명
- 금액
- 이전/이후 사용가능액
- 다음 청구일
표시.

## 10. Savings / Interest

Savings는 class별 활성화. Interest는 일정 주기로 실행.

**구조적 의미**
Checking와 Savings를 분리하면서 학생이 돈의 용도를 분리.

Class Money:
- 사용가능
- 목표저축
- 일반저축
정도로 초등화.

## 11. Student Helpers — 핵심 권한 모델

공식 Helper:
- Store Clerk
- HR Representative
- Banker

이는 ClassBank의 가장 구조적으로 중요한 기능 중 하나다.

### 좋은 점
학생이 경제의 참여자에서 운영자로 확장.

### 위험
‘직업명’이 곧 ‘실제 시스템 권한’이 되면 자기 자신 지급/승인 같은 이해상충 발생 가능.

### D Class Money
Job과 Permission 분리:
- Banker job: 경제 역할 경험
- Banker permission: 교사가 별도 부여

제약:
- 자기 자신 거래 금지
- 1회/일일 한도
- 고액 교사 2차 승인
- 자동 만료
- 모든 행위 감사로그

## 12. 경제 밸런스 UX

ClassBank는 학년군별 salary, bills, store price 범위를 공식 가이드로 제공한다.

3–5 예:
- 월 소득 약 100
- 월 비용 약 80
- 기본 spending 약 20

핵심은 숫자가 아니라 **급여를 비용보다 약간 높게 설계**한다는 원리다.

### D Class Money
도움말을 읽게 하지 말고 화면에서 즉시:
- 기간 수입
- 기간 고정비
- 남는 금액
- 대표상품 구매기간
- 적자 경고
계산.

## 13. 수업자료 구조

공식 Getting Started Lesson Plans:
- 15분/45분 버전
- Slides
- worksheet/exit ticket
- Money mindset
- Economy introduction
- Bonuses/Fines
- Jobs
- Applications
- Expenses
- Store
- Reflection

**중요:** 제품 기능과 별도의 curriculum layer를 갖고 있다.

### D Class Money
모듈마다:
설정 / 학생화면 / 10분활동 / 회고질문
을 같은 페이지에 연결.

## 14. Schoolwide 확장 구조

공식 School plan:
- 공통 통화/공통 언어
- schoolwide bonuses
- attendance automation
- SIS rostering
- centralized admin dashboard

**제품 복잡도 변화**
Class-level economy에서 organization-level policy로 확장된다.

Class Money는 초기에는 학급 단위에 집중하고, 학교 공용경제는 별도 tenant/policy layer로 나중에 확장해야 한다.

## 15. 복잡성을 풀어낸 UI·UX 패턴

1. Progressive Disclosure
2. suggested defaults
3. 여러 roster input path
4. Auto Pay / Auto Expense
5. 학생 Helper별 제한 영역
6. teacher/student tutorials 분리
7. lesson plan layer
8. schoolwide는 별도 plan/관리 layer

## 16. 리스크

- 행동보상과 경제자산이 직접 연결되어 자산격차가 행동평가를 반영할 수 있음.
- Fines가 경제교육보다 통제수단으로 과사용될 수 있음.
- Bills와 보상이 미국 교실문화에 맞춰진 예시가 많음.
- schoolwide 통화를 도입할 때 교사별 경제정책 충돌 가능.

## 17. Class Money에 가져올 것

**강하게**
- 작은 시작
- 자동급여/자동청구
- Student base job
- 역할 기반 학생운영
- 경제 밸런스 가이드
- lesson plan layer
- import/join의 복수경로

**변형**
- PBIS bonus → 경제 주수입과 분리
- Bills → 기본 OFF
- schoolwide → 별도 확장

## 18. Craft Anything 실측 과제

- 최초 setup 실제 화면수/클릭수
- Class/Setup/Jobs/Store 사이 navigation 깊이
- student bank account 첫 화면
- job application form
- helper 권한으로 로그인했을 때 보이는 메뉴
- store purchase 승인
- savings/interest 학생 표현
- auto pay 실행결과
- phone/tablet/desktop responsive
- school admin dashboard와 teacher dashboard 차이

## 19. 현재 판단

ClassBank의 핵심은 기능보다 **제품을 작게 시작시켜 점진적으로 성장시키는 구조**다. Class Money 온보딩과 권한모델 설계에 가장 유용한 사례다.

## 공식 근거
- https://www.classbank.com/
- https://help.classbank.com/en/articles/6499058-how-do-i-get-started-with-classbank
- https://help.classbank.com/en/articles/5949828-student-helper-jobs-banker-hr-manager-and-store-clerk
- https://help.classbank.com/en/articles/6499914-classbank-suggested-settings
- https://help.classbank.com/en/articles/10728866-getting-started-lesson-plans
- https://www.classbank.com/schools
