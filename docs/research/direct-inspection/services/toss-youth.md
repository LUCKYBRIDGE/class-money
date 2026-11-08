# 토스 유스 직접 관찰

기준일: 2026-11-08

## 직접 연 페이지
- https://toss.im/service/teenagers
- redirect된 영어 공식 페이지

## 실제 설명 순서
Hero: Your first steps with money start here.

기능 서술:
1. Youth Card
2. Allowance Tracker
3. Goal Pot / Fan Pot
4. Money Study Café / Mock Investing
5. 친구 송금/메시지
6. 보호자/안전 기능

기능 목록보다 **사용 가능 → 회고 → 목표 → 학습 → 사회적 기능 → 안전**의 순서가 보인다.

## 사용가능액 경계
Youth Card는 Spend only what you top up이라는 문구로 복잡한 선불 결제 구조를 한 문장으로 압축한다.

Class Money 학생 홈도 총자산보다 지금 쓸 수 있는 돈과 저축/목표로 잠긴 돈을 구분해 설명하는 편이 좋다.

## Allowance Tracker
공식 페이지는 어디에 썼는지, 많이 쓴 날, 아낄 수 있는 지점을 보여준다고 설명한다.

거래내역을 단순 history에서 reflection layer로 바꾼다.

Class Money 학생 주간결산은 받은 돈 / 쓴 돈 / 모은 돈 / 가장 큰 선택 / 목표 변화가 적합하다.

## Goal Pot / Fan Pot
Goal Pot은 목표와 진행률, Fan Pot은 관심대상과 저축동기를 결합한다.

Class Money에서 fandom 자체는 필요 없지만 학생이 목표 이름/icon을 직접 정하게 하는 personalization은 유효하다.

## Learning과 Simulation
- Money Study Café: 짧은 금융 퀴즈
- Mock Investing Challenge: real money 전에 virtual investing

Class Money에서도 고급투자는 기본 원장과 분리한 Simulation Lab으로 두는 편이 안전하다.

## Guardian / Safety
공식 페이지는 allowance sending, lost-card report, support/protection을 별도 보호자 영역으로 설명한다.

정상 플로우뿐 아니라 문제 발생 후 복구 action을 제품 1급 기능으로 다룬다.

## 공개 GitHub 판정
이번 조사에서 토스 유스 제품 본체의 공식 public source repository는 확인하지 못했다.

## Class Money에 가져올 것
- 한국어 행동언어 중심 student IA
- Available balance first
- transaction → reflection
- personal goal
- simulation 분리
- teacher-only recovery action
- 과도하게 유아적이지 않은 금융 UI