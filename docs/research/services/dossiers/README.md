# 서비스별 Product Anatomy / Dossier

기준일: 2026-11-08

이 폴더는 단순 기능 목록이나 UI 스크린 분석을 넘어, 각 서비스를 **하나의 시스템으로 해부**한다.

## 분석 철학

Craft Anything의 Clean Room 접근처럼, 공개 화면·공식 문서·공개 도움말로 관찰 가능한 것과 내부 구현 추론을 분리한다.

- **E1 확인**: 공식 문서/공개 화면에서 직접 확인.
- **E2 관찰 필요**: 로그인 후 실제 화면에서 확인해야 함.
- **I 추론**: 공개 동작을 설명하기 위한 구조적 추론. 내부 구현 사실로 취급하지 않음.
- **D 제안**: Class Money에 적용하기 위한 설계 제안.

## 각 Dossier의 공통 구조

1. 제품 경계와 정체성
2. 사용자 역할
3. 핵심 데이터/도메인 객체
4. 기능 구조도
5. 정보구조(IA)
6. 역할별 홈/대시보드
7. 대표 작업 플로우
8. 상태 모델
9. 자동화/예약/주기
10. 권한·승인 모델
11. 거래/기록/정정
12. 복잡성을 풀어낸 UI·UX 패턴
13. 오류·예외·복구
14. 모바일/공유기기
15. 교육·행동 모델
16. 확장 시 복잡도
17. Class Money에 가져올 것
18. 가져오지 않을 것
19. 실제 Craft Anything 실측 항목
20. 공식 근거

## Dossier 목록

### 직접 교실경제
- [ClassCoin](classcoin.md)
- [ClassBank](classbank.md)
- [Cashroom](cashroom.md)
- [Banqer Primary](banqer-primary.md)
- [ClassCents](classcents.md)
- [My Classroom Economy](my-classroom-economy.md)

### 인접 서비스
- [ClassDojo](classdojo.md)
- [Greenlight](greenlight.md)
- [NatWest Rooster Money](rooster-money.md)
- [Revolut Kids & Teens](revolut-kids-teens.md)
- [토스 유스](toss-youth.md)
- [YNAB](ynab.md)

## 비교 원칙

서비스별 목적이 다르므로 단일 총점으로 서열화하지 않는다.

- ClassCoin: 확장성과 통합 학급운영
- ClassBank: 단계형 도입과 학생 운영권
- Cashroom: 거래 순간의 학습
- Banqer: 금융개념 시뮬레이션
- ClassCents: 교사 업무 마찰 최소화
- My Classroom Economy: 체험·기록·물리적 절차
- ClassDojo: 초고빈도 입력 UX
- Greenlight: 수입 배분·목표·권한
- Rooster Money: 정기 루틴·과업
- Revolut Kids & Teens: 연령/위험 기반 자율성
- 토스 유스: 한국 아동·청소년 금융 정보구조
- YNAB: 목적 기반 예산 추상화

## Craft Anything 활용 방향

Craft Anything 공식 README 기준 Clean Room은 웹사이트 방문자가 볼 수 있는 스크린샷·가시 텍스트·레이아웃·메뉴 상태·반응형 폭 등을 수집하고 내부 코드/파일을 읽지 않는다. 다만 2026-11-04 STATUS에는 **실제 Clean Room build 전체 흐름은 아직 live 검증이 충분하지 않다**고 명시되어 있으므로, 이 저장소에서는 Craft Anything을 ‘증거 수집 프레임’으로 사용하되 실제 실측을 수행하지 않은 항목을 완료로 기록하지 않는다.

- https://github.com/storytold/craft-anything
- https://github.com/storytold/craft-anything/blob/main/docs/STATUS.md
