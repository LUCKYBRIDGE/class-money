# Greenlight — 기능 얽힘·UI·UX 심층 분석

기준일: 2026-11-08  
분석 목적: 실제 금융상품이 아니라 **아동의 돈 배분·목표·승인·과업 UI**를 분석

## 1. 복잡성의 본질
아동금융은 하나의 잔액이 아니라 여러 목적의 돈과 여러 권한이 동시에 존재한다.

\`\`\`mermaid
flowchart LR
 A[Allowance/Chore Earnings] --> AL[Allocation]
 AL --> SP[Spend]
 AL --> SV[Savings]
 AL --> GV[Give]
 AL --> GL[Savings Goal]
 P[Parent Permissions] --> SV
 P --> GL
 P --> TR[Transfers]
 C[Chores] --> A
\`\`\`

복잡한 부분은:
- 얼마를 지급할지
- 어디에 넣을지
- 아이가 스스로 옮길 수 있는지
- 목표에서 꺼낼 때 승인할지
를 동시에 관리하는 것이다.

## 2. 복잡함을 푸는 핵심: 돈의 목적을 카드/범주로 보이게 함
Spend Anywhere, General Savings, Give, Savings Goal 등 돈의 용도별 공간을 나눈다.

Class Money:
학생에게 ‘총잔액’보다
- 지금 쓸 돈
- 모아둘 돈
- 목표
- 공동체
를 별도 카드로 표시.

## 3. Allocation UI
Allowance나 pay-per-chore를 설정할 때 돈이 들어올 위치를 비율/정액으로 나눈다. 합계가 100%가 아니면 저장할 수 없다.

좋은 UX:
- 복잡한 자동이체 규칙을 “각 목적에 얼마?”라는 단순 질문으로 바꿈.
- 잘못된 총합을 저장 전 차단.
- 여러 아이에게 없는 category를 선택하면 오류를 미리 보여줌.

Class Money:
급여설정에서
“학생이 직접 나누게 하기 / 기본비율 적용 / 전액 사용가능”
세 옵션 정도로 단순화.

## 4. Chore UI의 상태 표현
아이 화면에는 Progress / Allowance / Earnings처럼 과업 상태를 나눠 보여주고:
- To do
- Pending Review
- Paid
를 진행률로 표현한다.

이것은 Class Money의 직업업무/과업에도 매우 유용하다.

학생:
해야 할 일 → 제출 → 확인 기다림 → 지급됨.

교사:
확인 대기만 Inbox에 모음.

## 5. Approval을 모든 것에 강제하지 않음
Savings→Spending 이동 승인 여부를 자녀별 permission으로 켜고 끌 수 있다.

핵심:
‘보호’와 ‘자율성’을 둘 중 하나로 선택하지 않고 **행동별 permission**으로 분해한다.

Class Money:
- 저축 인출
- 학생간 송금
- 고액구매
- 특별과업
등을 별도 승인정책으로 설정.

## 6. Savings Goal UI
목표 이름 + 목표액 + 현재액 + progress.
목표에서 돈을 꺼내는 경우 승인 요청이 가능하다.

Class Money에서 목표는 소비와 연결:
“이 상품을 사면 목표 달성이 현재 설정 기준 약 2주 늦어져요.”

목표를 별도 페이지에 고립시키지 않고 구매결정 순간에도 노출.

## 7. Parent/Kid 정보구조 분리
부모는:
- 설정
- allowance
- permissions
- 거래/알림

아이는:
- 과업
- 현재 돈
- 저축/목표
- 소비

같은 데이터라도 목적이 달라 화면을 다르게 구성한다.

Class Money도 Teacher dashboard를 단순 축소해 학생에게 보여주지 않는다.

## 8. UI에서 숨긴 복잡한 규칙
사용자에게 분배 합계 100%만 보여주지만 내부적으로는:
- 아이마다 존재하는 category 차이
- 권한
- 지급주기
- 과업 완료
를 동시에 검증한다.

Class Money 원칙:
복잡한 검증은 시스템이 하고 학생은 필요한 결과만 이해한다.

## 9. 위험
실제 금융앱의 카테고리를 많이 가져오면 초등 교실에서 지나치게 복잡해진다.

초기 기본:
2~4개 money bucket만.
사용자가 임의 category를 무한 생성하는 기능은 나중에 검토.

## 10. Class Money 적용
- 돈의 목적별 카드.
- 급여 수령 시 allocation.
- 과업 상태 Progress/Pending/Paid.
- 행동별 permission.
- Savings Goal을 구매결정과 연결.
- 교사/학생 정보구조 분리.
- 저장 전 규칙 검증.

## 공식 근거
- https://help.greenlight.com/hc/en-us/articles/50527840580379-How-do-I-pay-my-child-per-chore-and-split-the-earnings
- https://help.greenlight.com/hc/en-us/articles/360023614253-How-do-I-set-up-an-allowance-for-my-child
- https://help.greenlight.com/hc/en-us/articles/360009173153-How-do-Savings-Goals-work-How-do-I-set-them-up
- https://help.greenlight.com/hc/en-us/articles/45088782307867-How-do-I-manage-my-child-s-account-permissions
- https://help.greenlight.com/hc/en-us/articles/360019317134-How-can-my-children-see-and-manage-their-chores
