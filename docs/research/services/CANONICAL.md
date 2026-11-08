# 서비스별 Canonical Product Folders

기준일: 2026-11-08

이 디렉터리의 서비스별 하위폴더를 앞으로 **최신 정본**으로 사용한다.

- [ClassCoin](classcoin/README.md) — 국내 학급경영 + 교실경제 + 게임화
- [ClassBank](classbank/README.md) — 학급은행 + 금융문해력 + 학생 운영권
- [Cashroom](cashroom/README.md) — 거래 순간 수학 + 교실경제
- [Banqer Primary](banqer-primary/README.md) — 개념별 금융 시뮬레이션
- [ClassCents](classcents/README.md) — 교사 운영마찰 최소화형 교실경제
- [My Classroom Economy](my-classroom-economy/README.md) — 종이·역할 기반 교실경제 프로토콜
- [ClassDojo](classdojo/README.md) — 초고빈도 교실 피드백 UX
- [Greenlight](greenlight/README.md) — 아동 돈 배분·목표·권한
- [NatWest Rooster Money](rooster-money/README.md) — 정기 용돈·과업 루틴
- [Revolut Kids & Teens](revolut-kids-teens/README.md) — 아동 자율성·보호자 승인
- [토스 유스](toss-youth/README.md) — 한국 아동·청소년 금융 정보구조
- [YNAB](ynab/README.md) — 목적 기반 예산·거래 모델

각 폴더 공통 구조:

```text
service/
├─ README.md
├─ 01-pages-navigation.md
├─ 02-ui-ux-controls.md
├─ 03-features-flows.md
├─ 04-technical-structure.md
├─ 05-complexity-solutions.md
└─ 06-evidence-unknowns.md
```

기존의 flat 문서, dossiers, ui-ux, structures, direct-inspection 문서는 삭제하지 않는다. 새 폴더가 **탐색 시작점**, 기존 문서는 세부 증거·과거 분석 보존용으로 사용한다.
