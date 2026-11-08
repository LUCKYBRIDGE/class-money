# Rooster Money — 루틴·과업·승인 UI·UX 심층 분석

기준일: 2026-11-08  
증거 수준: 공식 Chores/Tracker 가이드와 Help 기반.

## 1. 복잡성의 원천
Allowance, Allowance chores, Extra earners, 일정, 승인, Overdue, Skip, Re-open, 부분지급, 자녀별 목록이 얽힌다.

이 복잡성은 ‘할 일 앱’과 ‘용돈 앱’이 결합하면서 생긴다.

## 2. 핵심 해법: 과업 유형을 먼저 분리
Allowance chore와 Extra earner를 다른 개념으로 둔다.

Allowance chore:
정기 용돈과 연결된 책임.

Extra earner:
완료할 때마다 추가 보상을 받는 과업.

Class Money에서:
기본 직업업무와 추가 과업을 같은 목록에 섞지 않아야 한다.

## 3. 시간 중심 IA
과업을 단순 목록이 아니라:
- Today
- Overdue
- Coming Up
- Done/Missed
처럼 시간 상태로 분류한다.

이 구조는 Class Money의 학생 오늘 할 일 화면에 매우 적합하다.

## 4. 승인 상태를 명확히
학생:
완료 → 승인 요청

보호자:
Approve / Re-open / Not Done

Class Money:
제출됨 / 확인됨 / 다시 하기 / 면제
정도로 초등 친화적으로 번역할 수 있다.

## 5. 대량 승인
여러 과업을 Select / Select All로 bulk approve 가능.

교실에서는 반드시 필요하다.
학생 25명의 과업을 개별 열어서 승인하면 유지되지 않는다.

Class Money 교사 Inbox:
- 모두 선택
- 조건별 선택
- 일괄 승인
- 예외 학생만 따로 처리

## 6. Swipe처럼 빠른 상태변경
공식 Help는 알림함/과업목록에서 swipe로 Approve/Re-open할 수 있는 패턴을 설명한다.

Class Money 모바일에서도:
- 오른쪽 승인
- 왼쪽 다시 하기
같은 gesture를 고려할 수 있지만,
오작동 방지를 위해 되돌리기와 명확한 시각 피드백이 필요하다.

## 7. Skip의 중요성
예정된 과업을 학생 사정 때문에 수행하지 못할 때 Skip하면 allowance 계산에서 제외할 수 있다.

이것은 교실에서 특히 중요하다.

결석, 지원 필요, 행사 등으로 일을 못한 학생을 자동 미완료 처리하면 공정성 문제가 생긴다.

Class Money:
미완료와 면제를 반드시 구분.

## 8. 부분 지급 정책
모든 과업 완료 여부에 따라 full / none / percentage 지급이 가능하다.

Class Money는 이를 직업 정책으로 제공할 수 있으나 기본은 단순하게 유지한다.

예:
- 정상 지급
- 면제
- 일부 지급
- 보류

교사 사유 기록 필수.

## 9. Master Chores List
자녀별 일상 화면과 별개로 전체 과업을 한 곳에서 관리하는 관리화면이 있다.

Class Money도:
학생용 오늘 할 일
vs
교사용 전체 직업/과업 관리
를 분리해야 한다.

## 10. UX 위험
- 과업이 너무 많으면 돈을 받기 위한 체크리스트 게임이 됨.
- 승인 요청이 많으면 교사 Inbox 폭증.
- 모든 공동체 책임에 보수를 붙이면 외재적 보상 의존.
- Swipe 같은 빠른 조작은 오입력 위험.

## 11. Class Money 적용
- 기본직업업무 / 추가과업 분리
- Today 중심 학생 화면
- Overdue와 Exempt 분리
- bulk approve
- Re-open
- 반복 일정
- 학생별 예외
- 빠른 조작 뒤 Undo

## 12. Craft Anything 실측 항목
- Today/Overdue/Coming Up 정보계층
- child switch
- 과업 승인 bulk flow
- Re-open 피드백
- Skip가 allowance 계산에 반영되는 방식
- 반복 과업 생성
- 모바일 swipe 사용성

## 공식 근거
- https://roostermoney.com/feature/chores-guide/
- https://roostermoney.com/feature/chore-app-rooster-money/
- https://support.roostermoney.com/en/articles/2943441-how-can-i-manage-and-approve-chores-card-feature
