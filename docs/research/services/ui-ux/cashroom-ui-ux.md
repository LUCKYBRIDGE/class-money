# Cashroom — 기능 얽힘·UI·UX 심층 분석

기준일: 2026-11-08  
핵심: **많은 경제 기능을 Pending + Math Check + History라는 공통 인터랙션으로 압축**

## 1. 복잡한 기능 관계
급여, 청구서, 벌금, 상점, 쿠폰, 경매, 저축, CD, 대출은 서로 다른 기능이지만 학생에게는 ‘돈이 움직이는 사건’이라는 공통점이 있다.

\`\`\`mermaid
flowchart LR
 E[Paycheck/Bill/Purchase/Fine] --> P[Pending]
 P --> M[Math Check]
 M --> R[Record]
 R --> B[Balance]
 B --> H[History]
\`\`\`

여기서 Cashroom의 핵심 UX 전략은 **기능마다 다른 거래 인터랙션을 만들지 않는 것**이다.

## 2. Pending이 복잡성을 푸는 방식
자동급여나 자동청구가 실행돼도 학생이 계산을 기록하기 전에는 Pending으로 남는다. 오래된 항목부터 처리하고, Pending이 남아 있으면 일부 소비 기능이 제한된다.

장점:
- 자동화가 학생 몰래 잔액만 바꾸지 않음.
- 학생이 모든 돈 이동을 한 번 확인.
- 해야 할 경제 활동이 queue로 정리됨.

위험:
- 결석 뒤 Pending이 많이 쌓이면 과업 부담.
- 반복 계산이 학습보다 의식행위가 될 수 있음.

Class Money:
교사/학생별로 ‘거래 확인 모드’를 켜고 끌 수 있게 하고, 결석 학생은 교사가 대신 정리 가능.

## 3. Math Check UI
공개 화면은 한 번에 딱 세 정보를 준다.
- 기존 잔액
- 들어오거나 나가는 금액
- 새 잔액 입력

틀려도 불이익이 없고 다시 시도하며, 반복 오류에는 힌트를 준다.

좋은 UX 이유:
- 하나의 primary action.
- 숫자 방향이 명확.
- 거래와 수학이 직접 연결.
- 오류를 처벌하지 않음.

Class Money 학년별 변형:
- 1~2: 보기 중 선택.
- 3~4: 직접 입력.
- 5~6: 직접 입력 + 변화 이유/식 선택.

## 4. One Bell — 교사 복잡성을 ‘할 일’로 압축
직업지원, 대출요청, 상점주문, 잔액 0 이하, 경매 종료 등을 한 알림 영역에 모은다.

기능별로 들어가 확인하는 대신:
**무엇을 처리해야 하는가?**
를 기준으로 정보구조를 바꾼다.

Class Money 교사 홈:
- 승인 대기
- 실패/주의
- 오늘/이번주 예정
을 가장 위에 둔다.

## 5. Undo가 단순하지 않은 것을 UI에서 인정
Cashroom은 plain transaction은 History에서 undo하지만 구매·대출·경매처럼 연결된 상태가 있으면 해당 기능에서 되돌린다.

이 방식은 ‘거래 삭제’라는 거짓 단순화를 피한다.

Class Money:
History에서 정정 버튼을 누르면 transaction type에 맞는 복구 화면으로 연결.
- 지급 → 역거래
- 구매 → 주문 취소 + 환불 + 재고복원
- 경매 → 낙찰상태/hold 복구
- 대출 → 상환스케줄 정정

## 6. 상점 UX와 상태
학생:
상품 → 계산 → 주문 → 승인 대기 → 승인/거절 → 영수증.

거절 시 돈/쿠폰 반환을 명시한다.

Class Money 상태:
\`\`\`
REQUESTED → RESERVED → APPROVED → FULFILLED
          ↘ REJECTED → RELEASED
APPROVED → REFUNDED
\`\`\`

UI는 각 상태마다 다음 행동을 알려줘야 한다.

## 7. 학생별 Accommodation
Math Check를 학생별 끌 수 있다. 동일 반 안에서 기능은 같지만 인지 부담을 조절한다.

Class Money도 학생별 지원 설정:
- 계산 방식
- 힌트 수준
- 글자 크기
- 추가 확인 단계
를 줄 수 있으나 다른 학생에게 표시하지 않는다.

## 8. 공유기기 UX
공식 Help는 학생과 교사의 자동 로그아웃 시간이 다르고 starter code 재발급을 지원한다.

Class Money:
- 항상 보이는 ‘학생 바꾸기’.
- 수업 끝나면 일괄 로그아웃.
- 개인 PIN 재발급.
- 이전 학생 정보 즉시 masking.

## 9. UI·UX 패턴 요약
| 복잡성 | Cashroom 해법 | Class Money |
|---|---|---|
| 여러 거래유형 | Pending+Math Check | 선택형 학습확인 |
| 여러 교사 요청 | One Bell | Today/Inbox |
| 개인별 차이 | per-student switch | 지원 프로필 |
| 오류 복구 | 거래유형별 undo | 상태머신 기반 정정 |
| 자동화와 학습 충돌 | 자동 생성+학생 record | 자동 운영+학습 확인 |
| 공유기기 | session expiry/starter code | 학생 전환 강화 |

## 10. 가장 중요한 결론
Cashroom은 기능을 줄이지 않고 **반복되는 상호작용을 통일**해서 복잡함을 줄인다.

Class Money도 기능마다 완전히 새 UI를 만들기보다:
‘요청 → 확인 → 처리 → 결과’
같은 공통 패턴을 설계해야 한다.

## 공식 근거
- https://cashroomapp.com/
- https://cashroomapp.com/help
