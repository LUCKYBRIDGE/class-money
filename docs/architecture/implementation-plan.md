# 기술 구조 및 구현 계획 (초안)

> 기술 스택은 **미정**. 저장소가 초기화되기 전 단계로 프레임워크·DB·배포사를 확정하지 않는다.

## 도메인 모델 (제안)
- `classrooms(id, teacher_id, name, currency_name, currency_symbol, precision, timezone, settings)`
- `students(id, classroom_id, display_name, student_number, login_credentials_ref, status)`
- `jobs(id, classroom_id, title, pay_amount, pay_frequency, active)`
- `job_assignments(id, classroom_id, job_id, student_id, starts_at, ends_at)`
- `wallet_accounts(id, classroom_id, student_id?, account_type)`: 체크/저축/학급은행/운영조정계정.
- `ledger_transactions(id, classroom_id, operation_key, type, actor_id, reason, created_at, reversal_of?, metadata)`
- `ledger_entries(id, transaction_id, account_id, amount)`: 각 거래의 분개 합계 = 0.
- `store_items(id, classroom_id, title, price, stock?, enabled)`
- `orders(id, classroom_id, student_id, item_id, price_snapshot, status, request_key, reviewed_by?)`
- `payroll_runs(id, classroom_id, period_key, scheduled_for, status)`
- `audit_events(id, classroom_id, actor_id, action, entity_id, created_at, payload)`

학생 단위 보유 금액은 원장 합산에서 계산하며 캐시를 두더라도 검증 가능한 재구축 방식으로 유지. 정수 최소 단위를 사용해 부동소수점 오차 방지.

## 거래 불변 조건
1. 한 거래의 분개 합계 0 (교실 은행/발행 계정 포함).
2. 지갑 잔액이 음수가 되는 동작은 기본 거절 (교사가 켠 부채 시뮬레이션은 별도 계정과 한도).
3. 상점 주문 승인 시 가격 스냅샷·재고 차감·출금이 **단일 원자 트랜잭션**으로 처리.
4. API 재시도로 중복 지급되지 않도록 `operation_key` 유일 제약.
5. 실수 정정은 원장 삭제가 아닌 역분개·정정 이유 기록.
6. 학급 ID마다 권한/쿼리 경계 유지; 학생은 자신의 정보만 읽음.
7. 클라이언트 계산 금액을 신뢰하지 않고 서버에서 가격·권한·잔액 재검증.
8. 예약 급여는 서버 작업 또는 다음 접속 시 재조정 작업으로 수행하되 **동일 기간 지급은 1회**.

## 기술 결정 전 확인할 질문
- 학생 로그인: 일회용 코드/교사가 발급한 PIN/학교 인증 중 무엇이 적절한가? 코드 유출·공유기기 위협 고려.
- 백엔드가 없는 단독 정적 앱으로 다중기기 공유가 가능한가? **아니오**. 실시간 공유·교사 승인·원장 무결성에는 신뢰 가능한 공유 저장소/서버 계층 필요.
- 교사 오프라인 사용: 로컬 임시 작성은 가능하지만 연결 복구 후 중복/충돌 정책 필수.
- 학교 운영·학생정보 관련 보존 기한·삭제 및 백업 정책은 학교 정책 확인 후 확정.

## 구현 순서
1. `docs/` 기준 PRD 확정, 화면 와이어프레임, 학생/교사 사용 시나리오.
2. 인증·학급 격리·DB 스키마·거래 원장 단위 테스트.
3. 교사용 학생 등록·일괄 지급·되돌리기·거래내역.
4. 학생 지갑과 상점 주문·승인.
5. 직업 신청·주급/월급 배치와 중복 방지.
6. CSV 내보내기, 모바일 접근성, 오류처리·감사 로그.
7. 초등 1개 학급 모의 데이터로 파일럿 후 경제 규칙 조정.
8. 저축·지출·세금 등 확장 모듈 검토.

## 필수 테스트
- 동시에 두 번 상점 구매해도 총액/재고가 음수가 되지 않음.
- 급여 배치를 재실행·새로고침해도 같은 기간 중복 지급하지 않음.
- 교사 일괄 지급 25명 중 일부 실패 시 정확한 처리 인원·재시도 안내.
- 취소된 구매는 실제 환불 처리 및 이력 남김.
- 학생 A가 학생 B의 잔액/주문 정보 API 접근 시 차단.
- 다른 학급의 동일 학생번호가 데이터를 공유하지 않음.
- 네트워크 끊김·시간대·학기 변경·활동 비활성화 테스트.
- 시력이 약한 학생, 터치 기기, 키보드 이용자 접근성 확인.

## 교육적 위험 목록
| 위험 | 완화책 |
|---|---|
| 돈 많은 학생/적은 학생의 낙인 | 개인 자산 공개 랭킹 기본 OFF |
| 특정 직업/성취만 보상받는 편향 | 직업 순환·기본소득·다양한 기여 인정 |
| 벌금이 처벌·통제 수단으로 변질 | 기본 OFF, 투명한 학급 합의·이의제기 |
| 복잡한 금융으로 수업 목표 이탈 | 교사 단계별 기능 열기 |
| 확률형 보상 과몰입 | MVP 미포함 |
| 아동 개인정보 유출 | 별칭/번호 최소 수집, 엄격한 접근제어 |
