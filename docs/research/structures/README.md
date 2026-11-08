# 외부 검증 기반 서비스 구조도 Atlas

기준일: 2026-11-08

이 폴더는 서비스별 기능 목록이 아니라 공개적으로 검증 가능한 전체 제품 구조를 정리한다.

## 정확도 표기

- C — 공식 홈페이지/도움말/공개 가이드로 확인
- I — 확인된 여러 기능의 연결관계에서 합리적으로 추론한 외부 구조
- U — 로그인 후 화면 또는 비공개 내부 구현을 확인해야 함
- X — Class Money에 적용하기 위해 제안한 구조이며 원 서비스 구조가 아님

내부 DB, 서버 아키텍처, 비공개 API를 확인하지 않은 상태에서 실제 내부구조라고 단정하지 않는다.

## 각 구조도의 구성

1. Product Context — 서비스가 해결하는 문제와 외부 사용자
2. Actor / Permission Map — 누가 무엇을 하는가
3. Information Architecture — 메뉴·기능의 외부 구조
4. Domain Map — 공개 기능을 설명하기 위해 필요한 개념 객체
5. Money / Value Flow — 돈·포인트·보상의 생성, 이동, 회수
6. State Machine — 주문·직업·거래 등 주요 상태 변화
7. Automation — 자동급여·이자·청구 등 예약 처리
8. Learning Loop — 학생에게 남는 학습 단계
9. Failure / Recovery — 실제 운영에서 깨질 수 있는 지점
10. Unknowns — 공개자료로 확인 불가능한 부분

## 구조도 목록

- [ClassCoin](classcoin-structure.md)
- [ClassBank](classbank-structure.md)
- [Cashroom](cashroom-structure.md)
- [Banqer Primary](banqer-primary-structure.md)
- [ClassCents](classcents-structure.md)
- [My Classroom Economy](my-classroom-economy-structure.md)
- [ClassDojo](classdojo-structure.md)
- [Greenlight](greenlight-structure.md)
- [NatWest Rooster Money](rooster-money-structure.md)
- [Revolut Kids & Teens](revolut-kids-teens-structure.md)
- [토스 유스](toss-youth-structure.md)
- [YNAB](ynab-structure.md)

## 공통 관찰 프레임

교실경제 직접 경쟁군은 다음 흐름을 기준으로 비교한다.

Teacher Setup
→ Student Identity
→ Earn
→ Record/Confirm
→ Spend
→ Save
→ Recurring Rules
→ Review
→ Correct
→ Close Period

아동 금융/예산 앱은 다음 흐름을 기준으로 비교한다.

Income
→ Allocate
→ Available
→ Spend/Save
→ Goal
→ Review
→ Permission

## Craft Anything 후속 실측

현재 구조도는 공식 공개자료를 우선한 외부 시스템 모델이다.

Craft Anything Clean Room 또는 실제 접근권한이 있는 계정으로 화면을 측정한 뒤 C/I/U 상태를 갱신한다.

실측 증거:
- screenshot
- viewport
- visible menu
- click path
- state change
- error/recovery
- observed date

Craft Anything:
https://github.com/storytold/craft-anything
