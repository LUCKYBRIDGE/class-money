# Class Money Economy Kernel v4

기준일: 2026-11-08  
상태: 구현 전 아키텍처 제안  
근거: ClassBank, Cashroom, ClassCoin, ClassCents, Banqer, My Classroom Economy의 공개 동작을 비교해 도출한 Class Money 독자 설계

## 1. 경제 기능보다 먼저 만들어야 할 커널

직업, 상점, 저축, 세금, 경매, 대출은 서로 다른 기능처럼 보이지만 결국 모두 ‘누가 누구에게 어떤 이유로 얼마를 이동했는가’로 귀결된다.

따라서 UI보다 먼저 안정화해야 할 것은 거래 커널이다.

핵심 요구:
- 모든 금액 이동의 추적 가능성
- 중복실행 방지
- 연결된 거래의 원자성
- 정정 가능성
- 예약실행 신뢰성
- 학급별 데이터 격리
- 정책 변경 전후 이력

## 2. Account 모델

권고 Account 종류:

STUDENT_AVAILABLE
학생이 현재 사용할 수 있는 지갑

STUDENT_SAVINGS
일반 저축

STUDENT_GOAL
목적 저축

CLASS_TREASURY
세금/공동체 기금

ISSUANCE
새 화폐 발행의 반대계정

STORE_REVENUE_OR_SINK
상점에서 회수되는 돈

DEBT
대출 모듈 활성화 시 별도 부채

ACTIVITY_CURRENCY
특정 게임/활동의 분리 재화

기본 Class Money는 AVAILABLE + SAVINGS + TREASURY + ISSUANCE 정도만 사용한다.

## 3. Transaction과 Entry

Transaction:
왜 돈이 움직였는지 설명하는 사건

Entry:
어느 계정에서 얼마가 빠지고 들어갔는지 기록

한 Transaction의 Entry 합계는 항상 0.

예: 직업급여 50
ISSUANCE -50
STUDENT_AVAILABLE +50

예: 저축 20
STUDENT_AVAILABLE -20
STUDENT_SAVINGS +20

예: 세금 10
STUDENT_AVAILABLE -10
CLASS_TREASURY +10

이 구조면 돈이 생성/소멸/이동되는 이유를 구분할 수 있다.

## 4. 잔액은 원인이 아니라 결과

wallet.balance를 직접 수정하는 API를 만들지 않는다.

잘못된 방식:
student.balance = 100

권고:
award, purchase, transfer, tax, reverse 같은 명령이 Transaction을 만들고 잔액은 Entry 합산으로 계산.

성능 때문에 balance cache를 두더라도 원장에서 재구성 가능해야 한다.

## 5. Idempotency

교실경제에서 가장 치명적인 오류 중 하나는 중복급여다.

모든 자동/네트워크 재시도 명령에 idempotency key가 필요하다.

예:
class + payroll_rule + period + student

같은 조합은 한 번만 성공.

상점 order approve도:
order_id + approve
를 한 번만 확정.

## 6. Reversal

거래를 삭제하지 않는다.

원거래:
Salary +50

정정:
Reversal -50, reversal_of = original transaction

복합 기능은 도메인별 reversal policy를 가진다.

Store:
환불 + 재고 복원 + coupon 복원

Auction:
hold 해제 + 낙찰 상태 취소

Loan:
원금/이자/상환계획 재계산

## 7. Hold

주문/경매에서 실제 결제 전에 돈을 예약할 필요가 있다.

available balance = posted balance - holds

학생이 100을 가지고 80짜리 주문 두 개를 동시에 넣어도 두 번째는 사용할 수 없어야 한다.

Hold 상태:
ACTIVE
CAPTURED
RELEASED
EXPIRED

## 8. Scheduler

자동급여, bills, 이자, 세금은 단순 cron 한 줄로 처리하지 않는다.

Rule:
언제 무엇을 실행할지

Run:
특정 날짜의 실제 실행

Run Item:
학생별 성공/실패

필수 필드:
- scheduled_at
- started_at
- completed_at
- status
- attempt
- error
- operation_key

교사 UI:
다음 실행, 예상 인원, 예상 총액, 마지막 성공을 보여준다.

## 9. Policy Version

세율, 급여, 상품가격이 바뀌면 과거 거래에 새 규칙을 적용하면 안 된다.

각 transaction/order/payroll item은 당시 정책 snapshot 또는 version id를 참조한다.

예:
11월 1일 주급 50
11월 15일 60으로 변경
11월 8일 거래는 계속 50으로 설명 가능해야 한다.

## 10. Classroom Scope

모든 핵심 객체에 classroom_id를 포함한다.

학생 identity와 wallet scope는 분리:
한 학생이 여러 반에 있더라도 기본 지갑은 classroom별.

학교 전체 공용경제는 별도의 school economy mode에서 명시적으로 연결.

## 11. Command API

UI의 CRUD보다 도메인 명령 중심이 안전하다.

awardMoney
reverseTransaction
approveOrder
rejectOrder
transferToSavings
executePayroll
collectTax
applyForJob
hireStudent

각 명령은:
- actor
- permission
- current state
- idempotency
- invariant
- audit
를 검사.

## 12. 불변조건

- 일반 학생 지갑은 0 미만 금지
- Transaction entry 합 = 0
- 한 period 급여는 학생당 1회
- 승인된 주문 가격은 snapshot 유지
- 학생은 자기 계정 외 수정 불가
- 삭제된 직업/상품도 과거 거래 설명 가능
- 학기 종료 상태에서는 자동작업 중지
- reversal은 원거래를 보존

## 13. Class Money의 핵심 기술 경쟁력

ClassCents 수준의 빠른 UX,
Cashroom 수준의 자동화,
ClassBank 수준의 학습확인,
ClassCoin 수준의 확장성을 동시에 얻으려면
기능별로 balance를 직접 수정하는 구조를 피해야 한다.

경제 커널은 처음에는 과한 설계처럼 보이지만 이후 세금·시장·저축·경매가 늘어날수록 복잡도를 흡수하는 기반이 된다.
