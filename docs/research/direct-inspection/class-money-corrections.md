# 직접 관찰 뒤 Class Money 설계 보정

기준일: 2026-11-08

공개 사이트, 공식 Help/PDF, 공식 GitHub source를 직접 연 뒤 기존 설계에 추가하거나 수정할 항목.

## 1. 기능 중심보다 상태 중심 설계를 강화

### Store
- CLOSED
- OPEN
- REQUESTED
- PARTIALLY_APPROVED
- APPROVED
- FULFILLED
- REJECTED
- REFUNDED

### Task
- TODO
- SUBMITTED
- REOPENED
- APPROVED
- SKIPPED
- NOT_DONE

### Payment
- SCHEDULED
- PENDING_CONFIRMATION
- POSTED
- FAILED
- REVERSED

### Goal
- ACTIVE
- PAUSED
- ACHIEVED
- CANCELLED

상태는 단순 내부 enum이 아니라 학생·교사가 이해할 수 있는 문구와 다음 행동을 가져야 한다.

## 2. Disabled Reason 표준 컴포넌트

Cashroom 직접 관찰에서 특히 중요성이 확인됐다.

버튼이 비활성화될 때 반드시 이유를 보인다.
- 잔액이 부족해요
- 상점이 지금 닫혀 있어요
- 먼저 대기 중인 거래를 확인하세요
- 재고가 없어요
- 선생님 확인을 기다리고 있어요

silent disabled 금지.

## 3. Fallback Mode를 P0 요구사항으로

직접 확인한 사례:
- ClassCents: 학생 로그인 없이 교사 운영 가능
- Cashroom: 교사가 absent student의 pending transaction 대신 record 가능
- Rooster: bulk approve / skip / re-open

Class Money P0:
- Teacher-only operation
- Student login optional
- teacher acts on behalf + audit
- bulk resolve
- per-student exception

## 4. Save-time Validation

Greenlight 직접 Help에서 allocation 합계 100%와 category compatibility를 저장 전에 검사한다.

Class Money에서도:
- 배분 percentage 합
- payroll rule
- item price
- stock
- schedule conflict
- tax rule
을 저장 시 검증한다.

경제적으로 위험하지만 수업 의도상 가능한 값은 hard block보다 warning + explicit override가 적합하다.

예: 정기지출이 정기소득보다 큰 경우.

## 5. 경제규칙 변경 전 영향 Preview

ClassCoin의 현재 tax preview와 YNAB의 previewable automation 원칙을 결합한다.

급여/세금/정기비용/이자/학기이월을 바꾸기 전에:
- 영향을 받는 학생 수
- 학생당 변화
- 전체 총액
- 최소/최대 변화
- 다음 실행일
- 대표 example
을 보여준다.

## 6. Account와 Purpose를 분리

YNAB 공식 SDK 직접 분석을 반영한다.

Class Money domain을 구분:
- Account — 돈의 실제 위치
- Allocation / Goal — 돈의 목적
- Transaction — 실제 돈 이동
- AllocationMovement — 목적 간 배분 이동
- ScheduleRule — 미래 자동 이벤트

학생 UI에서는 단순하게 보여도 내부 domain을 하나의 wallet 객체에 몰아넣지 않는다.

## 7. Purchase와 Fulfillment를 분리

Banqer Class Store에서 구매 후 My Stuff → Claim이라는 별도 단계가 확인된다.

Class Money 실물/특전 상품:
- payment status
- fulfillment status
를 분리한다.

예:
PAID + WAITING_FULFILLMENT

상품을 돈으로 샀다는 것과 실제로 받았다는 것은 다른 사건이다.

## 8. StudentGroup과 GroupAccount를 분리

ClassDojo Group 직접 관찰에서 Group은 대상 selector로 작동하고 group point는 구성원 개별 report에 들어간다.

Class Money에서는:
- StudentGroup — 여러 학생을 한 번에 선택
- GroupAccount — 모둠 공동기금
을 별개 객체로 둔다.

UI도:
- 5명에게 각각 10 지급 — 총 50
- 1모둠 공동기금에 50 지급
처럼 명확히 구분한다.

## 9. 사용자에게 설명하는 순서 수정

### 학생
벌기 → 계획하기 → 쓰기 → 모으기 → 돌아보기

### 교사
설정 → 운영 → 승인 → 정정 → 결산

서비스 소개, onboarding, navigation이 이 mental model과 최대한 일치해야 한다.

## 10. 운영상 Open/Closed 상태를 기능 활성화와 구분

Banqer Class Store에서 기능 존재와 현재 Store open 상태가 분리된다.

Class Money에서도:
- Module enabled
- Activity currently open
을 구분한다.

예:
상점 기능은 사용하지만 매주 금요일 5교시에만 OPEN.

경매, 학생간 거래, 시장 실험에도 같은 개념 적용.

## 11. 실제 개발 전에 추가할 Acceptance Criteria

- 모든 disabled action은 이유가 있다.
- 학생 로그인 없이 teacher-only demo가 완주된다.
- 학생별 exception이 batch operation을 깨뜨리지 않는다.
- payment와 fulfillment 상태가 독립적이다.
- StudentGroup과 GroupAccount가 혼동되지 않는다.
- 자동규칙 저장 전에 영향 preview가 있다.
- 사용가능액과 총자산이 구분된다.
- 미래 예정 거래는 현재 사용가능액에 섞이지 않는다.
- task completion과 payment completion이 별도 상태다.
- 연결 거래를 정정하면 관련 재고/승인/hold까지 정합하게 복구된다.

## 12. 연구 문서 구조도 정리 필요

현재 repository에는:
- services/ui-ux
- services/ux
- services/dossiers
- research/structures
가 일부 중복된다.

직접 tree를 확인한 결과 분석이 깊어진 대신 같은 서비스의 비슷한 내용이 여러 폴더에 흩어져 있다.

권장 최종 구조:

docs/research/
  direct-inspection/    실제 사이트/repo 증거
  services/
    service-name/
      overview.md
      product-anatomy.md
      ux.md
  synthesis/
  verification/

기존 파일을 즉시 삭제하지 않는다. 직접관찰 증거가 충분히 쌓인 뒤 서비스별 폴더로 단계적으로 병합하고, 기존 링크는 redirect/index 역할로 남기는 편이 안전하다.

## 13. 다음 실측 단계

실제 Craft Anything 또는 동등한 Clean Room capture를 실행할 수 있는 환경에서 서비스별로:
- 360 / 768 / 1280 폭
- first fold
- navigation
- menu/dialog/tab states
- route graph
- click depth
- primary CTA
- form fields
- error states
- responsive changes
를 캡처해 S1 관찰을 E2 실측으로 끌어올린다.