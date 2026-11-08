# 서비스별 심층 분석 인덱스

기준일: 2026-11-08

이 폴더는 경쟁서비스를 하나의 점수표로 뭉뚱그리지 않고, 각 제품이 해결하는 문제를 독립적으로 분석한다.

## 분석 방법

Craft Anything의 Clean Room 원칙을 참고한다.

- 공개 화면·공식 문서·공개 도움말에서 확인 가능한 것만 ‘확인’으로 기록.
- 내부 코드, DB 구조, 비공개 로직은 추정하지 않음.
- 로그인 후 실제 조작을 하지 않은 UX는 실측 결과처럼 표현하지 않음.
- 원 서비스의 로고·카피·시각 디자인을 복제하지 않고 문제 해결 원리만 추출.
- 관찰 → 해석 → Class Money 제안 → 후속 실측을 분리.

Craft Anything 자체의 현재 상태상 Clean Room live build가 아직 모든 환경에서 실증된 것은 아니므로, 이 저장소에서는 현재 공개자료 문헌분석과 후속 실측 계획을 명확히 구분한다.

참고:
- https://github.com/storytold/craft-anything
- https://github.com/storytold/craft-anything/blob/main/docs/STATUS.md

## 공통 분석 틀

각 문서는 가능한 한 다음 순서로 본다.

1. 왜 분석하는가
2. 제품 정체성
3. 핵심 사용자와 사용 주기
4. 교사/관리자 흐름
5. 학생/아동 흐름
6. 경제 엔진 또는 보상 구조
7. 자동화
8. 권한과 안전
9. 학습 설계
10. UX에서 배울 점
11. 위험·한계
12. Class Money에 가져올 것
13. 가져오지 않을 것
14. Craft Anything 후속 실측 과제
15. 공식 근거

## 교실경제 서비스

### [ClassCoin](classcoin.md)
**핵심 질문:** 기능이 매우 많아졌을 때 학급경제와 학급경영을 어떻게 한 시스템에 묶는가?

주요 분석:
- 직업·자동급여
- 은행·세금·국고
- 부동산·투자·창업
- 게임재화 분리
- 기능 숨김과 메뉴 확장
- 국내 초등교실 맥락

### [ClassBank](classbank.md)
**핵심 질문:** 처음 쓰는 교사가 복잡한 경제를 어떻게 단계적으로 시작하는가?

주요 분석:
- 4개 기본 구성요소
- 단계형 온보딩
- 경제 가격/급여 가이드
- 학생 Banker/HR/Store Clerk
- 학생 공동 경제 설계
- Bills의 안전철학

### [Cashroom](cashroom.md)
**핵심 질문:** 디지털 거래 자체를 어떻게 수학·금융 학습 순간으로 만드는가?

주요 분석:
- 거래 전 새 잔액 계산
- 학생별 계산 accommodation
- Student job 기본소득
- 자동 payday/bills
- 단일 요청함
- 기능별 undo
- 영수증과 저축
- 대출/신용의 초등 적합성

### [Banqer Primary](banqer-primary.md)
**핵심 질문:** 경제 기능을 어떻게 ‘학습 개념 모듈’로 만드는가?

주요 분석:
- Basic Income
- Expenses
- Employment
- Banking
- Interest
- Tax
- Property/Insurance/Transport
- 영상·퀴즈·그룹활동
- 수업 시나리오와 시뮬레이션 연결

### [ClassCents](classcents.md)
**핵심 질문:** 교실경제 운영의 마찰을 얼마나 줄일 수 있는가?

주요 분석:
- 학생 로그인 선택
- 교사 단독 운영
- CSV/Excel/paste roster
- 자동 Payday
- 완료 확인형 Job
- Group/Whole Class 지급
- Undo/CSV
- 여러 교실 Balance 공유의 장단점

### [My Classroom Economy](my-classroom-economy.md)
**핵심 질문:** 디지털화 과정에서 학생에게 남겨야 할 ‘의미 있는 마찰’은 무엇인가?

주요 분석:
- 수기 bank ledger
- 급여/월세/경매
- 직업지원
- opportunity cost
- 물리적 출력물
- 월간 경제 루틴
- 학년말 회고
- 실제 좌석·필수권 상품화 위험

## 행동 피드백 서비스

### [ClassDojo](classdojo.md)
**핵심 질문:** 수업 흐름을 깨지 않고 교사가 즉시 기록하는 UX는 어떻게 만드는가?

주요 분석:
- 학생 타일
- Skill 기반 지급
- Group points
- Undo
- Reports
- Redeem/Reset
- 행동 포인트와 경제화폐를 분리해야 하는 이유

## 아동·청소년 금융 서비스

### [Greenlight](greenlight.md)
**핵심 질문:** 돈이 들어오는 순간부터 소비·저축·기부·목표로 어떻게 배분하게 하는가?

주요 분석:
- allowance
- pay per chore
- earning allocation
- savings goals
- withdrawal approval
- granular permissions
- parent-paid interest

### [NatWest Rooster Money](rooster-money.md)
**핵심 질문:** 정기 용돈과 추가소득을 어떻게 생활 루틴으로 만드는가?

주요 분석:
- allowance
- allowance chores
- extra earners
- partial payout
- Stars
- 연령별 과업
- 반복 지급 리듬

### [Revolut Kids & Teens](revolut-kids-teens.md)
**핵심 질문:** 연령과 위험도에 따라 아동 자율성과 보호자 승인을 어떻게 나누는가?

주요 분석:
- 자녀 전용 앱
- Challenges
- Goals
- Analytics
- 보호자 승인
- 연령별 기능
- co-parent 개념

### [토스 유스](toss-youth.md)
**핵심 질문:** 한국 어린이·청소년에게 돈의 상태와 소비 습관을 어떻게 단순하게 보여주는가?

주요 분석:
- 사용 가능 잔액
- 충전한 만큼 사용
- 용돈기입장
- 목표
- 보호자 기능
- 한도
- 친구 송금의 교실 적용 위험

## 개인 예산 서비스

### [YNAB](ynab.md)
**핵심 질문:** 학생이 ‘잔액’이 아니라 ‘돈의 목적’을 보게 만들 수 있는가?

주요 분석:
- Give every dollar a job
- Ready to Assign
- Categories
- Available
- Targets
- Underfunded
- Auto-Assign
- Reconcile

## 현재까지의 역할 분담

각 서비스를 하나의 순위로 평가하지 않는다.

- **ClassCoin**: 확장 범위의 상한
- **ClassBank**: 도입 순서와 학생 운영
- **Cashroom**: 거래 순간의 학습
- **Banqer**: 개념 중심 시뮬레이션
- **ClassCents**: 운영 마찰 최소화
- **My Classroom Economy**: 체험과 기록의 교육가치
- **ClassDojo**: 즉시 입력 UX
- **Greenlight**: 수입 배분과 목표저축
- **Rooster Money**: 반복 루틴과 과업
- **Revolut Kids & Teens**: 자율성/승인 경계
- **토스 유스**: 한국 청소년 금융 정보계층
- **YNAB**: 목적 기반 예산 사고

이 개별 분석이 완료된 뒤에만 Class Money의 통합 설계에서 어떤 조합을 선택할지 결정한다.
