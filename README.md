# Class Money — 교실 경제 체험 플랫폼

> 상태: **기획·벤치마킹 단계** (2026-11-08). 현재 구현 코드 없음. 이 저장소의 문서는 설계 제안이며 구현 완료를 의미하지 않습니다.

초등학교 교실에서 학생이 **일·소득·소비·저축·지출·선택·공동체 경제**를 체험하고 교사는 간단한 조작으로 학급 경제를 운영할 수 있게 하는 웹 앱을 기획합니다.

## 문서 안내
- [서비스 벤치마킹](docs/research/benchmark-2026-11.md): 공식 출처 기반 사례, 참고할 기능, 한계, 검증 상태.
- [심층 비교 분석 v2](docs/research/deep-analysis-2026-11.md): 확인된 사실/시사점/비도입 요소, 서비스별 교육·운영 분석.
- [서비스별 독립 심층 분석](docs/research/services/README.md): ClassCoin, ClassBank, Cashroom, Banqer, ClassCents, My Classroom Economy, ClassDojo, Greenlight, Rooster Money, Revolut Kids & Teens, 토스 유스, YNAB을 각각 별도 문서로 분석.
- [서비스별 기능 얽힘·UI·UX 분석](docs/research/services/ui-ux/README.md): 각 서비스가 복잡한 기능을 메뉴, 역할, 상태, 승인, 자동화, 오류복구 흐름으로 어떻게 풀어냈는지 별도 분석.
- [서비스별 Product Anatomy / Dossier](docs/research/services/dossiers/README.md): 역할·도메인 객체·기능 의존관계·플로우·상태·자동화·권한·복구까지 서비스 전체 구조를 해부.
- [복잡성 해소 패턴 종합](docs/research/synthesis/complexity-resolution-patterns.md): 여러 서비스에서 반복되는 UX/구조 패턴을 Class Money 설계 언어로 추출.
- [직접 사이트·리포지토리 관찰](docs/research/direct-inspection/README.md): 공개 사이트, 공식 Help/PDF, 공식 GitHub source를 실제로 열어 확인한 증거와 기존 설계 보정.
- [서비스별 UI·UX / 복잡성 해소 구조](docs/research/services/ux/README.md): 기능이 얽히는 방식, 정보구조, 화면 상태, 승인·오류복구, 모바일·공유기기 UX를 서비스별 독립 분석.
- [경제 엔진·정책](docs/product/economy-engine-and-policies.md): 경제 밸런스 계산, 거래 정책, 학생 공정성.
- [Economy Kernel v4](docs/architecture/economy-kernel-v4.md): 이중원장, account, hold, scheduler, reversal, 정책 버전 등 거래 커널 설계.
- [교사 운영 시스템 v4](docs/product/teacher-operations-v4.md): Teacher Inbox, 빠른 지급, 설정 마법사, 실패 복구, 학기 종료.
- [학생 학습 루프 v4](docs/product/student-learning-loop-v4.md): Earn→Plan→Decide→Predict→Act→Reflect의 학습 경험.
- [교실경제 위험 등록부 v4](docs/research/economic-risk-register-v4.md): 인플레이션, 격차, 낙인, 권리 상품화, 소셜·거래 위험.
- [실측 지표 v4](docs/research/benchmark-metrics-v4.md): Craft Anything/직접 실측을 위한 동일 시나리오와 증거 등급.
- [교사·학생 사용 시나리오](docs/product/teacher-student-journeys.md): 화면 플로우 및 실패/복구 시나리오.
- [평가표와 검증 계획](docs/research/verification-and-scorecard.md): 증거 수준, 실측 과제, 후속 사용성 검증.
- [제품 요구사항 및 학습 설계](docs/product/requirements.md): 역할, 흐름, 단계별 기능, 안전·공정성·접근성.
- [기술 설계 및 실행 계획](docs/architecture/implementation-plan.md): 데이터 모델, 원장/거래 안전성, 권한, 검증 시나리오.
- [Craft Anything 조사 프로토콜](docs/research/craft-anything-protocol.md): 실제 화면 증거 수집·비교를 위한 후속 조사 체크리스트.

## 설계 원칙
1. **교사 운영 부담 최소화**: 학생 일괄 등록, 급여 예약, 그룹 지급, 수정·취소, 이력 내려받기.
2. **학생의 선택과 이해**: 잔액을 보는 것만이 아닌 소득·필수 지출·소비·저축·목표 설정의 인과를 학습.
3. **단계적 공개**: 기본(지갑/직업/상점) → 금융(저축/세금/예산) → 확장(시장/창업/대출 등 선택).
4. **공정하고 안전한 참여**: 생활 필수권·학습권과 경제 보상을 분리, 학생 간 공개 자산 순위는 기본 비활성화.
5. **감사 가능한 거래**: 잔액 직접 덮어쓰기 대신 거래 원장 기록, 중복 지급 방지, 정정 이력 유지.
6. **독자 구현**: 타 서비스 디자인·상표·원본 코드·문구를 복제하지 않음.

## 벤치마킹 출처
[클래스코인](https://classcoin.me/) · [ClassBank](https://help.classbank.com/en/articles/5745347-classroom-economy-101) · [Cashroom](https://cashroomapp.com/) · [Banqer Primary](https://banqer.co/au/primary/how-it-works) · [ClassCents](https://www.classcents.com/) · [My Classroom Economy](https://myclassroomeconomy.org/) · [ClassDojo](https://www.classdojo.com/points/) · [Greenlight](https://help.greenlight.com/hc/en-us/articles/50527840580379-How-do-I-pay-my-child-per-chore-and-split-the-earnings)

**근거 범위**: 공개 홈페이지·공식 도움말·공식 기능 설명. 로그인이 필요한 실제 화면, 시스템 내부 구조, 성능은 미검증. 추정·제안은 사실과 구분합니다.
