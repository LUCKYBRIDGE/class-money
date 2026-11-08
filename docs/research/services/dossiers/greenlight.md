# Greenlight Product Anatomy

기준일: 2026-11-08  
범위: 공식 Allowance, Chores, Savings Goals, Permissions, Family Hub help.  
목적: 실제 금융상품이 아니라 **아동의 돈 배분·목표·승인 구조** 분석.

## 1. 제품 경계와 정체성

Greenlight는 부모/보호자가 자녀의 실제 금융생활을 관리하면서 아이에게:
- allowance
- chores
- Spend
- Savings
- Giving
- Goals
- permissions
- child app
을 제공하는 가족 금융 플랫폼이다.

Class Money는 실제 금융계좌나 카드를 따라갈 필요가 없으며, **money purpose + autonomy model**을 참고한다.

## 2. 사용자 역할

### Primary Accountholder / Authorized Approver
Allowance, chore rule, allocation, permissions, savings transfer approval.

### Child
Chores 확인/완료, earnings 상태 확인, Spend/Savings/Goal 사용.

### Family Hub
공유 화면에서 chores view. 수정은 admin PIN 필요.

**핵심 구조**
같은 데이터라도:
- 부모는 설정/승인
- 아이는 실행/진행
- shared display는 조회 중심
으로 surface가 다르다.

## 3. 핵심 도메인 객체

- Child profile
- Parent/Admin
- Allowance
- Allowance schedule
- Chore
- Chore completion
- Review state
- Pay-per-chore earning
- Allocation rule
- Spending bucket
- General Savings
- Giving
- Goal
- Permission
- Transfer request
- Family Hub view

## 4. 기능 구조도

~~~mermaid
flowchart TD
  C[Chores] --> CR[Completion/Review]
  CR --> E[Earnings]
  A[Allowance] --> E
  E --> AL[Allocation]
  AL --> SP[Spend]
  AL --> SV[General Savings]
  AL --> GV[Giving]
  AL --> GL[Goal]
  P[Permissions] --> SV
  P --> GL
  P --> TR[Transfers]
  FH[Family Hub] --> C
~~~

## 5. Allowance Flow

공식:
1. child dashboard
2. Set up allowance
3. amount
4. schedule: weekly/biweekly/monthly + day
5. allocate allowance
6. 각 category percentage
7. total 100% requirement

**핵심 UX**
복잡한 자동이체/계좌분배를 **“이 돈을 어디에 얼마나 둘까?”**라는 한 질문으로 바꾼다.

### D Class Money
급여 수령 정책:
- 전액 사용가능
- 추천 배분
- 학생이 직접 배분

예:
쓰는 돈 50 / 목표저축 30 / 모아두기 10 / 공동체 10.

## 6. Chores 상태 모델

공식 Child Chores:
- Progress
- Allowance
- Earnings

Earnings 상태:
- Paid
- Pending Review
- To do

Family Hub에서는:
- reward 없음
- pay per chore
- star reward
- required for allowance
처럼 chore reward type도 나뉜다.

### 구조적 교훈
Chore와 Reward가 하나가 아니다.

Class Money 과업:
Task definition
+ completion state
+ reward policy
+ payment state
를 분리.

## 7. Allowance와 Chores 연결

공식:
- flat-rate allowance
- chores와 연결
- partial payment
- all-or-nothing

즉 같은 allowance라도 지급조건을 다르게 선택.

### D Class Money
직업급여 정책:
- 정액 자동
- 완료비율
- 교사 결정
- 면제/예외

주의:
결석/지원 필요 학생에게 자동 불이익이 없도록 override.

## 8. Allocation

Greenlight는 Spend Anywhere / General Savings / Giving / Cash to Invest 등으로 자동분배.

**UX 강점**
돈이 들어온 후 ‘나중에 생각’이 아니라 income event에 planning을 붙인다.

Class Money 학생 학습:
Payday notification → 배분 제안 → 학생 확정 → wallet update.

단, 저학년에서는 2개 bucket만.

## 9. Savings Goals

공식:
- goal name
- amount
- round ups 옵션
- private
- move money in
- progress
- goal에서 돈을 쓰려면 transfer request
- parent-paid interest가 goal에도 적용

**핵심**
Goal은 단순 시각화가 아니라 money movement permission과 연결.

Class Money:
Goal withdrawal:
- 자유
- 확인 한 번
- 교사 승인
중 선택.

## 10. Permissions

공식 child permission:
- share savings goals
- referral
- transfer out of savings
- sibling transfer
- Paylink

Permission은 child profile별 toggle.

**구조적 강점**
‘학생에게 자율성 있음/없음’이 아니라 **행동별로 자율성을 분해**.

### D Class Money
학생 권한:
- 저축→사용가능 이동
- 학생간 송금
- 판매
- 고액구매
- 목표 공유
를 각각 설정.

## 11. Family Hub — Shared Surface

공식:
가족 전체가 chores를 PIN 없이 조회할 수 있지만 create/edit/delete는 parent admin PIN 필요.

이 구조는 교실 shared display에 매우 유용하다.

Class Money projector/shared screen:
조회 가능:
- 오늘 공동 할 일
- 학급 공동 목표
- 국고

관리 불가:
- 개인 잔액
- 지급
- 설정
- 개인정보.

## 12. 복잡성을 풀어낸 방식

1. child dashboard 중심
2. 돈을 purpose bucket으로 분리
3. allowance setup wizard
4. chore status를 Progress/Paid/Pending으로 분리
5. permission을 행위별 toggle
6. goal과 withdrawal approval 연결
7. shared display는 read-heavy / admin protected

## 13. UI의 중요한 디테일

Allowance 설정에서 100%가 아니면 저장하지 않는 것은 **invalid economic rule을 저장 전에 차단**하는 패턴.

Class Money도:
- 세율 총합 오류
- 배분 100% 오류
- salary보다 fixed expense 과다
- 상품가격 0
같은 문제를 Save 후 경고하지 않고 설정 단계에서 차단/경고.

## 14. 교육적 리스크

실제 가정용 Chore 시스템을 교실에 그대로 옮기면 모든 공동체 책임이 돈과 연결될 수 있다.

Class Money는:
- 무보수 공동책임
- job
- paid extra task
를 구분해야 함.

학생이 “돈 안 주면 안 함”을 학습하지 않도록 경제영역의 경계를 명확히.

## 15. Class Money에 가져올 것

**강하게**
- income allocation
- purpose bucket
- goal
- chore/payment state separation
- partial/all-or-nothing policy
- per-action permission
- shared display permission
- save-time validation

**제외**
- 실제 card/account/invest
- real-world transfers/referral.

## 16. Craft Anything 실측

- Parent Home vs Child Home
- allowance setup wizard
- allocation % interaction
- child chores tab
- Progress/Allowance/Earnings tabs
- pending review
- goal create/move out
- permission screen
- Family Hub shared view
- mobile navigation

## 17. 현재 판단

Greenlight의 가장 큰 설계 가치는 **자녀의 돈을 하나의 잔액으로 보지 않고 목적과 권한으로 분해하는 것**이다. Class Money 학생 지갑과 승인정책에 직접 참고 가치가 크다.

## 공식 근거
- https://help.greenlight.com/hc/en-us/articles/360023614253-How-do-I-set-up-an-allowance-for-my-child
- https://help.greenlight.com/hc/en-us/articles/360019317134-How-can-my-children-see-and-manage-their-chores
- https://help.greenlight.com/hc/en-us/articles/360023614373-Are-chores-and-allowances-connected
- https://help.greenlight.com/hc/en-us/articles/360009173153-How-do-Savings-Goals-work-How-do-I-set-them-up
- https://help.greenlight.com/hc/en-us/articles/45088782307867-How-do-I-manage-my-child-s-account-permissions
- https://help.greenlight.com/hc/en-us/articles/52141594156571-How-do-Chores-work-on-Greenlight-Family-Hub
