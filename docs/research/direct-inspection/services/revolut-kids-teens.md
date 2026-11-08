# Revolut Kids & Teens 직접 관찰

기준일: 2026-11-08

## 직접 연 페이지
- https://www.revolut.com/revolut-kids-and-teens-parent-and-guardians/
- Kids & Teens Help index
- Managing Kids & Teens account
- Kids & Teens Earn
- Kids & Teens Save

국가별 제공기능 차이가 있어 특정 지역의 금융상품 수치보다 **권한·정보구조 패턴**만 분석한다.

## Parent / Child 제품 분리
공개 페이지에서 child own app/card, parent visibility, spending limits, card freeze, transaction notifications를 명확히 분리한다.

같은 제품의 메뉴를 role별로 disable하는 것보다 **서로 다른 shell**을 제공한다.

## Account hierarchy
공식 Help에서 Kids & Teens account는 parent personal account의 sub-account로 설명된다.

Co-parent는 top up과 monitor는 가능하지만 admin parent만 withdraw/close 등 핵심 owner action을 수행할 수 있다.

즉 관리자도 Owner와 Limited Co-manager로 구분한다.

## Challenges / Earn
공식 Help:
- parent가 challenge 생성
- child도 request 가능
- child request는 parent approval 필요
- one-time 또는 recurring
- daily / weekly / monthly

Task definition, request, approval, reward를 별도 단계로 둔다.

## Save / Pockets
Kids & Teens Save:
- parent 또는 child가 Pocket 생성/커스터마이즈
- main balance와 Pocket 분리
- Pocket은 direct card payment 불가
- child withdraw 가능
- recurring transfer 가능
- insufficient funds면 recurring transfer skip

이는 돈의 목적과 사용가능성을 구조적으로 분리하는 좋은 사례다.

## 공개 GitHub 판정
현재 Revolut 소비자 앱 본체 source를 공식 public repository로 확인하지 않았다.

## Class Money에 가져올 것
- TeacherShell / StudentShell 분리
- Owner teacher / co-teacher permission 차등
- Challenge request/approval
- Goal/Pocket을 spending balance와 분리
- insufficient funds에서 자동실행 실패를 명시
- 학년별 progressive autonomy

## 가져오지 않을 것
- 실제 card/payment
- real P2P
- 지역별 실제 금융상품 규칙