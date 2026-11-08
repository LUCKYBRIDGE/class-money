# Cashroom 직접 관찰

기준일: 2026-11-08

## 직접 연 페이지
- https://cashroomapp.com/
- https://cashroomapp.com/help

## 홈페이지 first fold
Hero 문구는 Earn it. Save it. Do the math.

바로 아래 실제 Math Check 형태를 공개한다.
- Checking Pending
- Paycheck
- previous balance
- new balance input
- Record it

그리고 이 단계가 paycheck, purchase, fine, bill마다 반복된다고 명시한다.

즉 핵심 기능을 설명문보다 **실제 interaction grammar**로 보여준다.

## 공개 설명 순서
1. Earn
2. Pay bills
3. Spend
4. Save
5. Borrow

기능 메뉴가 아니라 학생의 경제 cycle로 설명한다.

## Help Center IA
상위 category:
- Signing in
- Money and the math check
- Jobs and paydays
- Store, coupons, auctions
- Credit and loans
- CDs, raffles, challenges
- Badges
- For teachers
- Privacy

## 공유기기 인증
직접 확인:
- starter code 1회
- 첫 로그인 후 새 password
- 5회 오류 → 15분 lock
- student session 3h
- teacher session 12h
- shared Chromebook을 이유로 session expiry 설명
- browser-only

교실 공용기기를 명시적으로 제품 요구사항에 포함한다.

## Pending 상태
- 가장 오래된 Pending부터 처리
- Pending이 남으면 store/coupon/bid 제한

Pending은 단순 알림이 아니라 다른 기능의 availability를 결정하는 핵심 상태다.

## 오류 학습 UX
Math Check 오답:
- 금전 penalty 없음
- retry
- 반복 오답 후 hint

학생의 계산실수를 경제적 처벌로 연결하지 않는다.

## 구매 불가 원인
Help에서 상태별로:
- pending
- below zero
- insufficient
- winning bid hold
- sold out
- store closed

Class Money에 매우 중요한 패턴: **disabled action에는 항상 reason이 있어야 한다.**

## Store/Cart
- checkout 전에는 charge 안 됨
- 오류가 있으면 어떤 것도 charge하지 않음
- logout하면 cart clear
- teacher가 item별 approve/deny
- deny item은 money/coupon 반환

부분승인/부분거절을 허용하는 주문모델이다.

## Auction
winning bid amount를 checking에서 hold하고 outbid/end까지 유지하며 win 시 capture한다.

이는 Class Money의 주문/경매에 Hold 계정이 필요한 직접 근거다.

## 공개 GitHub 판정
현재 Cashroom 제품 source 공식 public repository는 확인하지 못했다.

## Class Money에 가져올 것
- Pending 공통 거래상태
- Before → Change → Expected → Record
- disabled reason
- shared-device session
- Hold
- partial order approval
- 오류에 penalty 없는 학습지원
- teacher override/accommodation
- one inbox/bell

## 현재 미확인
- 로그인 후 dashboard 실제 화면 배치
- Bell priority
- student/teacher navigation
- mobile density
- keyboard/accessibility