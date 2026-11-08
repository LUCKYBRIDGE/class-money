# Cashroom — 페이지·내비게이션

## 제품/화면 지도

| 페이지·Surface | 직접 확인/구조적 역할 |
|---|---|
| 홈 | Math Check 데모와 Earn→Bills→Spend→Save→Borrow cycle. |
| Student Money/Checking | Pending 거래와 Math Check. |
| Jobs | Student Job, Open Jobs, 지원, Payday. |
| Bills | 정기 청구. |
| Store | Cart, Orders, Coupons. |
| Auctions | 입찰과 금액 Hold. |
| Savings/Goals | Checking↔Savings, 목표, 이자. |
| Loans/Credit | 대출·신용. |
| Badges | 경제 milestone. |
| Teacher Bell | 지원·주문·대출·below-zero 등 action queue. |
| History/Undo | 일반 거래 정정. |
| Help/Auth | starter code, session, lockout. |

## 페이지 구조를 볼 때의 핵심

- 이 표는 공개 홈·공식 도움말·공개 가이드에서 확인 가능한 **외부 IA**다.
- 로그인 후 실제 route 이름이나 URL 구조와 동일하다고 단정하지 않는다.
- 제품 본체 source가 공개된 경우에만 실제 route/file tree를 별도 기술문서에 기록한다.

## Class Money 관점

- **홈**: Math Check 데모와 Earn→Bills→Spend→Save→Borrow cycle.
- **Student Money/Checking**: Pending 거래와 Math Check.
- **Jobs**: Student Job, Open Jobs, 지원, Payday.
- **Bills**: 정기 청구.
- **Store**: Cart, Orders, Coupons.
