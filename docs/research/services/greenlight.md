# Greenlight 심층 분석

기준일: 2026-11-08  
분석 목적: 실제 금융서비스를 복제하지 않고 아동의 돈 배분·저축 목표·보호자 승인 UX를 연구  
주의: Class Money는 실제 계좌/카드 연동을 목표로 하지 않는다.

## 1. 왜 분석하는가

Greenlight는 ‘아이가 돈을 가진 뒤 무엇을 하게 할 것인가’를 잘 보여주는 사례다.

교실경제 앱들은 돈을 버는 기능에는 강하지만, 학생이 들어온 돈을 소비/저축/기부/목표로 어떻게 나눌지 계획하는 기능은 상대적으로 약할 수 있다.

## 2. 핵심 구조

공개 도움말에서 확인되는 주요 요소:
- recurring allowance
- chores
- pay per chore
- Spend categories
- General Savings
- Savings Goals
- Give
- 부모/보호자 permissions
- 목표 저축에서 돈을 꺼낼 때 승인 설정
- 부모 지급 이자
- 사용 내역과 잔액

## 3. 가장 중요한 패턴: 수입 시점의 자동 배분

Allowance나 chore earning이 들어올 때:
- Spend
- Savings
- Give
- 기타 카테고리
로 비율 또는 금액을 정할 수 있다.

총 배분은 100%가 되어야 저장된다.

Class Money 적용:
‘급여를 받으면 어디에 둘까요?’

예:
- 지금 쓸 돈 50%
- 목표저축 40%
- 공동체기금 10%

핵심은 급여가 들어온 뒤 나중에 저축을 ‘생각해보는’ 것이 아니라 수입 시점부터 계획하게 하는 것이다.

## 4. 학생에게 보여줄 잔액은 하나가 아닐 수 있다

Greenlight는 Spending, Savings, Invest, Giving 등 계정/범주를 나눠 보여준다.

Class Money 초등용 단순화:
- 사용 가능
- 모아두기
- 목표 저축
- 공동체

‘총자산’보다 각 돈의 용도를 먼저 보여준다.

## 5. Savings Goals

확인된 기능:
- 목표 이름
- 목표 금액
- 진행률
- 돈 옮겨 넣기
- 목표 수정
- 목표 비공개 설정
- 목표에서 돈을 빼려면 보호자 승인을 요구할 수 있음
- 목표 달성 이후 사용/일반저축 이동/목표 확대 가능

Class Money에서 매우 유용한 학습 패턴:
저축목표를 단순 progress bar가 아니라 선택의 기준점으로 사용.

상품을 살 때:
‘이 구매를 하면 목표 달성이 약 2주 늦어져요.’
처럼 연결 가능.

## 6. 목표에서 돈을 꺼내는 마찰

Greenlight는 저축에서 돈을 꺼낼 때 보호자 승인을 설정할 수 있다.

교육적으로 중요한 것은 ‘못 쓰게 막는 것’보다 한 번 더 생각하게 만드는 것이다.

Class Money:
저축 인출 옵션:
- 자유
- 확인 한 번
- 교사 승인
을 수업설정에 따라 선택.

교사 승인을 기본으로 강제하면 학생 자율성이 너무 떨어질 수 있다.

## 7. Parent-Paid Interest의 시사점

부모가 아이의 저축에 이자를 지급할 수 있다.

Class Money:
이자는 실제 금융상품 수익을 재현하는 것보다:
- 일정 기간 유지
- 꾸준한 저축
- 복리 실험
을 보여주는 수업 도구로 사용.

초기에는 단순 이자부터.

## 8. Permissions에서 배울 것

Greenlight는 자녀의:
- savings transfer
- sibling transfer
- goal sharing
등을 개별 권한으로 켜고 끌 수 있다.

Class Money도 ‘학생 권한’을 하나의 student role로 뭉치지 않는다.

예:
- 구매 가능
- 저축 이동 가능
- 학생 간 송금 가능
- 상품 판매 가능
- 목표 공유 가능

기능별 권한 토글.

## 9. Chore와 급여 구조

과업당 금액을 정하고 완료에 따른 보상을 설정한다.

Class Money에서는 과업을:
- 직업의 반복업무
- 1회성 학급 과업
- 공동체 과업
으로 분류.

단, 모든 교실 책임을 돈으로 전환하면 공동체 책임이 외재적 보상에 종속될 수 있으므로 교사가 ‘무보수 공동책임’도 설정할 수 있어야 한다.

## 10. 실제 금융 앱에서 그대로 가져오면 안 되는 것

- 실제 카드
- 실제 결제
- 실제 투자
- 실제 금융계좌
- 가족 간 실제 송금
- 실제 이율 경쟁

Class Money가 가져올 것은 금융 인프라가 아니라 ‘아이에게 돈의 목적을 보이게 하는 UX’다.

## 11. Class Money에 가져올 것

강하게:
1. 급여 자동 배분
2. 목적별 돈 구분
3. 목표저축
4. 저축 인출에 선택적 마찰
5. 권한 세분화
6. 이자 학습
7. 과업→보수 연결

특히 추천:
학생 홈에서 ‘총 잔액’보다 ‘사용 가능’ 금액을 가장 크게 보여준다.

## 12. Craft Anything 후속 실측

공개/정당한 접근 범위에서:
- allowance 생성
- allocation UX
- 목표 생성
- 목표 돈 이동
- 인출 승인 요청
- permissions 화면
- 부모/아이 화면 정보 차이
- 목표 달성 후 행동
- 잔액 화면 정보계층

## 13. 현재 판단

Greenlight의 가장 큰 시사점은 ‘버는 순간부터 계획한다’이다.

Class Money가 이를 초등 교실에 적용하면:
급여 → 잔액 증가
가 아니라
급여 → 계획 → 사용할 돈/모을 돈/공동체 돈
으로 바뀐다.

## 공식 근거
- https://help.greenlight.com/hc/en-us/articles/360023614253-How-do-I-set-up-an-allowance-for-my-child
- https://help.greenlight.com/hc/en-us/articles/50527840580379-How-do-I-pay-my-child-per-chore-and-split-the-earnings
- https://help.greenlight.com/hc/en-us/articles/360009173153-How-do-Savings-Goals-work-How-do-I-set-them-up
- https://help.greenlight.com/hc/en-us/articles/45088782307867-How-do-I-manage-my-child-s-account-permissions
