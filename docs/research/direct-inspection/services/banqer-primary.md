# Banqer Primary 직접 관찰

기준일: 2026-11-08

## 직접 확인한 공개 자료
- Banqer Primary 공식 페이지/검색 노출
- https://primary.banqer.co/nz/help/the-class-store
- https://primary.banqer.co/nz/help/spending-what-students-can-buy-with-their-banqer-dollars

일부 how-it-works URL은 자동 fetch에서 403이 발생해 전체 페이지 본문 직접관찰은 제한됐다.

## Class Store에서 직접 확인한 Teacher/Student 분리
Teacher Dashboard:
- Class Store widget
- 기본 상태 Closed
- Store open으로 전환

Student Dashboard:
- store item browse
- Add to cart
- Go to checkout
- payment
- My Stuff

기능 existence와 현재 운영 state가 분리된다.

## 중요한 상태 모델
상점 모듈이 활성화돼 있어도 Closed / Open이라는 수업 운영상태를 갖는다.

Class Money에서 module enabled와 activity open을 별도로 모델링할 근거가 된다.

## Purchase와 Fulfillment
Banqer help의 Class Store 구조는 학생이 구매한 뒤 My Stuff에서 teacher item을 claim하는 패턴을 사용한다.

따라서 Purchase completed와 classroom privilege/item fulfilled는 다른 사건이다.

Class Money에서는 payment status와 fulfillment status를 분리해야 한다.

## Spending ideas에서 직접 확인한 범위
공식 help에는 tax, retirement/superannuation, charitable donation, in-class store 등 여러 돈 사용방식을 제안한다.

또 privilege reward 예시가 포함돼 있어 학습권/숙제/자리 등 기본권과 연결되는 보상은 별도 안전검토가 필요하다.

## 공개 GitHub 직접 감사
공식 GitHub organization Banqer를 직접 확인했다.

확인한 공개 repositories:
- Banqer/angular_sample — interview용 Angular sample, 2022 push
- Banqer/ui-select-banqer — Angular 1.5용 historical hard copy, 2016 push
- 기타 보조 repositories

현재 Banqer Primary 앱 본체 source라고 볼 수 없다.

따라서 현재 frontend stack을 이 repo들로 단정하지 않는다.

## Class Money에 가져올 것
- Module enabled와 Open/Closed 분리
- Teacher control surface / Student consumption surface 분리
- Purchase vs Fulfillment 분리
- 학습개념별 module
- 고급 금융기능은 단계적 activation

## 현재 미확인
- 실제 module activation navigation
- student home first fold
- learning resource 연결
- responsive layout
- 전체 product source