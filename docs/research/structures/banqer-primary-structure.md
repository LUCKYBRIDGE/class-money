# Banqer Primary 외부 구조도

검증 범위: 공식 Primary 제품 페이지·Help·운영 가이드  
제품 성격: 금융문해력 커리큘럼 + 장기 시뮬레이션

## 1. Product Context

~~~mermaid
flowchart LR
  Teacher --> Class
  Student --> Class
  Class --> Modules[Financial Modules]
  Modules --> Learning[Video / Quiz / Activity]
  Modules --> Simulation[경제 시뮬레이션]
  Simulation --> Dashboard
  Learning --> Progress
~~~

C.

## 2. Module 중심 구조

대표 공개 모듈:
- Basic Income
- Expenses
- Careers & Employment
- Banking
- Savings Interest
- Term Deposits
- Tax
- Property
- Insurance
- Transport
- 국가별 기타 금융개념

C.

## 3. Module Lifecycle

~~~mermaid
stateDiagram-v2
  [*] --> Disabled
  Disabled --> TeacherPreview
  TeacherPreview --> Enabled
  Enabled --> StudentLearning
  StudentLearning --> Simulation
  Simulation --> Review
  Review --> Completed
~~~

Teacher preview / enabling / 학생 학습 흐름 C/I.

## 4. 단계적 공개

공식 운영가이드:
Basic Income + Expenses를 기반으로 시작하고 일반적으로 여러 새로운 모듈을 동시에 켜지 않도록 권장. 장기 운영은 약 2~4주 간격 개방.

~~~mermaid
flowchart LR
  Base[Basic Income + Expenses] --> M1[Module 1]
  M1 --> M2[2~4주 후 Module 2]
  M2 --> M3[2~4주 후 Module 3]
  M3 --> M4[심화]
~~~

C.

## 5. Careers & Employment

~~~mermaid
flowchart TD
  Teacher --> CreateJob[직업 생성]
  CreateJob --> Fields[Title/Description/Type/Pay/Frequency/Positions]
  Fields --> Publish
  Student --> CV
  Student --> Apply
  CV --> Apply
  Apply --> Review
  Review --> Hire
  Review --> Reject
  Hire --> Contract
  Contract --> Pay
  Contract --> End
~~~

C.

## 6. 사용자/권한

~~~mermaid
flowchart TD
  Teacher --> Setup[모듈/경제 설정]
  Teacher --> Monitor[학생 진행/계좌/거래]
  Teacher --> Jobs[직업시장]
  Student --> Learn[콘텐츠]
  Student --> Economy[경제 활동]
  Student --> JobApply[직업지원]
  Student --> Quiz[퀴즈]
~~~

C.

## 7. Dashboard 구조

공식 자료 기준 교사에게:
- 학생 progress
- recent activity
- account/transactions
- module progress

가 보임.

~~~mermaid
flowchart LR
  TeacherDashboard --> Ops[운영]
  TeacherDashboard --> Economy[경제상태]
  TeacherDashboard --> Learning[학습진도]
~~~

C/I.

## 8. Store

C:
- Class Store
- digital avatar items
- teacher-created items
- store open/close
- stock 제한/무제한

Claim/거절/환불의 정확한 상태는 실측 필요.

## 9. Leaderboard

C:
- achievement
- savings
- net worth
- 지역/설정에 따라 credit score 등

일부 leaderboard를 교사가 비활성화할 수 있음.

## 10. 외부 도메인 모델

~~~mermaid
erDiagram
  CLASS ||--o{ MODULE_ACTIVATION : enables
  MODULE ||--o{ MODULE_ACTIVATION : configured
  STUDENT ||--o{ MODULE_PROGRESS : tracks
  MODULE ||--o{ MODULE_PROGRESS : measures
  CLASS ||--o{ JOB : defines
  STUDENT ||--o{ JOB_APPLICATION : submits
  JOB ||--o{ JOB_CONTRACT : creates
  STUDENT ||--o{ JOB_CONTRACT : holds
  STUDENT ||--o{ ACCOUNT : owns
  STUDENT ||--o{ QUIZ_RESULT : completes
~~~

I.

## 11. 학습과 경제의 분리

구조적으로 두 개의 상태를 분리해야 함.

~~~mermaid
flowchart TD
  Student --> FinancialState[경제 상태]
  Student --> LearningState[학습 상태]
  FinancialState --> Balance
  FinancialState --> Assets
  LearningState --> ModuleProgress
  LearningState --> Quiz
  LearningState --> Reflection
~~~

Class Money용 X 개념이지만 Banqer 분석에서 도출.

## 12. Unknown

- 내부 account/ledger 구조
- transaction correction 방식
- Class Store 정확한 결제/환불 시점
- module prerequisite의 기술 구현
- leaderboard 내부 정렬규칙
- scheduler 재시도

## 13. Class Money 적용

X:
기능 플래그보다 Module Engine:
- prerequisite
- recommended grade
- teacher preview
- feature bindings
- lesson card
- reflection
- completion

## 근거
- https://banqer.co/au/primary/how-it-works
- https://banqer.co/nz/blog/how-to-plan-banqer-primary
