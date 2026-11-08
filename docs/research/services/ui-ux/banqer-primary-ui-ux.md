# Banqer Primary — 기능 얽힘·UI·UX 심층 분석

기준일: 2026-11-08  
핵심: **기능을 금융 개념별 Expansion으로 나누고, Dashboard 위젯과 학습자료로 복잡성을 관리**

## 1. 복잡한 구조

Banqer는 하나의 지갑 앱이 아니라 여러 생활금융 시뮬레이션의 집합이다.

\`\`\`mermaid
flowchart TD
  CORE[Core]
  INC[Basic Income]
  EXP[Expenses]
  JOB[Employment]
  BANK[Banking]
  SAV[Savings/Interest]
  TAX[Tax]
  PROP[Property]
  INS[Insurance]
  TRANS[Transport]
  STORE[Class Store]
  LEARN[Videos/Quiz/Activities]

  CORE --> INC --> EXP --> JOB --> BANK
  BANK --> SAV
  SAV --> TAX
  TAX --> PROP
  PROP --> INS
  PROP --> TRANS
  CORE --> STORE
  LEARN --> INC
  LEARN --> EXP
  LEARN --> JOB
  LEARN --> TAX
\`\`\`

모든 기능을 한 번에 보여주면 학생에게 너무 복잡하므로 **개념 단위의 Expansion**이 핵심 해법이다.

## 2. Expansion 방식의 UX 장점

교사가 학습 순서에 맞춰 기능을 연다.

이것은 단순 feature flag가 아니라:
‘이번에는 어떤 경제 세계를 배우는가?’
라는 교육 흐름과 연결된다.

Class Money:
설정 화면을 기능토글 목록보다 ‘학습 단계’ 카드로 설계.

예:
1. 돈 벌기
2. 계획하고 쓰기
3. 모으기
4. 공동체 세금
5. 시장 실험

## 3. Teacher Dashboard와 Student Dashboard 분리

Class Store 공식 도움말에서 교사 대시보드에 Store widget이 있고, 교사가 Store open/closed를 토글한다. 학생은 자기 dashboard에서 직접 store에 접근한다.

이 패턴의 핵심:
같은 기능을 교사와 학생에게 다른 control surface로 보여준다.

교사: 개방/정책/승인.
학생: 사용/선택/결과.

Class Money 전반에 이 역할 차이를 적용해야 한다.

## 4. Store UI의 복잡성 해소

학생:
Item → Add to cart → Checkout.

익숙한 전자상거래 mental model을 사용한다.

장점:
학생이 새 인터랙션을 학습할 필요가 적음.

주의:
교실경제에서는 shopping UX가 너무 재미있어지면 경제 학습이 소비 중심으로 치우칠 수 있음.

Class Money:
카트가 필요한지 검토.
상품 수가 적다면 바로 ‘구매 계획’ 화면이 더 적합할 수 있음.

## 5. 교사 기능 개폐

Store가 기본 closed이고 교사가 open한다.

Class Money에서 모든 고위험/집중 활동에 활용:
- 상점 운영 시간
- 경매 오픈
- 학생간 거래 오픈
- 세금 활동 오픈
- 시장 시뮬레이션 기간

항상 켜진 기능보다 수업 시간에만 여는 것이 교사 통제와 집중에 유리.

## 6. 기능 + 학습자료의 결합

Banqer는 단순 기능 메뉴가 아니라 금융개념과 학습자료를 함께 제공한다.

UX적으로:
‘설정을 끝내고 수업자료 찾으러 다른 곳’이 아니라 같은 개념 아래 운영과 학습을 둔다.

Class Money 모듈 화면:
- 이 기능이 무엇인가
- 교사 설정
- 10분 활동
- 학생 화면 미리보기
- 운영 시작
을 한 곳에 배치하는 방안.

## 7. 고급 개념의 정보 과부하

Property/Insurance/Transport 같은 기능은 서로 영향을 주는 생활비 시뮬레이션이 된다.

해법:
학생에게 모든 변수의 계산식을 노출하기보다:
- 선택
- 당장 비용
- 이후 정기 비용
- 위험
- 결과
만 보여준다.

Class Money 시뮬레이션 카드도 같은 구조로 단순화.

## 8. UI에서 배울 핵심

- 개념별 단계적 개방.
- 역할별 대시보드.
- Store open/close 같은 교사 통제.
- 익숙한 mental model 활용.
- 학습자료와 기능을 같은 맥락에 배치.

## 9. Class Money 적용

추천:
\`\`\`
학습 모듈 카드
[저축과 이자]
상태: 아직 시작 전
학생에게 보일 기능: 목표저축, 이자
예상 수업시간: 20분
[수업자료 보기] [학생화면 미리보기] [활성화]
\`\`\`

이렇게 하면 복잡한 경제 기능을 ‘설정’이 아니라 ‘수업 개시’로 이해할 수 있다.

## 공식 근거
- https://banqer.co/au/primary/how-it-works
- https://primary.banqer.co/nz/help/the-class-store
