# 앱별 파일·폴더·기술 구조 인덱스

기준일: 2026-11-08

이 폴더는 기능/UX 분석과 별도로 **각 서비스의 기술적 구성**만 정리한다.

## 정확도 등급

- **A — Exact source**: 공식 공개 repository의 실제 tree/file/source를 직접 확인.
- **B — Official partial source**: 공식 조직의 공개 source가 있으나 현재 제품 본체 전체는 아님.
- **C — Closed product**: 현재 제품 source는 비공개. 공개 사이트/Help에서 확인 가능한 외부 기술구조만 기록.
- **X — Proposed mapping**: Class Money 구현을 위해 제안한 구조. 원 서비스 내부구조가 아님.

## 원칙

1. 공개 source가 없으면 실제 폴더명·framework·DB를 만들어내지 않는다.
2. 공식 조직 repository라도 현재 제품 본체인지 README와 activity로 다시 판정한다.
3. 외부 동작으로 확인되는 것은 `외부 구조`, 내부 구현은 `미확인`으로 분리한다.
4. 기술 스택 추정은 제품 source 근거가 있을 때만 사용한다.
5. 서비스별 파일은 이후 실제 repository/source가 발견되면 A/B/C 등급을 갱신한다.

## 서비스

- [ClassCoin](classcoin.md) — C
- [ClassBank](classbank.md) — C
- [Cashroom](cashroom.md) — C
- [Banqer Primary](banqer-primary.md) — B
- [ClassCents](classcents.md) — C
- [My Classroom Economy](my-classroom-economy.md) — C / 문서시스템 중심
- [ClassDojo](classdojo.md) — B
- [Greenlight](greenlight.md) — C
- [NatWest Rooster Money](rooster-money.md) — C
- [Revolut Kids & Teens](revolut-kids-teens.md) — C
- [토스 유스](toss-youth.md) — C
- [YNAB](ynab.md) — A/B

## 분석 도구
- [Craft Anything](craft-anything.md) — A

## 우리 저장소
- [Class Money](class-money.md) — A

## 문서 공통 형식

각 앱별 문서에는 다음을 정리한다.
- Source 공개 여부
- 실제 확인된 repository / tree
- 확인된 파일·폴더
- 현재 제품과의 관련성
- 브라우저/앱/인증/역할/스케줄러 등 외부 기술 경계
- 확인된 기술 스택
- 확인 불가한 내부 구조
- Class Money에 대응시킬 기술 모듈