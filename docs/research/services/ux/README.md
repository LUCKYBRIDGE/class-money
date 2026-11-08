# 서비스별 UI·UX / 복잡성 해소 구조 분석

기준일: 2026-11-08

이 폴더는 각 앱·웹의 기능 목록이 아니라, **복잡하게 얽힌 기능을 사용자가 이해하고 처리할 수 있도록 어떤 구조로 풀었는가**를 분석한다.

## 공통 분석 프레임

각 서비스마다 다음을 분리해 기록한다.

1. 복잡성의 원천 — 어떤 기능·상태·권한이 서로 얽히는가
2. 해소 방식 — 단계형 노출, 역할분리, 공통 인터랙션, 자동화 등
3. 정보구조(IA) — 메뉴/탭/계층이 어떻게 구성되는가
4. 핵심 화면 — 홈, 목록, 상세, 승인, 거래, 설정
5. 상태 표현 — pending, approved, completed, rejected, refunded 등
6. 피드백 — 성공, 실패, 힌트, 되돌리기, 영수증
7. 권한 — 교사/학생/보조역할/보호자의 화면 차이
8. 반복업무 — 자동화와 일괄처리
9. 모바일/공유기기 — 작은 화면, 로그인, 전환
10. Class Money 적용 — 가져올 것, 변형할 것, 제외할 것
11. Craft Anything 후속 실측 — 실제 화면에서 검증할 항목

현재 문서는 공개 공식자료와 공개 화면을 근거로 한 구조 분석이다. 실제 클릭수·화면 치수·반응형 배치·키보드 접근성은 아직 동일 조건으로 실측하지 않았으며, 후속 Clean Room 관찰에서 보완한다.

## 교실경제

### [ClassCoin UI·UX](classcoin-ux.md)
핵심: 많은 학급경영·경제·게임 기능을 **분류·숨김·역할별 화면**으로 관리하는 방식.

### [ClassBank UI·UX](classbank-ux.md)
핵심: 복잡한 경제를 **Progressive Disclosure**로 단계적으로 도입하고 학생 보조역할을 기능권한에 연결하는 방식.

### [Cashroom UI·UX](cashroom-ux.md)
핵심: 다양한 금융기능을 **현재상태 → 변화 → 예측 → 기록**이라는 하나의 거래문법과 Pending 상태로 통일.

### [Banqer Primary UI·UX](banqer-primary-ux.md)
핵심: 기능을 메뉴가 아니라 **경제 개념 Expansion**으로 단계적으로 열고 수업자료와 문맥적으로 연결.

### [ClassCents UI·UX](classcents-ux.md)
핵심: 학생 로그인 없이도 돌아가는 **Teacher-first 저마찰 운영**, Earn/Spend/Save, Before/After 구매 UI.

### [My Classroom Economy UX](my-classroom-economy-ux.md)
핵심: 디지털 UI 이전에 복잡한 경제상태를 **역할·문서·물리적 절차**로 명시적으로 표현한 방식.

## 수업 중 빠른 입력

### [ClassDojo UI·UX](classdojo-ux.md)
핵심: 학생 타일 → Skill이라는 최소 인터랙션, Group 재사용, 빠른 Undo, 통합 알림.

## 아동·청소년 금융

### [Greenlight UI·UX](greenlight-ux.md)
핵심: 목표 카드, 돈 이동 출처/목적, 과업수입 배분, **기능별 Permission**.

### [Rooster Money UI·UX](rooster-money-ux.md)
핵심: Today/Overdue/Coming Up 상태, Approve/Re-open/Skip, bulk approval 등 **과업 루틴 UX**.

### [Revolut Kids & Teens UI·UX](revolut-kids-teens-ux.md)
핵심: 부모/아이 IA 분리, Pockets, Analytics, Challenges, **연령·위험도별 자율성**.

### [토스 유스 UI·UX](toss-youth-ux.md)
핵심: 한국 청소년에게 맞춘 **사용 가능액·최근 소비·목표 중심의 단순한 정보계층**.

## 예산/계획

### [YNAB UI·UX](ynab-ux.md)
핵심: Account와 Purpose를 분리하고 Ready to Assign, Available, Targets, Preview로 **돈의 목적을 중심에 두는 UX**.

## 서비스별로 발견한 대표적인 복잡성 해소 패턴

| 서비스 | 복잡하게 얽힌 문제 | 풀어낸 핵심 방식 |
|---|---|---|
| ClassCoin | 학급경영+경제+게임 | 분류, 메뉴 숨김, 역할별 화면 |
| ClassBank | 직업+청구+상점+저축+학생운영 | 단계형 노출, 역할별 권한 |
| Cashroom | 다수 금융거래+학습 | 공통 거래문법, Pending, 통합 Inbox |
| Banqer | 많은 금융개념 | Expansion, 학습 단계 |
| ClassCents | 대규모 학급 반복업무 | Teacher-first, 일괄처리, 자동 Payday |
| MCE | 종이 기반 복잡한 경제 | 문서와 역할로 상태 가시화 |
| ClassDojo | 수업 중 즉시 입력 | 타일, Skill, Group, Undo |
| Greenlight | 돈의 여러 목적+보호자 통제 | Goal, allocation, granular permission |
| Rooster | 반복 과업+용돈 | 시간상태, 승인상태, bulk |
| Revolut | 아동 자율성+보호자 감독 | 별도 IA, Pockets, 위험 기반 권한 |
| Toss | 여러 청소년 금융기능 | 큰 숫자, 최근 행동, 목표 중심 |
| YNAB | 계좌+예산+목표+거래 | 위치와 목적 분리, Preview, Available |

## Class Money에 통합할 UX 원칙

- **교사 화면은 기능 중심이 아니라 업무 중심**: 오늘 처리할 것, 빠른 지급, 이상 거래.
- **학생 화면은 메뉴 중심이 아니라 경제 행동 중심**: 벌기, 쓰기, 모으기, 확인하기.
- **설정은 단계적으로 공개**: 처음부터 세금·대출·투자를 보여주지 않음.
- **상태는 숨기지 않음**: 요청됨, 승인대기, 완료, 정정됨을 분명하게.
- **비활성 버튼에는 이유를 설명**: 잔액부족, 상점닫힘, 승인대기 등.
- **자동화 전 결과 미리보기**: 급여·세금·자동배분·정책변경.
- **일괄처리 + 예외처리**: 25명 전체를 빠르게 처리하되 특정 학생만 다르게 처리 가능.
- **Undo와 정정은 기본 기능**: 실수는 예외가 아니라 정상 운영 시나리오.
- **학생별 접근성/난도 지원**: 계산 단계 등은 개인별 조정 가능.
- **권한은 역할명이 아니라 행동 단위**: 지급, 승인, 상품편집, 거래조회 등을 각각 통제.
- **돈의 위치와 목적을 분리**: 지갑과 목표/예산은 다른 개념.
- **고급 시뮬레이션은 별도 공간**: 실제 학급경제 원장과 투자·시장 실험을 섞지 않음.
