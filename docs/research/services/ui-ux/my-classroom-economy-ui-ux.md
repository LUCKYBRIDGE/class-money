# My Classroom Economy — 기능 얽힘·UI·UX 심층 분석

기준일: 2026-11-08  
성격: 앱 UI보다 **물리적 서비스 디자인** 분석

## 1. 왜 UI/UX 분석 대상인가

이 시스템은 웹앱 중심이 아니지만:
- Job application
- Job offer
- Paycheck
- Bank log
- Bank slip
- Fine ticket
- Rent agreement
- Deed
- Auction record
- Auction paddle
처럼 역할별 서식이 매우 세분화되어 있다.

즉 화면 대신 **종이가 인터페이스**다.

## 2. 기능 얽힘

\`\`\`mermaid
flowchart LR
  JOB[Job application]
  PAY[Paycheck]
  BANK[Bank log]
  RENT[Rent]
  BONUS[Bonus/Fine]
  AUC[Auction]
  LOAN[Loan]
  REF[Reflection]

  JOB --> PAY --> BANK
  RENT --> BANK
  BONUS --> BANK
  AUC --> BANK
  LOAN --> BANK
  BANK --> REF
\`\`\`

모든 기능이 Bank Log로 수렴한다.

이것이 매우 중요한 설계 원리다.

Class Money에서도 모든 기능을 결국 동일한 Transaction Ledger로 수렴시켜야 한다.

## 3. 각 복잡한 행위를 별도 서식으로 분해

한 장의 거대한 경제양식이 없다.

- 취업 → Job application.
- 지급 → Paycheck.
- 입출금 → Bank slip.
- 월세 → Rental agreement.
- 경매 → Auction record.

복잡한 사회 시스템을 **작은 역할별 인터페이스**로 나눈다.

디지털 제품도 같은 원칙:
각 화면은 하나의 사용자 질문에 집중.

## 4. 종이의 장점

종이는 상태가 눈앞에 남는다.
- 월급수표를 받음.
- 통장에 적음.
- 은행원에게 제출.
- 월세 납부.

디지털화하면 이러한 물리적 단계가 사라져 경제 흐름이 보이지 않을 수 있다.

Class Money:
자동화 후에도 ‘급여명세’, ‘거래 영수증’, ‘월간 결산’ 같은 visual artifact를 남긴다.

## 5. Bank Log의 UX 가치

수기 log는 비효율적이지만:
- inflow/outflow
- 잔액
- 날짜
를 한 줄로 연결한다.

학생은 잔액이 갑자기 변하는 것이 아니라 거래의 누적이라는 것을 경험한다.

Class Money 거래내역:
날짜 | 이유 | 들어옴 | 나감 | 이후 잔액
구조가 초등학생에게 매우 적합하다.

## 6. 역할의 UX

Banker 학생이 자신의 장부뿐 아니라 여러 client ledger도 관리한다.

이것은 실제 업무 체험이라는 장점이 있지만 디지털에서는 타인 자산 접근 위험이 생긴다.

Class Money:
학생 Banker에게 raw ledger 편집권한을 주지 않고 승인된 작업만 가능.

## 7. Auction의 물리 UX

Auction paddle은 학생이 입찰 의사를 물리적으로 드러내고 교사가 즉시 전체 상황을 볼 수 있게 한다.

디지털 경매가 오히려 이 가시성을 잃을 수 있다.

Class Money에서 경매를 구현하면:
- 현재 가격
- 남은 시간
- 내 최대 예산
- 최근 입찰
을 교실 프로젝터 화면에 표시하는 shared screen 필요.

## 8. 출력물이라는 확장 UI

Class Money가 웹앱이어도 인쇄물을 적극적으로 제공하는 것이 좋다.

출력 후보:
- 직업 카드
- 월급 명세
- 학생 통장
- 상점 가격표
- 경제 규칙
- 세금/국고 보고서
- 경매 번호표
- 학기말 결산

‘앱=화면’이라는 제한을 벗어난다.

## 9. 디지털화할 때 없애야 할 마찰

없애기:
- 장부 합계 계산
- 반복 월급 계산
- 누락 검증
- 교사 수작업 잔액 수정

남기기:
- 선택
- 예상 계산
- 기록 확인
- 계약/규칙 이해
- 회고

## 10. Class Money 핵심 적용

My Classroom Economy에서 얻을 UI/UX 결론:
**복잡한 사회 시스템을 하나의 대시보드로 압축하지 말고, 각 행위의 맥락을 가진 작은 인터페이스와 기록물로 나눈다.**

## 공식 근거
- https://myclassroomeconomy.org/en/grades4-5
- https://myclassroomeconomy.org/assets/printables/en/4-5/Program_Guide_4-5.pdf
