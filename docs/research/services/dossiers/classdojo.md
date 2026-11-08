# ClassDojo Product Anatomy

기준일: 2026-11-08  
범위: 공식 Points/Groups/Reports/Undo/Redeem 도움말.  
목적: 경제모델이 아니라 **고빈도 교실 입력 시스템** 분석.

## 1. 제품 경계와 정체성

ClassDojo Points는 교사가 수업 중 학생에게 긍정/부정 피드백을 빠르게 기록하는 시스템이다.

주요 객체:
- Class
- Student
- Group
- Skill
- Point event
- Note
- Report
- Point bubble
- Reward/Redeem

Class Money가 참고할 것은 화폐 구조가 아니라 **입력 latency와 feedback loop**다.

## 2. 사용자 역할

### Teacher
Skill 정의, 학생/그룹에 point 지급, undo, report 조회, 표시설정.

### Student / Family
설정에 따라 point/report 일부 조회.

Class Money와 가장 큰 차이:
Point event는 금융원장보다 행동피드백 이벤트에 가깝다.

## 3. 기능 구조

~~~mermaid
flowchart LR
  CL[Class] --> ST[Students]
  CL --> GR[Groups]
  SK[Skills] --> PE[Point Event]
  ST --> PE
  GR --> PE
  PE --> PB[Point Bubble]
  PE --> RP[Reports]
  PE --> UN[Undo]
  PB --> RE[Redeem]
  RE --> RP
~~~

## 4. 핵심 UX: 대상 → Skill

교사가 수업 중 이미 알고 있는 정보는:
- 누구?
- 왜?

ClassDojo는 이 두 선택만 남긴다.

Skill에 point value가 미리 정의되므로 반복 입력이 없다.

### D Class Money
지급 사유 preset:
- 직업 추가업무 +10
- 공동체 도움 +5
- 특별보수 +5

Quick Award:
대상 → 사유 → 완료.

금액을 preset이 들고 있으면 수업 중 numeric input 생략.

## 5. Student Tile Model

공식 웹 흐름:
Class → student tile / whole class → skill.

Groups tab에서는 group 선택→Award group→skill.

**구조적 강점**
대상을 데이터테이블에서 검색하는 대신 **시각적 명단 자체를 action surface**로 사용.

Class Money:
교사 수업모드에서 학생 tile을 누르면:
- + 지급
- 최근 거래
정도만 빠르게 표시.

상세 금융정보는 별도 학생 페이지.

## 6. Group Model

Group에 point를 주면 구성 학생 individual report에 기록. 별도 Group report는 없음.

Class Money에서는 두 경제 모델을 반드시 구분:
1. 그룹원 각자에게 N 지급
2. 그룹 공동계좌에 N 지급

UI 문장:
“1모둠 5명에게 각각 5 지급 (총 25)”
vs
“1모둠 공동기금에 25 지급”

## 7. Undo

**E1 확인**
직전 point는 즉시 Undo 가능.
오래된 잘못된 point는 Reports에서 수정.

이 구조는 time proximity를 이용한 복구 UX다.

### D Class Money
거래 직후 banner:
“25명 × 5 = 총 125 지급”
[되돌리기]

그러나 금융원장은 event 삭제가 아니라 reversal.

## 8. Report Model

공식 help에는:
- Point note
- point values
- custom skills
- parent report visibility
- PDF/download/spreadsheet
- report editing
등이 분리되어 있다.

**핵심**
입력 화면은 단순하지만 상세 데이터는 Reports로 이동.

Class Money:
Quick UI와 Audit UI를 분리.
수업 중에는 최소 필드, 저장 시에는:
- actor
- targets
- reason
- amount
- source
- timestamp
- batch id
를 기록.

## 9. Redeem / Reset

Redeem:
현재 point bubble에서는 차감되지만 report 기록은 남는다.

Reset:
current display와 historical report를 분리.

이 개념은 Class Money에서 직접 reset으로 가져오면 안 되지만:
- 현재 사용가능액
- 기간 요약
- 전체 history
가 서로 다른 view라는 점은 유용하다.

## 10. Display / Privacy

ClassDojo는 point total을 combine/separate/hide할 수 있고 family report 노출도 설정할 수 있다.

Class Money는 더 엄격하게:
- 공개 class screen: 개인 balance 없음
- student: 자기 balance
- teacher: 전체
- parent integration이 있다면 scope별 opt-in.

## 11. Negative Point와 금융 벌금의 차이

ClassDojo의 negative skill은 behavior feedback.

이걸 돈 차감으로 그대로 옮기면:
- 행동평가가 자산격차가 됨
- 관찰빈도 bias
- 공개 ranking과 결합 시 낙인.

### D Class Money
Behavior feedback layer와 Economy layer 분리.
Fine은 별도 module / 기본 OFF.

## 12. 고빈도 작업의 설계 법칙

ClassDojo에서 얻는 핵심:
**빈도가 높은 작업은 설정의 유연성보다 실행 마찰이 더 중요하다.**

따라서 Class Money의 가장 자주 쓰는:
- 지급
- 승인
- 학생 찾기
- 최근 undo
는 1–3 action 안에서 끝나야 한다.

반대로 경제설정은 자주 쓰지 않으므로 더 상세해도 된다.

## 13. Class Money에 가져올 것

- Student tiles
- Group selection
- preset reason
- last-action undo
- quick surface vs detailed reports
- display privacy controls
- mobile-first fast feedback

가져오지 않을 것:
- behavior score=money
- negative points→automatic fines
- public economic totals.

## 14. Craft Anything 실측

- class screen student tile density
- point award steps
- group award
- whole class award
- recent undo banner
- reports navigation
- mobile app vs web
- projector/display settings
- parent/student report visibility

## 15. 현재 판단

ClassDojo는 Class Money의 경제엔진 benchmark가 아니라 **교사가 수업을 끊지 않고 transaction을 시작하는 방법**의 benchmark다.

## 공식 근거
- https://www.classdojo.com/points/
- https://help.classdojo.com/hc/en-us/articles/205494185-How-to-Set-Up-and-Award-Points-to-Groups
- https://help.classdojo.com/hc/en-us/articles/209619243-How-to-Undo-a-Point
- https://help.classdojo.com/hc/en-us/sections/200472659-Class-Points-and-Reports
- https://help.classdojo.com/hc/en-us/articles/205647205-How-to-Redeem-Class-Points
