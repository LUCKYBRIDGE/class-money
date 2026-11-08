# 토스 유스 Product Anatomy

기준일: 2026-11-08  
범위: 토스 공식 어린이·청소년 서비스 페이지.  
목적: 한국 아동·청소년에게 복잡한 금융을 어떤 정보구조와 언어로 보여주는지 분석.

## 1. 제품 경계와 정체성

토스 유스는 실제 선불카드/충전/결제와 함께:
- 유스카드
- 용돈기입장
- 해냄 저금통
- 덕질 저금통
- 경제 학습
- 보호자 전용 기능
- 사기/분실 대응
을 제공하는 청소년 금융경험이다.

Class Money가 참고할 부분은 실제 금융 인프라가 아니라:
- 어린 사용자 전용 Home
- ‘쓸 수 있는 돈’ 경계
- 목표
- 소비 회고
- 보호자/자녀 역할 분리
다.

## 2. 사용자 역할

### Youth user
카드 잔액, 결제, 소비내역, 목표저축, 학습콘텐츠.

### Guardian
용돈 보내기, 카드 분실신고 등 관리.

### Support/Safety
고객센터, 안심보상, 카드 정지 등 문제복구.

Class Money의 교사/학생 관계와 완전히 같지는 않지만 **운영자와 아동 사용자의 정보 필요가 다르다**는 점은 동일하다.

## 3. 핵심 객체

- Youth user
- Guardian
- Card
- Balance
- Top-up
- Payment transaction
- Spending category
- Spending summary
- Savings goal
- Goal contribution
- Safety event
- Support action

## 4. 기능 구조

~~~mermaid
flowchart TD
  G[보호자] --> AL[용돈/충전]
  AL --> B[사용 가능 잔액]
  B --> PAY[결제]
  PAY --> LOG[용돈기입장]
  LOG --> REF[소비 회고]
  B --> GOAL[해냄/덕질 저금통]
  GOAL --> PROG[진행률/남은금액]
  G --> SAFE[분실/안전 관리]
  SAFE --> CARD[유스카드]
~~~

## 5. Youth-specific IA

토스 공식 소개는 어린 사용자에게:
- 카드
- 용돈기입장
- 저금통
- 경제 학습
같이 생활 행동 단위로 설명한다.

**핵심 UX**
성인 금융의 ‘예금계좌/자산배분/재무분석’ 언어보다:
- 쓰기
- 어디에 썼는지 보기
- 목표를 정해 모으기
처럼 행동 언어로 번역.

### D Class Money
저학년:
내 돈 / 일하기 / 모으기 / 쓰기.

고학년:
지갑 / 직업 / 저축 / 상점 / 기록.

## 6. 잔액 경계 — “충전한 만큼만”

공식 페이지는 유스카드가 ‘충전한 만큼만 쓸 수 있다’는 점을 명확하게 강조한다.

복잡한 선불 결제 구조를 사용자가 기억할 한 문장으로 압축한다.

### D Class Money
학생에게:
“지금 쓸 수 있는 돈만 상점에서 사용할 수 있어요.”
“저축에 넣은 돈은 사용 가능 금액에 포함되지 않아요.”

총자산보다 Available balance를 중심으로.

## 7. 용돈기입장

공식:
- 어디에 얼마나 썼는지 한눈에
- 평소보다 많이 쓴 날
- 아낄 수 있는 내역
- 소비습관 회고

**구조적 가치**
Transaction list를 단순 기록이 아니라 insight layer로 변환.

Class Money:
거래내역 → 주간 회고:
- 받은 돈
- 쓴 돈
- 모은 돈
- 가장 큰 지출
- 목표에 미친 영향.

단, ‘과소비’라고 자동 평가하지 않는다. 교실 상품가격은 인위적이기 때문.

## 8. 해냄 저금통

공식:
- 목표
- 모이는 금액
- 목표까지 남은 정도.

목표가 시각적으로 구체적.

### D Class Money
Goal card:
- 무엇을 위해
- 현재 / 목표
- 남은 금액
- 현재 계획 기준 예상기간
- 최근 넣은 돈.

## 9. 덕질 저금통

좋아하는 대상과 연결해 저축 동기를 만든다.

Class Money에 그대로 fandom 기능은 필요 없지만:
**goal personalization이 저축의 감정적 의미를 높인다**는 원리는 유용.

학생이 icon/image/title을 선택할 수 있게.

## 10. 보호자 전용 기능

공식:
- 용돈 보내기
- 카드 분실 신고
등이 보호자 전용.

**핵심**
관리 기능을 child UI에 섞지 않는다.

Class Money:
Teacher-only:
- PIN 재발급
- 전체 원장
- policy
- export
- student privacy.

Student:
자기 경제행동.

## 11. 안전/문제복구 UX

실제 금융제품에서는:
- 카드 분실
- 사기
- 문제 발생
후 사용자가 바로 할 수 있는 행동이 중요.

Class Money에도 이 사고방식 적용:
- 로그인코드 분실 → 재발급
- 모르는 거래 → 신고
- 주문 미처리 → 상태 확인
- 오지급 → teacher correction
- 세션 남음 → student switch/logout.

정상경로만 디자인하지 않는다.

## 12. 실제 투자/금융과 교육 시뮬레이션의 분리

토스는 실제 금융생활과 교육/모의 콘텐츠를 분리해 제공하는 맥락이 있다.

Class Money:
고급 시장 시뮬레이션이 있더라도 기본 wallet과 구별:
- 별도 시뮬레이션 계정
- 종료시 실제 class balance에 자동 영향 없음
을 기본으로 검토.

## 13. 정보 밀도와 톤

토스의 아동/청소년 서비스는 어린 사용자라고 해서 지나치게 유아적인 금융앱으로 만들기보다, 실제 금융경험 느낌을 유지하면서 설명과 범위를 단순화한다.

### D Class Money
- 1–2학년: icon과 짧은 문구 강화
- 5–6학년: 지나친 캐릭터화보다 실제 장부/예산 느낌
- 같은 기능이라도 density preset.

## 14. 복잡성을 풀어낸 방식

1. Youth-specific IA
2. 생활언어
3. Available balance 경계
4. transaction→reflection
5. goal personalization
6. guardian-only management
7. safety recovery surface
8. 실제금융과 학습콘텐츠 구분

## 15. Class Money에 가져올 것

**강하게**
- 학생 전용 Home
- Available 중심
- 주간 소비/저축 summary
- goal
- 역할별 UI 완전분리
- 쉬운 한국어
- 복구경로 노출

**신중**
- peer transfer
- social messaging

**제외**
- 실제 payment/card/bank connectivity.

## 16. Craft Anything 실측

정당한 접근범위에서:
- Youth Home first fold
- balance hierarchy
- transaction list/detail
- allowance ledger
- savings goal interaction
- guardian vs youth navigation
- safety action
- mobile one-hand primary actions
- typography/density by age.

## 17. 현재 판단

토스 유스는 Class Money의 경제엔진 참고보다 **한국 초등·청소년에게 돈 상태와 목표를 설명하는 화면언어**의 benchmark다.

## 공식 근거
- https://toss.im/service/teenagers
- https://toss.im/teens/uss-card
