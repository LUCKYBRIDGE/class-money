# Cashroom — 복잡성·정보구조·UI·UX 심층 분석

기준일: 2026-11-08  
증거 수준: 공식 공개 홈페이지와 Help에서 학생/교사 흐름 확인. 로그인 후 시각적 정밀 실측 전.

## 1. 복잡성의 원천
jobs, paydays, bills, store, coupons, auctions, savings, interest, loans, credit, CDs, badges 등이 연결된다. 보통 이런 구조는 메뉴와 상태가 폭발하기 쉽다.

## 2. 핵심 해법: 공통 거래문법
공개 메인 예시는 모든 기능을 하나의 반복 패턴으로 단순화한다.

현재 잔액 → 들어오거나 나갈 금액 → 새 잔액 예측 → Record

급여, 구매, 벌금, 청구가 서로 다른 기능이어도 학생이 학습하는 인터랙션은 비슷하다.

Class Money는 이를 현재 → 변화 → 예상 → 확정 → 이유의 공통 거래문법으로 일반화할 수 있다.

## 3. Pending 상태로 복잡성을 노출
Cashroom은 자동 발생한 거래를 바로 끝내지 않고 Pending으로 둔다. 가장 오래된 Pending부터 기록해야 하고 Pending이 있으면 상점·쿠폰·경매가 잠긴다.

좋은 점:
- 처리 안 된 상태가 숨겨지지 않음.
- 학생이 해야 할 다음 행동이 분명함.
- 경제 상태와 학습과제를 하나로 연결.

Class Money는 내부 상태를 더 다양하게 가져가되 학생에게는 확인 필요 / 완료 / 취소처럼 단순하게 보여주는 편이 좋다.

## 4. 오류 피드백
공식 Help에서 계산 오답은 손해로 이어지지 않는다. 두 번 틀리면 힌트를 제공한다.

이 패턴은 교육용 UX에 적합하다.
실수 → 처벌이 아니라 실수 → 피드백 → 재시도.

## 5. 교사 복잡성 해소
- 자동 Payday/Bills
- 한 개의 bell에 job applications, loan requests, store orders, below-zero alerts 등을 통합
- 학생별 Math Check 예외
- History와 Undo
- CSV export

핵심 원리:
설정은 기능별, 운영은 통합 Inbox.

## 6. 상점 상태 UX
학생이 구매했는데 아직 받지 못한 상태를 주문 승인 대기로 분리한다. 거절되면 돈과 쿠폰이 돌아온다.

또한 구매가 막힌 이유를 명시적으로 설명한다:
- Pending 존재
- 음수 잔액
- 잔액 부족
- 입찰 hold
- 품절
- 상점 닫힘

Class Money도 비활성 버튼만 보여주지 말고 왜 안 되는지 바로 설명해야 한다.

## 7. 경매의 Hold UX
최고입찰 금액은 checking에서 hold된다. 다른 사람이 더 높게 입찰하면 hold가 해제된다.

Class Money의 주문/경매/예약 기능에서 사용 가능 잔액과 예약 금액을 분리해야 하는 근거가 된다.

## 8. 계정/공유기기 UX
- starter code는 1회 사용 후 개인 비밀번호 생성.
- 5회 실패 후 잠금.
- 학생 3시간, 교사 12시간 후 자동 로그아웃.
- 교사가 새 starter code를 발급 가능.

교실의 공유 Chromebook 환경을 실제 사용 시나리오로 다룬다.

## 9. UX 위험
- 모든 거래의 계산 확인이 누적 피로를 만들 수 있음.
- 중학생 기준 금융용어가 초등에게 어려움.
- 기능이 많아지면 Home이 복잡해질 가능성.
- credit score가 학생 평가처럼 인식될 위험.

## 10. Class Money 적용
강하게 채택:
- 공통 거래문법
- Pending
- 이유가 있는 비활성 상태
- 통합 Inbox
- 학생별 난도
- 영수증
- 공유기기 자동 로그아웃
- Hold
- 도메인별 Undo

초등용 표현:
Checking → 쓸 수 있는 돈  
Savings → 모아둔 돈  
Credit → 초기 미노출

## 11. Craft Anything 실측 항목
- 거래 카드의 실제 시각계층
- 오답/힌트 표현
- 여러 Pending이 있을 때 화면
- Bell의 유형 구분
- 주문 거절과 환불 표시
- Hold 금액 가시성
- 폰 숫자 입력 UX
- 공유기기 로그인/로그아웃
- Undo 후 기록 표현

## 공식 근거
- https://cashroomapp.com/
- https://cashroomapp.com/help
- https://cashroomapp.com/getting-started
