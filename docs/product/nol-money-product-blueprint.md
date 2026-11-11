# 놀머니 제품 아이디어 및 설계 청사진

기준일: 2026-11-11  
상태: 구현 전 제품 아이디어 / 독자 설계

---

## 1. 제품 한 문장

**놀머니는 초등학생이 교실 안에서 돈을 벌고, 계획하고, 쓰고, 모으고, 투자하고, 경제사건을 경험하며 선택의 결과를 돌아보는 경제 시뮬레이션 플랫폼이다.**

단순 학급화폐 앱도 아니고, 주식게임도 아니다.

핵심은:

> **경제 개념을 설명하는 대신 반복해서 경험하게 만드는 것.**

---

## 2. 제품이 가르쳐야 할 경제 개념

### 기본 경제
- 노동과 보상
- 소득
- 소비
- 저축
- 목표
- 선택
- 기회비용
- 예산

### 시장
- 수요와 공급
- 가격 변화
- 경쟁
- 재고
- 희소성

### 금융
- 이자
- 예금
- 환율
- 통화
- 위험과 수익
- 분산

### 공공경제
- 세금
- 국고
- 공동체 지출
- 공공재
- 기부

### 기업/투자
- 기업이 하는 일
- 매출/비용
- 산업
- 원재료
- 수출입
- 금리
- 환율
- 경기
- 기업사건
- 투자판단

---

## 3. 제품 전체 구조

```text
놀머니
│
├─ 1. 나의 경제
│  ├─ 사용 가능 돈
│  ├─ 저축
│  ├─ 목표
│  ├─ 최근 거래
│  └─ 주간 회고
│
├─ 2. 직업과 과업
│  ├─ 기본 참여
│  ├─ 정기 직업
│  ├─ 추가 과업
│  └─ 급여
│
├─ 3. 상점
│  ├─ 상품
│  ├─ 구매 요청
│  ├─ 승인
│  └─ 사용/수령
│
├─ 4. 경제 배우기
│  ├─ 저축/이자
│  ├─ 세금/국고
│  ├─ 예산
│  ├─ 환율
│  └─ 시장
│
└─ 5. 경제 실험실
   ├─ 실제 시장 모드
   │  ├─ 한국 주식
   │  ├─ 미국 주식
   │  └─ 환전
   │
   └─ 시나리오 모드
      ├─ 가상시장
      ├─ 가상기업
      ├─ 경제사건
      ├─ 학생 판단
      └─ 결과·해설·회고
```

---

## 4. 가장 중요한 제품 분리

## 4.1 Core Economy
교실에서 매일 쓰는 경제.

- 직업
- 급여
- 지갑
- 저축
- 상점
- 목표
- 세금/국고

이 영역은 매우 안정적이어야 한다.

## 4.2 Simulation Lab
경제 개념을 의도적으로 경험하는 별도 공간.

- 실제시장
- 가상시장
- 환율
- 기업사건
- 수요/공급
- 금리
- 경기
- 정책

**Simulation Lab 장애가 Core Economy를 멈추면 안 된다.**

---

## 5. 실제 시장 모드

목적:
실제 기업과 시장을 관찰하고 현실 금융의 구조를 경험.

### 시장
- 🇰🇷 한국
- 🇺🇸 미국

### 기능
- 종목 탐색
- 기업 정보
- 가격
- 포트폴리오
- 매수/매도
- KRW/USD 환전
- 매매일지
- 수익률
- 위험/분산 확인

### 교육적 제한
- 실제 돈 사용 없음
- 학생간 실제 송금 없음
- 과도한 레버리지 없음
- 파생상품 없음
- 단순 수익률 공개랭킹 기본 OFF

### 시세 표시
항상:
- 마지막 업데이트 시각
- 실제/지연 여부
- 시장 Open/Closed
를 표시.

---

## 6. 시나리오 모드

제품 내부/교사용 명칭은 **시나리오 모드**가 적합하다.

학생 화면 명칭 후보:
- 경제 실험실
- 시장 미션
- 가상시장
- 경제 시뮬레이션

### 역할

실제 시장에서는 수업시간에 원하는 경제현상이 발생하지 않을 수 있다.

시나리오 모드는:
- 특정 경제원리를
- 의도적으로
- 반복 가능하게
- 여러 변형으로
경험시키는 기능이다.

---

## 7. 시나리오 학습루프

```text
시나리오 시작
→ 기업/산업 조사
→ 초기 포트폴리오
→ 사건 발생
→ 생각할 시간
→ 매수 / 매도 / 유지
→ 시장 반응
→ 후속 사건
→ 결과
→ 매매일지
→ 학급 토론
→ 경제원리 해설
```

핵심은 가격이 아니라:

> 사건 → 판단 → 결과 → 설명

이다.

---

## 8. 완전 랜덤이 아니라 통제된 랜덤

잘못된 방식:

```text
Random()
→ 아무 주식이나 +20%
```

권장:

```text
학습목표
→ Scenario Pool
→ Event Graph
→ 조건부 Random
→ Company Sensitivity
→ Price Response
→ Debrief
```

예:

```text
시나리오: 원유가격 상승

Event 후보
├─ 산유국 감산
├─ 국제분쟁
├─ 예상보다 빠른 공급회복
└─ 정부 유류세 완화
```

매번 조금씩 다른 결과가 나오되 경제적 인과관계는 유지한다.

---

## 9. 가상시장과 가상기업

현실 기업의 패러디 이름을 쓰지 않는다.

예:
- 삼썽전자
- 애플리
- NVIDA

같은 방식은 피한다.

### 별도 세계관

가상시장 이름 예:
- 놀마켓
- NSE — Nol Simulation Exchange
- 놀경제시장

항상 표시:

> 이 시장의 기업과 가격은 학습용 가상 정보입니다. 실제 기업·주식시장과 관련이 없습니다.

### 가상기업 예

| 산업 | 가상기업 | 코드 |
|---|---|---|
| 반도체 | 별빛반도체 | NSE-BST |
| 항공 | 하늘길항공 | NSE-SKY |
| 자동차 | 미래모터스 | NSE-MTR |
| 전기차 | 푸른바퀴 | NSE-GRW |
| 배터리 | 에너지셀 | NSE-ECL |
| 에너지 | 한빛에너지 | NSE-HBE |
| 태양광 | 햇살에너지 | NSE-SUN |
| 유통 | 모두마켓 | NSE-MKT |
| 식품 | 맛나푸드 | NSE-FOD |
| 바이오 | 새봄바이오 | NSE-BIO |
| AI | 넥스트AI | NSE-NAI |
| 물류 | 빠른길물류 | NSE-QLG |
| 건설 | 튼튼건설 | NSE-BLD |
| 여행 | 두루여행 | NSE-TRV |
| 로봇 | 로보웨이 | NSE-RBW |

이름만 보고 산업을 어느 정도 추론할 수 있지만 실제 상장사와 직접 연결되지는 않게 한다.

---

## 10. 가상기업 데이터 모델

```text
VirtualCompany
├─ id
├─ name
├─ ticker
├─ sector
├─ description
├─ size
├─ debtLevel
├─ exportRatio
├─ importRatio
├─ oilSensitivity
├─ interestSensitivity
├─ fxSensitivity
├─ consumerDemandSensitivity
├─ technologySensitivity
├─ policySensitivity
├─ volatility
└─ tags[]
```

학생에게는 모든 숫자를 그대로 보여주지 않는다.

학생용 자연어:
- 해외 판매가 많아요
- 빚이 조금 많아요
- 원유 가격 영향을 많이 받아요
- 신기술 연구에 돈을 많이 써요

고학년:
- 해외매출 ★★★★☆
- 부채 ★★☆☆☆
- 환율 영향 ★★★★☆
같은 요약 추가 가능.

---

## 11. 시나리오 데이터 모델

```text
Scenario
├─ id
├─ title
├─ learningObjective
├─ difficulty
├─ targetGrade
├─ duration
├─ startingConditions
├─ companyPool[]
├─ eventPool[]
├─ endingConditions
└─ debrief
```

### Event

```text
ScenarioEvent
├─ id
├─ headline
├─ description
├─ type
├─ probability
├─ prerequisites
├─ effects[]
├─ followUpEvents[]
├─ studentPrompt
└─ explanation
```

### Effect

```text
Effect
├─ targetType
├─ targetId / tag
├─ strength
├─ range
├─ delay
└─ duration
```

---

## 12. 시나리오 가격엔진

기업별 고정 가격변화만 입력하면 시나리오 수가 늘수록 관리가 어렵다.

권장:

```text
Event Factor
× Company Sensitivity
× Market Noise
× Previous State
= Price Impact
```

예:

원유 상승:
- oil factor +0.8

하늘길항공:
- oilSensitivity -0.9

한빛에너지:
- oilSensitivity +0.6

결과:
- 항공 ↓
- 에너지 ↑

단, 작은 random range를 넣어 결과 암기를 방지.

---

## 13. 초기 시나리오 주제

### Level 1 — 직접 영향
- 폭염
- 한파
- 여행객 증가
- 신제품 인기
- 제품 리콜
- 농작물 풍년/흉년

학습:
수요·공급·기업매출.

### Level 2 — 연쇄 영향
- 원유가격 상승
- 환율 급등
- 반도체 부족
- 항구 파업
- 자연재해
- 전기요금 상승
- 관광경기 변화

학습:
산업 연결·비용·수출입.

### Level 3 — 복합 경제
- 금리 상승
- 금리 인하
- 경기침체
- 경기회복
- 인플레이션
- 정부 보조금
- 친환경 규제
- 무역갈등

학습:
여러 요인의 동시 영향.

---

## 14. 학생용 시나리오 UI

```text
경제 실험실

[📢 현재 사건]
[📈 가상시장]
[💼 내 포트폴리오]
[📝 내 판단]
[📰 지난 뉴스]
[📚 경제 해설]
```

### 사건 카드

> 국제 원유 가격이 크게 올랐습니다.

학생에게 바로 가격결과를 보여주지 않고 먼저:

> 어떤 기업이 영향을 받을까요?

를 묻는다.

### 판단 기록

선택:
- 산다
- 판다
- 유지한다

이유:
- 직접입력
- 이유 카드 선택
- 둘 다 가능

---

## 15. 실제시장 UI와 시나리오 UI는 명확히 구분

```text
📈 시장

실제 시장
├─ 🇰🇷 한국
├─ 🇺🇸 미국
└─ 💱 환전

경제 실험실
└─ 🧪 가상시장
```

가상시장에서는 모든 화면 상단에:
- 가상시장
- 학습용
표시 유지.

색상만으로 구분하지 않고 text/badge/icon을 모두 사용.

---

## 16. 학생 Home

가장 크게:

> 사용 가능

그 다음:
- 저축
- 목표
- 최근 거래
- 다음 급여
- 오늘의 역할
- 오늘 열린 경제활동

총자산은 secondary.

### 학생 mental model

```text
벌기
→ 계획하기
→ 쓰기/모으기
→ 경험하기
→ 돌아보기
```

---

## 17. 교사 Home

통계보다 Action Queue 우선.

### 오늘 처리
- 구매 승인
- 과업 승인
- 직업지원
- 실패한 자동급여
- 시나리오 수업 예정

### 빠른 지급
- 최근 학생
- 최근 사유
- 최근 금액

### 예정
- Payday
- 세금
- 시장 Simulation

### 경제 건강
- 유통량
- 저축률
- 대표상품 달성기간
- 직업 미배정

---

## 18. 교사 시나리오 Dashboard

교사가 수업 중 보고 싶은 것:

- 현재 Event
- 학생별/학급별 선택
- 많이 산 기업
- 많이 판 기업
- 유지 선택 비율
- 학생 판단 이유
- 산업별 포트폴리오
- 위험집중도
- 수익률 분포

질문 자동 제안:

> 왜 많은 학생이 하늘길항공을 팔았을까요?

> 별빛반도체와 미래모터스가 같은 뉴스에 다르게 움직인 이유는 무엇일까요?

---

## 19. 랭킹 정책

개인 자산/수익률 순위는 기본 OFF.

시나리오 결과는 다음처럼 분리.

```text
시장 결과
- 수익률 +8.4%

학습 결과
- 판단근거 4/5
- 분산투자 양호
- 위험관리 우수
- 경제개념 이해 3/4
```

수익률이 높다고 학습성공으로 간주하지 않는다.

---

## 20. 직업·과업·소득 구조

학생소득을 세 종류로 분리.

### 기본 참여소득
직업 미배정 학생도 경제활동에 참여 가능한 최소소득.

### 정기 직업급여
직업 수행에 따른 주기급여.

### 추가 과업보수
선택형 추가 task.

공동체 기본책임까지 전부 돈으로 환산하지 않는다.

---

## 21. 상점 구조

```text
Browse
→ Request
→ Hold/Check
→ Teacher Approval
→ Payment
→ Fulfillment
→ Used/Completed
```

구매와 실제 교실 보상 제공을 분리.

상태:
- CLOSED
- OPEN
- REQUESTED
- APPROVED
- REJECTED
- FULFILLED
- REFUNDED

---

## 22. Teacher-only fallback

학생 기기가 없어도 경제가 운영돼야 한다.

교사는 학생 대신:
- 지급
- 저축 이동
- 구매 처리
- task 승인
가능.

모든 대리행동은 audit에:
- actor=teacher
- onBehalfOf=student
를 남긴다.

---

## 23. Shared-device mode

학교 태블릿/공용PC를 1급 요구사항으로 본다.

학생 전환:
- 로그아웃보다 빠른 “학생 바꾸기”
- 이전 학생 잔액/거래 화면 즉시 masking
- short code / QR
- 일정시간 자동종료

---

## 24. 놀머니 핵심 기술 도메인

```text
domain/
├─ classrooms/
├─ identities/
├─ groups/
├─ accounts/
├─ ledger/
├─ allocations/
├─ goals/
├─ jobs/
├─ tasks/
├─ payroll/
├─ store/
├─ orders/
├─ holds/
├─ schedules/
├─ taxes/
├─ treasury/
├─ permissions/
├─ audit/
└─ simulation/
   ├─ real-market/
   ├─ virtual-market/
   ├─ quotes/
   ├─ fx/
   ├─ companies/
   ├─ scenarios/
   ├─ events/
   ├─ portfolios/
   └─ journals/
```

---

## 25. 권장 source tree

구현 전 제안:

```text
apps/
├─ teacher-web/
├─ student-web/
└─ shared-kiosk/

packages/
├─ domain/
├─ ui/
├─ validation/
├─ simulation-engine/
└─ shared-types/

server/
├─ api/
├─ application/
├─ domain/
├─ persistence/
├─ jobs/
├─ market-data/
└─ audit/

tests/
├─ domain/
├─ integration/
├─ e2e/
├─ fixtures/
└─ simulation/

docs/
├─ adr/
├─ product/
├─ architecture/
└─ research/
```

---

## 26. Economy Kernel

반드시 구현 전에 고정해야 할 것:

### Ledger
모든 돈 이동의 원장.

### Idempotency
중복지급/중복주문 방지.

### Reversal
삭제 없는 정정.

### Hold
주문/경매/시장예약.

### Scheduler
급여/이자/세금.

### Policy Version
과거 거래의 설명가능성.

### Classroom Isolation
학급별 경제 분리.

---

## 27. Simulation Engine은 Core와 분리

```text
Core Economy
↕ adapter
Simulation Lab
↕ provider
Actual Market Data
```

시장 provider 장애가:
- 학생 지갑
- 상점
- 급여
를 멈추면 안 된다.

가상시장도 Core balance와 별도 simulation account를 기본으로 권장.

---

## 28. 실제시장 기술 주의

실제 시세 기능에는 최소:
- quote provider
- last updated
- market status
- symbol universe
- currency
- FX rate snapshot
- stale data handling
가 필요하다.

미국시장:
- 시차
- 휴장
- 장전/장후
문제를 학생에게 단순화해 설명해야 한다.

---

## 29. 학습설계

학생 핵심 루프:

```text
EARN
→ PLAN
→ DECIDE
→ PREDICT
→ ACT
→ REFLECT
```

시나리오 학습 루프:

```text
OBSERVE
→ HYPOTHESIZE
→ CHOOSE
→ EXPERIENCE
→ EXPLAIN
→ REFLECT
```

---

## 30. 학년별 복잡도

### 1~2
- 벌기
- 쓰기
- 모으기
- 목표 하나

### 3~4
- 직업
- 가격비교
- 저축
- 간단 수요/공급

### 5~6
- 예산
- 세금
- 이자
- 환율
- 실제시장 관찰
- 시나리오시장
- 산업연결

---

## 31. MVP

고급기능보다 먼저 검증할 것.

### Teacher
- 반 만들기
- 학생 25명 붙여넣기
- 빠른 지급
- 자동급여
- 승인함
- 오지급 Undo
- 상점

### Student
- QR/short code
- 사용 가능 돈
- 최근내역
- 직업
- 목표
- 상점

### Kernel
- Ledger
- Reversal
- Idempotency
- Schedule

이게 안정되기 전 실제주식 기능을 핵심제품으로 만들지 않는다.

---

## 32. 이후 단계

### V1
- Savings
- Goal
- Interest
- Budget
- Weekly Reflection

### V2
- Tax/Treasury
- Public Spending
- Basic Scenario Mode

### V3
- Full Scenario Engine
- Virtual Companies
- KR/US Actual Market
- FX
- Teacher Market Dashboard

---

## 33. 제품 성공 기준

놀머니가 성공했다는 것은:

- 학생 잔액이 많아졌다는 뜻이 아니다.
- 거래량이 많다는 뜻도 아니다.

학생이 다음에 답할 수 있어야 한다.

- 이 돈은 어디서 왔는가?
- 지금 얼마를 쓸 수 있는가?
- 무엇을 위해 모으고 있는가?
- 지금 사면 무엇을 포기하는가?
- 왜 이 기업을 선택했는가?
- 어떤 사건이 기업에 영향을 주었는가?
- 결과가 예상과 달랐던 이유는 무엇인가?
- 다음에는 어떤 선택을 바꿀 것인가?

교사는:
- 25명 학급을 과도한 반복작업 없이 운영할 수 있어야 한다.
- 실수했을 때 즉시 복구할 수 있어야 한다.
- 시나리오 수업을 45분 안에 시작·진행·회고할 수 있어야 한다.

---

## 34. 최종 방향

놀머니는 다음 세 제품의 결합으로 보는 것이 적합하다.

```text
1. 교실 경제 운영도구
+
2. 학생 금융학습 도구
+
3. 경제 Simulation Lab
```

세 영역은 연결되지만 서로의 복잡성을 강제로 전파하지 않는다.

가장 중요한 설계 원칙:

> **교사에게는 복잡성을 숨기고, 학생에게는 배워야 할 경제적 복잡성만 남긴다.**
