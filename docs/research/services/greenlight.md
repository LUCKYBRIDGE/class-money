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


## 심화 보완: 12개 분석축

### A. 사용자와 권한
Greenlight는 보호자가 자녀 금융범주와 권한을 관리하는 구조다. 교실에 그대로 적용하지 않되 '돈 이동 권한'과 '보기 권한'을 구분하는 패턴은 참고할 가치가 있다.

Class Money:
- 자기 저축 이동: 학생 가능
- 상점 주문: 학생 요청
- 고액/특수거래: 교사 승인
- 정책 변경: 교사만

### B. 돈의 버킷 모델
Spend, Savings, Give, Goal 등 목적별로 돈을 나눈다.

Class Money 계좌구조:
- available
- savings
- goal-specific subaccount
- classroom/public fund
를 별도로 둘 수 있다.

총자산과 사용가능액을 분리하는 것이 중요하다.

### C. 수입 상태전이
Chore 설정 → 완료 → 지급 → allocation → 각 bucket 반영

Class Money에서는:
직업/퀘스트 완료 → 지급 확정 → 학생 자동배분 규칙 → 지갑/저축/기여 분개
로 만들 수 있다.

### D. 학생 JTBD
- 얼마 벌었는가
- 얼마 쓸 수 있는가
- 무엇을 위해 모으는가
- 목표까지 얼마나 남았는가

이 네 질문은 Class Money 학생 홈의 핵심이다.

### E. 자동배분의 교육성
학생이 미리 저축비율을 결정하면 돈을 받은 뒤 남으면 저축하는 행동보다 계획적이다.

Class Money는 자동배분을 '교사가 정해주는 규칙'보다 학생의 선택으로 두고 주기적으로 수정/회고하게 하는 편이 좋다.

### F. 목표저축 상태
목표생성 → 자금이동 → 진행 → 달성 → 사용/유지/종료

달성 후 행동이 중요하다. 목표 완료 즉시 자동 구매보다 학생이 다시 선택하도록 한다.

### G. 잠금과 자율성
저축에서 돈을 빼는 마찰은 충동소비를 줄이지만 과도하면 교사가 돈을 통제하는 경험이 된다.

권고:
- 기본은 학생 자율
- 인출 시 목표영향 미리보기
- 선택적으로 승인 잠금

### H. 실제 금융과 모의경제 경계
Greenlight의 실제 카드·투자기능은 Class Money 범위 밖이다.

Class Money에서 '현실적인 금융'은 실제 돈을 연결하는 것이 아니라:
- 정확한 거래
- 명확한 잔액
- 목표
- 선택 결과
를 모사하는 것이다.

### I. 실패모드
- allocation 합이 100%가 아님
- goal 삭제 시 잔액 처리
- 자동배분 대상 goal이 종료됨
- 급여가 0/음수
- class fund 배분 후 환불

각 경우의 fallback 계정을 명시해야 한다.

### J. UI 정보계층
총자산보다 사용가능액이 학생에게 더 중요하다.

Class Money:
큰 숫자 = 오늘 사용가능
작은 카드 = 저축/목표/공동체
하단 = 최근 거래

### K. 제품결정
Adopt:
- bucket
- goal
- auto allocation
- permissioned requests

Adapt:
- protected savings

Avoid:
- 실제 금융망
- 투자/카드 연동

### L. 남은 실측
- allocation 화면의 이해성
- goal 달성 후 흐름
- 자녀/보호자 화면차이
- permission 변경
- 여러 goal의 정보밀도

## V4 심층 해부 — 돈을 받은 뒤가 아니라 받는 순간 계획하기

### 1. Allocation은 예산표보다 강한 행동설계다

Greenlight의 chore pay allocation은 수입이 발생할 때 Spend, Savings, Give, Goal 등으로 비율/금액을 바로 분배한다.

Class Money에서 이 아이디어는 단순 저축 기능보다 중요하다.

학생은 금요일에 100을 받은 뒤 남은 돈을 저축하는 것이 아니라:
- 60 사용
- 30 목표
- 10 공동체
라고 먼저 결정할 수 있다.

이는 계획이 소비보다 시간적으로 앞서게 만든다.

### 2. 자동배분은 학생의 선택이어야 한다

교사가 모든 학생에게 저축 30%를 강제하면 금융습관은 생길 수 있지만 자기결정 학습은 약해진다.

권고:
첫 2~3회는 매 급여마다 직접 배분.
그 후 학생이 ‘이 규칙을 앞으로 자동으로 적용’할 수 있게 한다.

자동화가 학습 뒤에 온다.

### 3. Bucket과 Account는 구분해야 한다

기술적으로 모든 목적을 실제 계좌로 만들 필요는 없다.

Class Money 모델 선택:
- ledger account: 가용지갑, 저축, 국고처럼 실제 돈 이동
- budget bucket: 계획상 목적만 지정

예:
‘다음 상점 구매용 30’은 실제 별도계좌일 수도 있고 예산 bucket일 수도 있다.

저학년에는 단순히 저축계좌,
고학년에는 예산 bucket까지 확장 가능하다.

### 4. Goal 해제는 중요한 학습 순간이다

학생이 목표저축 80 중 30을 다시 꺼내려 할 때 단순 허용/차단보다:
‘목표 달성이 약 1주 늦어질 수 있어요.’
를 보여주는 것이 좋다.

즉 시스템은 통제보다 결과 예측을 제공한다.

### 5. 실패 시나리오

- 자동배분 합계 100% 초과/미만
- 목표 삭제 후 연결된 돈의 귀속
- 목표 달성 뒤 계속 자동배분
- 급여보다 정액배분 합계가 큼
- 공동체기금 환불 시 원래 배분 복원

Class Money는 allocation rule을 버전 관리하고 거래마다 당시 규칙 snapshot을 남기는 편이 안전하다.

### 6. 최종 판단

Greenlight에서 가져올 핵심은:
‘돈을 받은 뒤 관리’가 아니라 ‘돈을 받는 순간 목적을 결정’하는 구조다.

이것은 Class Money 학생 경험의 강한 차별화 후보다.

근거:
- https://help.greenlight.com/hc/en-us/articles/50527840580379-How-do-I-pay-my-child-per-chore-and-split-the-earnings
- https://help.greenlight.com/hc/en-us/articles/360019240274-How-do-I-create-a-chore-for-my-child