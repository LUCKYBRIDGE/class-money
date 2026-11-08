# ClassDojo 외부 구조도

검증 범위: 공식 Help Center의 Points / Groups / Reports / Redeem  
제품 성격: 행동 피드백·포인트·가정 소통

## 1. Product Context

~~~mermaid
flowchart LR
  Teacher --> Class
  Student --> Class
  Parent --> Reports
  Class --> Students
  Class --> Groups
  Class --> Skills
  Skills --> Points
  Points --> Reports
  Points --> Redeem
~~~

C.

## 2. 포인트 IA

~~~text
Class
├─ Students
├─ Groups
├─ Skills / Point types
├─ Give point
├─ Undo
├─ Reports
│  ├─ Student
│  ├─ Period
│  ├─ PDF
│  └─ Spreadsheet
├─ Notes
├─ Redeem
└─ Display settings
~~~

C.

## 3. Group Flow

~~~mermaid
flowchart TD
  Class --> GroupTab
  GroupTab --> CreateGroup
  CreateGroup --> SelectStudents
  SelectStudents --> SavedGroup
  SavedGroup --> AwardGroup
  AwardGroup --> Skill
  Skill --> IndividualReports[참여 학생 각각의 Report]
~~~

C. 공식 도움말상 별도 Group report는 없고 학생별 report에 반영.

## 4. Point Event

~~~mermaid
stateDiagram-v2
  [*] --> Awarded
  Awarded --> Noted
  Awarded --> Reported
  Awarded --> UndoLast
  Reported --> DeleteFromReport
  Awarded --> Redeemed
~~~

Undo last point와 Reports에서 과거 포인트 삭제 방식이 분리되어 있음 C.

## 5. Quick Interaction

~~~mermaid
sequenceDiagram
  participant T as Teacher
  participant C as Class
  participant S as Student/Group
  T->>C: 학생 또는 그룹 선택
  T->>C: Skill 선택
  C->>S: Point 반영
  C-->>T: 즉시 feedback/Undo
~~~

C.

## 6. 외부 도메인 모델

~~~mermaid
erDiagram
  CLASS ||--o{ STUDENT : contains
  CLASS ||--o{ GROUP : defines
  GROUP }o--o{ STUDENT : members
  CLASS ||--o{ SKILL : defines
  STUDENT ||--o{ POINT_EVENT : receives
  SKILL ||--o{ POINT_EVENT : categorizes
  POINT_EVENT ||--o| NOTE : may_have
~~~

I.

## 7. Display / Privacy

공식 Help에 point totals를 separate/combine/hide하는 Display 설정과 Parent report 공개 조절 관련 문서가 존재.

C.

Class Money 시사점:
- 프로젝트 화면에 개인 잔액 기본 비공개
- 공동목표만 공개
- Quick action UI와 Accounting UI 분리

## 8. Unknown

- 포인트 내부 DB 모델
- Redeem의 회계적 구현
- group event의 서버 저장 방식
- 모바일과 웹의 실제 latency
- parent/student visibility의 모든 조합

## 9. Class Money 적용

X:
ClassDojo는 경제모델이 아니라 ‘수업 중 입력 인터페이스’의 벤치마크.

가져올 구조:
Student tiles → Group → Reason → Award → Undo → Report.

단, 행동포인트와 경제화폐는 별도 도메인으로 유지.

## 근거
- https://help.classdojo.com/hc/en-us/articles/205494185-How-to-Set-Up-and-Award-Points-to-Groups
- https://help.classdojo.com/hc/en-us/articles/209619243-How-to-Undo-a-Point
- https://help.classdojo.com/hc/en-us/sections/200472659-Class-Points-and-Reports
