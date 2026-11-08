# ClassCoin 외부 구조도

검증 범위: 공식 홈페이지·사용 가이드·공개 업데이트  
구조 성격: 국내 학급경영 + 교실경제 + 게임화 통합 플랫폼

## 1. Product Context

C:
- 교사와 학생이 하나의 학급 공간을 공유
- 학급화폐가 직업·퀘스트·상점·저축·세금·자산·시장·게임과 연결
- 교사용 가이드와 학생용 가이드가 분리

~~~mermaid
flowchart LR
  T[교사] --> C[ClassCoin 학급]
  S[학생] --> C
  C --> E[학급경제]
  C --> M[학급관리]
  C --> G[게임/동기]
  C --> L[학습/퀴즈]
  E --> W[학급화폐]
  E --> TR[국고]
  G --> AC[별도 활동재화 가능]
~~~

## 2. 외부 IA

공식 가이드에서 확인되는 최상위 기능군.

~~~text
ClassCoin
├─ 시작하기
├─ 점수판
├─ 학생 관리
├─ 퀘스트
├─ 루틴
├─ 직업
├─ 아이템 상점
├─ 행운 상자 / 수집품
├─ 경제 시스템
├─ 학급 온도계
├─ 자리배치
├─ 공지사항
├─ 대시보드
├─ 팜타이쿤
├─ 펫
├─ 마켓플레이스
├─ 퀴즈
├─ 브레인런
├─ 미션 보드
├─ 감사 카드
├─ 대출
├─ 쪽지
└─ 설정
~~~

상태: C.

## 3. 기능을 경제도메인으로 재분류

~~~mermaid
flowchart TD
  IN[화폐 유입]
  HOLD[보관/증식]
  OUT[화폐 회수]
  MARKET[학생시장]
  PUBLIC[공공경제]
  CREDIT[신용경제]
  GAME[게임경제]

  IN --> A1[점수판]
  IN --> A2[직업급여]
  IN --> A3[퀘스트/루틴]
  IN --> A4[퀴즈/미션 보상]

  HOLD --> B1[현금/가계부]
  HOLD --> B2[저축/예금]
  HOLD --> B3[이자]

  OUT --> C1[아이템 상점]
  OUT --> C2[세금]
  OUT --> C3[게임 소비]

  MARKET --> D1[창업/상점]
  MARKET --> D2[마켓플레이스]
  MARKET --> D3[부동산/임대]
  MARKET --> D4[경매]

  PUBLIC --> E1[세금]
  PUBLIC --> E2[국고]
  PUBLIC --> E3[정기지출]
  PUBLIC --> E4[기부/온도계]

  CREDIT --> F1[대출]
  CREDIT --> F2[신용]

  GAME --> G1[펫]
  GAME --> G2[수집품]
  GAME --> G3[행운상자]
  GAME --> G4[팜타이쿤]
~~~

기능 존재는 C. 내부 데이터 연결은 I.

## 4. Actor / Permission 구조

~~~mermaid
flowchart TD
  Teacher[교사]
  Student[학생]
  Public[프로젝터/학급공개]
  Helper[학생 운영역할 가능 영역]

  Teacher --> Setup[학급/경제 규칙 설정]
  Teacher --> Award[지급/회수]
  Teacher --> Manage[직업·상점·세금·자산 관리]
  Teacher --> Moderate[가게/후기/소통 관리]

  Student --> Wallet[본인 경제]
  Student --> Job[직업/퀘스트]
  Student --> Shop[상점/시장]
  Student --> Finance[저축/투자/대출]
  Student --> Game[게임/퀴즈]

  Helper -. 공개자료 추가 실측 필요 .-> Manage
  Public -. 공개범위 실측 필요 .-> Wallet
~~~

교사/학생 기본 역할 C. 학생 보조권한의 정확한 범위 U.

## 5. 핵심 Money Flow

~~~mermaid
flowchart LR
  Issue[발행/보상] --> Wallet[학생 학급화폐]
  Salary[직업급여] --> Wallet
  Quest[퀘스트/학습보상] --> Wallet

  Wallet --> Shop[아이템 구매]
  Wallet --> Saving[저축/예금]
  Saving --> Interest[이자]
  Interest --> Wallet

  Wallet --> Tax[세금]
  Tax --> Treasury[국고]
  Treasury --> PublicSpend[공공지출]

  Wallet --> Asset[자산/투자]
  Asset --> GainLoss[수익/손실]
  GainLoss --> Wallet

  Wallet --> Market[학생시장]
  Market --> OtherWallet[다른 학생 경제]
~~~

기능 C. 실제 원장 처리 I/U.

## 6. 주요 상태기계

### 직업

~~~mermaid
stateDiagram-v2
  [*] --> 모집
  모집 --> 지원
  지원 --> 배정
  배정 --> 근무
  근무 --> 급여예정
  급여예정 --> 지급
  지급 --> 근무
  근무 --> 종료
  종료 --> [*]
~~~

지원/급여 기능 C, 정확한 내부 상태 I.

### 세금정책

~~~mermaid
stateDiagram-v2
  [*] --> 규칙작성
  규칙작성 --> 영향미리보기
  영향미리보기 --> 활성
  활성 --> 징수
  징수 --> 국고
  국고 --> 공공지출
~~~

영향 미리보기와 국고 흐름 C.

## 7. 자동화 구조

C로 확인 가능한 자동화:
- 직업 급여
- 저축 이자
- 세금
- 국고 정기지출

I 구조:

~~~mermaid
flowchart TD
  Rule[경제 규칙] --> Scheduler[예약 실행]
  Scheduler --> SalaryRun[급여]
  Scheduler --> InterestRun[이자]
  Scheduler --> TaxRun[세금]
  Scheduler --> TreasuryRun[국고 지출]
  SalaryRun --> Ledger[경제 기록]
  InterestRun --> Ledger
  TaxRun --> Ledger
  TreasuryRun --> Ledger
~~~

내부 scheduler 구현은 U.

## 8. 복잡도 관리 구조

최근 공개 업데이트에서 설정 메뉴 재분류와 일부 카드 숨김 기능이 확인된다.

~~~mermaid
flowchart TD
  Core[기본 경제]
  Advanced[고급 경제]
  Game[놀이/게임]
  Experimental[실험 기능]

  TeacherSetting[교사 설정] --> Core
  TeacherSetting --> Advanced
  TeacherSetting --> Game
  TeacherSetting --> Experimental

  Advanced --> VisibleA[학생에게 활성 기능만 노출]
  Game --> VisibleA
  Experimental --> VisibleA
~~~

## 9. 구조상 핵심 위험

- 유입 기능이 많아 통화량 증가 가능
- 경제·게임 메뉴 혼합 시 탐색 복잡도
- 실제 좌석/사물함 자산화의 교육권 충돌
- 학생시장 개방 시 분쟁/갈취/후기 안전
- 실제 시장연동 투자의 투기적 해석
- 삭제된 객체를 과거 알림/거래가 참조하는 lifecycle 문제

## 10. Unknown

U:
- 실제 DB/원장 방식
- 학생간 시장 결제의 원자성
- 환불/정정 내부 처리
- 모바일 실제 메뉴 깊이
- 학생 역할별 정확한 권한
- 자산/대출의 동시성 처리

## 11. Class Money에 주는 구조적 교훈

X:
- Core Currency / Activity Currency / Treasury를 분리 가능하게 설계
- 기능을 Module로 숨기고 단계적으로 개방
- 세금·급여 등 정책 변경 전에 영향 시뮬레이션
- 학생시장은 Store와 별도 Marketplace Domain
- 장기 확장을 위해 처음부터 거래원장 기반

## 근거
- https://classcoin.me/
- https://classcoin.me/guide
