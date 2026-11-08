# Greenlight — 돈 배분·목표·권한 UI·UX 심층 분석

기준일: 2026-11-08  
목적: 실제 금융 인프라가 아니라 아동의 돈 계획과 보호자 통제 UX 분석.

## 1. 복잡성의 원천
아이의 돈은 spending, savings, goals, giving, chores, allowances, permissions 등 여러 상태로 분산된다. 보호자는 여러 아이를 관리한다.

## 2. 핵심 해법: Child Dashboard와 Account 구분
공식 Help에서 목표 생성 흐름은 child dashboard → Accounts → Save → Savings Goal처럼 계층화되어 있다.

복잡한 금융기능을 첫 화면에 전부 놓지 않고:
아이 선택 → 돈 영역 → 세부 목적
순으로 내려간다.

## 3. 목표 UI
Savings Goal은:
- 목표 이름
- 목표 금액
- 진행률
- Move In
- 편집
- privacy
- Round Ups
를 하나의 목표 객체에 묶는다.

Class Money는 목표를 독립 카드로 만들고:
현재 / 목표 / 남은금액 / 예상기간
을 한눈에 보여준다.

## 4. 돈 이동의 출처와 목적을 명시
목표에 돈을 넣을 때 어디에서 가져오는지를 선택한다.

Class Money에서도 단순 +20이 아니라:
쓸 돈 → 목표저축
이라는 이동을 명확히 한다.

계좌 간 이동은 새 돈이 생긴 것이 아님을 UI에서도 보여준다.

## 5. Chore Payment Allocation
과업별 금액을 정한 뒤 earnings가 어떤 category로 갈지 비율/금액으로 배분한다.

복잡한 규칙을:
과업 상세 → Payment → Amount & allocation
이라는 국소 설정으로 묶는다.

Class Money의 직업/과업 설정에서도 급여배분을 해당 업무 안에서 설정할 수 있다.

## 6. Permissions를 기능별 토글로 나눔
Savings 이동, 형제간 이동, 공유 목표 등 권한을 하나의 ‘자녀 권한’으로 뭉치지 않고 기능별로 나눈다.

Class Money:
학생별로 구매, 저축이동, 목표공유, 학생간송금, 운영보조 권한을 분리해야 한다.

## 7. Family Hub에서의 공용보기와 관리자 PIN
Chores는 가족 모두 볼 수 있지만 생성/수정/삭제는 관리자 PIN이 필요하다.

Class Money 적용:
학급 공용 화면에서는 오늘의 역할/학급 목표 같은 정보는 보여주되 학생 자산과 정책 변경은 교사 인증 뒤에만 허용.

## 8. UX 위험
- 실제 금융 앱의 카테고리 수를 그대로 가져오면 초등에게 복잡.
- 모든 저축 이동을 교사 승인으로 만들면 자율성 저하.
- 보호자 중심 승인모델을 교사에게 그대로 적용하면 업무 폭증.

## 9. Class Money 적용
- 학생 홈은 2~4개의 돈 목적만 노출
- 목표를 카드 객체로 관리
- 돈 이동 출처/목적 표시
- 수입 발생 시 선택적 자동배분
- 기능별 권한
- 위험한 행동만 승인
- 공용 디스플레이와 관리자 영역 분리

## 10. Craft Anything 실측 항목
- 목표 생성 깊이
- Move In/Out 흐름
- allocation 편집
- 권한 화면의 정보밀도
- child switch
- Family Hub와 앱의 역할 차이
- 학생/보호자 홈의 시각적 우선순위

## 공식 근거
- https://help.greenlight.com/hc/en-us/articles/360009173153-How-do-Savings-Goals-work-How-do-I-set-them-up
- https://help.greenlight.com/hc/en-us/articles/50527840580379-How-do-I-pay-my-child-per-chore-and-split-the-earnings
- https://help.greenlight.com/hc/en-us/articles/45088782307867-How-do-I-manage-my-child-s-account-permissions
- https://help.greenlight.com/hc/en-us/articles/52141594156571-How-do-Chores-work-on-Greenlight-Family-Hub
