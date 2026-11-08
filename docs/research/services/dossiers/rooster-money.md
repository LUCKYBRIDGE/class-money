# NatWest Rooster Money Product Anatomy

기준일: 2026-11-08  
범위: 공식 Tracker, Chores guide, Help.  
목적: 정기 용돈·추가 earning·반복과업·공유기기 루틴 분석.

## 1. 제품 경계와 정체성

Rooster Money는 가정의 pocket money routine을 관리하는 서비스다.

핵심:
- Scheduled allowance
- Virtual Money Tracker
- Chores
- Allowance chores
- Extra earners
- Approval
- Partial/full/none allowance
- Stars
- Savings / pot history
- Child login
- Shared-device switch user

Class Money가 참고할 핵심은 금융기능보다 **정기경제의 생활 리듬과 과업 분류**다.

## 2. 사용자 역할

### Parent/Guardian
아이, allowance, chore, schedule, approval, payout policy 설정.

### Child
오늘 chore 확인, 완료 제출, photo proof, goal/history 확인.

공유기기에서는 switch user.

## 3. 핵심 객체

- Child
- Allowance
- Allowance period
- Chore
- Allowance chore
- Extra earner
- Recurrence rule
- Chore submission
- Approval
- Skip / Not Done / Re-open
- Earnings
- Stars / virtual reward
- Pot / History

## 4. 기능 구조도

~~~mermaid
flowchart TD
  A[Allowance] --> AP[Allowance Period]
  C1[Allowance Chore] --> AP
  C2[Extra Earner] --> ER[Extra Reward]
  C1 --> SUB[Submission]
  C2 --> SUB
  SUB --> REV[Review]
  REV --> DONE[Approved]
  REV --> RE[Re-open]
  REV --> ND[Not Done]
  AP --> PAY[Allowance Payout]
  DONE --> ER
  PAY --> POT[Pot]
  ER --> POT
  POT --> HIST[History]
~~~

## 5. 가장 중요한 도메인 구분: Allowance Chore vs Extra Earner

**E1 확인**
- Allowance chore: 정기 allowance와 연결.
- Extra earner: 개별 monetary/star reward.

이 구분이 매우 중요하다.

### D Class Money
교실에서도 다음을 분리:
1. 공동체 기본책임 — 무보수 가능
2. 직업 기본업무 — 정기급여와 연결
3. Extra Task — 별도 추가보수

모든 행동을 micro-payment로 만들지 않는다.

## 6. Schedule UX

공식 Chores:
- daily
- weekly
- monthly
- one-off
- 특정 time of day
- rotating chores
- start day / stagger

### 좋은 점
기술적인 스케줄 expression이 아니라 생활언어로 구성.

### D Class Money
교실 schedule preset:
- 매일
- 매주 특정요일
- 격주
- 매월 첫/마지막 주
- 일회성
- 학기중 특정 기간

cron expression 같은 설정은 노출하지 않음.

## 7. Master Chores List와 Today View

공식:
- Master Chores list: 전체 고수준 관리
- Today’s Chores: 오늘 + overdue 집중

**중요 IA**
관리자는 전체 시스템을 보지만, 일상 실행은 **오늘의 것만** 본다.

Class Money:
Teacher:
전체 Job/Task 관리 페이지 + Home Today queue.

Student:
오늘 할 일 + overdue.

## 8. Submission / Approval

Child:
chore 완료 → submit → optional photo proof.

Parent:
- individual approve
- bulk approve
- Re-open
- Not Done
- Skip

이 상태모델은 Class Money 과업에 매우 유용하다.

추천 상태:
TODO → SUBMITTED → APPROVED → PAID  
SUBMITTED → REOPENED → TODO  
TODO/SUBMITTED → SKIPPED  
TODO → NOT_DONE.

## 9. Bulk Approval

공식:
To Approve에서 select / select all → bulk approve.

Class Money는 25명 학급에서 개별 approval만 두면 운영불가.

교사 Inbox:
- 같은 task 18건 묶음
- 전체 승인
- 선택 제외
- 일괄 사유
기능 필요.

## 10. Allowance Payout Policy

공식:
미완료 chores가 있을 때:
- full allowance
- no allowance
- percentage
- parent prompted

이것은 경제 rule을 설정가능하게 만든다.

### D Class Money
직업급여:
- Full
- Completion percentage
- Teacher decides
- Base + performance component

단, 장애/결석/지원 필요 사유를 고려한 exception 필수.

## 11. Overdue / Skip

Rooster는 future task가 다른 일정 때문에 불가능하면 Skip하여 allowance calculation에서 제외할 수 있다.

이것은 **미완료와 면제를 분리**하는 좋은 상태 모델이다.

Class Money:
미완료:
- 학생 책임
면제:
- 공식적으로 수행 필요 없음
결석:
- 별도 status
로 분리.

## 12. Virtual Money Tracker

공식 Tracker는 실제 돈이 입금되지 않는 virtual money 방식.

Class Money 역시 이 모델과 유사:
real money가 아닌 simulation.

중요:
실제 금융 UI를 흉내 내더라도 ‘실제 현금 가치 없음’을 명확히.

## 13. Child UX

아이는:
- 오늘 chores
- 완료표시
- approval 상태
- pot/history
를 본다.

복잡한 payout configuration은 보지 않는다.

Class Money 학생 UI:
‘급여 계산규칙 편집’ 대신
- 오늘 해야 할 일
- 급여 받기까지 남은 일
- 다음 지급일
정도로 표현.

## 14. Stars / Money

Rooster는 money와 stars라는 다른 reward system을 둘 수 있다.

Class Money에서 얻는 원칙:
모든 보상을 경제화폐로 통합할 필요 없음.

예:
- 경제화폐
- 비금전 badge
정도로 분리.

단, reward currency를 여러 개 남발하면 복잡도가 증가.

## 15. 복잡성을 풀어낸 방식

1. allowance chore / extra earner 분류
2. recurring schedule preset
3. Master list vs Today view
4. submit/review 상태
5. bulk approve
6. re-open/not-done/skip 분리
7. payout policy
8. child/parent surface 분리
9. shared-device switch user

## 16. Class Money에 가져올 것

**강하게**
- task type 분리
- today view
- bulk approval
- skip/absent/not-done 구분
- schedule preset
- partial payout policy
- next payday visibility
- shared-device switch user

**변형**
- photo proof는 교실에서는 과도할 수 있어 선택기능
- stars는 badge layer로.

## 17. Craft Anything 실측

- parent chores list
- Today vs Master
- chore creation
- schedule chooser
- allowance/extra earner selector
- child submit
- photo proof
- bulk approve
- Re-open/Skip/Not Done visual
- shared-device user switch
- allowance payout setting

## 18. 현재 판단

Rooster Money의 가장 큰 강점은 **복잡한 과업·용돈 시스템을 반복 루틴으로 안정화**한 것이다. Class Money 직업/업무/급여 시스템에서 직접 참고 가치가 높다.

## 공식 근거
- https://roostermoney.com/feature/getting-started-with-roostermoney-tracker/
- https://roostermoney.com/feature/chores-guide/
- https://roostermoney.com/feature/chore-app-rooster-money/
- https://support.roostermoney.com/en/articles/2943417-linking-chores-to-allowance
- https://support.roostermoney.com/en/articles/2943433-set-extra-earners-to-earn-additional-money-card-feature
