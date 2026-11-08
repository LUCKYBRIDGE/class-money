# YNAB — 기능 얽힘·UI·UX 심층 분석

기준일: 2026-11-08  
분석 목적: **복잡한 예산 모델을 ‘돈의 목적’이라는 한 가지 질문으로 단순화하는 방식** 분석

## 1. 복잡성의 본질
YNAB 내부 개념은 단순하지 않다.
- Accounts
- Transactions
- Categories
- Category Groups
- Ready to Assign
- Assigned
- Available
- Targets
- Scheduled Transactions
- Auto-Assign
- Overspending

그러나 사용자에게 핵심 질문을 하나로 압축한다:
**“지금 가진 돈을 어디에 둘 것인가?”**

\`\`\`mermaid
flowchart LR
 I[Income] --> R[Ready to Assign]
 R --> C1[Category A]
 R --> C2[Category B]
 R --> C3[Goal]
 C1 --> A1[Available]
 C2 --> A2[Available]
 C3 --> A3[Available]
 T[Targets] --> C1
 T --> C2
 T --> C3
\`\`\`

## 2. 복잡함을 풀어낸 가장 좋은 방식: 언어를 바꿈
YNAB는 최근 “budget”을 “plan”으로 바꾸고, 복잡한 target type을 사용자가 원하는 결과 중심의 문장으로 설정하게 단순화했다.

핵심:
기능을 제거하지 않고 **사용자가 시스템 내부 모델을 이해하지 않아도 되게 한다.**

Class Money:
학생에게
- 계좌배분
- 예산카테고리
같은 용어보다
- 지금 쓸 돈
- 모을 돈
- 목표에 넣을 돈
처럼 행동 언어를 사용.

## 3. Ready to Assign — 복잡한 돈 상태를 한 곳에 모음
새 수입은 ‘아직 목적이 정해지지 않은 돈’으로 모이고 0이 될 때까지 category에 배분한다.

장점:
- 돈이 들어왔다는 사실과 쓸 수 있다는 사실을 분리.
- 미래 의도를 먼저 정함.
- 모든 카테고리의 합계를 사용자가 직접 계산할 필요 없음.

Class Money:
급여 수령 직후 선택형:
“이번 돈 100을 어떻게 나눌까요?”
[쓸 돈 50] [목표 30] [모아두기 20]

저학년은 자동추천 후 확인만.

## 4. Available을 의사결정 숫자로 사용
YNAB에서 daily spending 결정의 기준은 account balance가 아니라 category Available이다.

Class Money에 매우 중요:
학생에게 ‘총자산 300’보다 ‘지금 상점에서 쓸 수 있는 돈 70’을 크게 표시.

저축/국고/hold된 돈까지 총잔액으로 보여주면 구매력을 잘못 이해할 수 있다.

## 5. Targets — 복잡한 목표 규칙을 plain language로
공식 업데이트는 기능을 줄이지 않고 target 설정 방식을 더 직관적 언어로 바꿨다고 설명한다.

Class Money:
목표 설정 UI는:
- 무엇을 위해?
- 얼마가 필요해?
- 언제쯤?
세 질문.

이자계산식·기간유형 같은 세부 규칙은 필요할 때만 Advanced.

## 6. Auto-Assign — 자동화 전에 Preview
Auto-Assign은 targets/scheduled transactions에 따라 돈을 자동 배분하지만 저장 전에 preview를 제공한다.

이 패턴은 Class Money 전체에 적용 가치가 크다.

교사:
- 급여 일괄 지급 preview
- 세금 부과 preview
- 학기 이월 preview

학생:
- 급여 자동배분 preview

**자동화 = 즉시 실행이 아니라 자동 제안 + 미리보기**가 더 안전하다.

## 7. Focused Views와 숨김
많은 category가 있어도 필요한 subset을 focused view로 보는 접근이 있다.

Class Money 교사 거래장부:
- 전체
- 오늘
- 실패
- 급여
- 상점
- 정정
- 학생도우미 처리
같은 focused filter를 기본 제공.

## 8. 색 상태의 위험
YNAB은 target 상태를 색으로 구분한다. 금융앱에서는 빠르지만 초등/접근성에서는 색 하나에만 의존하면 안 된다.

Class Money:
아이콘 + 문구 + 색 병행.
“목표까지 20 남음”을 반드시 텍스트로.

## 9. 복잡한 자동분류는 내부에서 해결
YNAB은 payee history를 기반으로 category를 자동 추천하는 고급 규칙을 내부에서 처리하지만 사용자는 필요하면 기본 category를 직접 고정하거나 자동화를 끌 수 있다.

Class Money 원칙:
자동 추천은 **설명 가능하고 끌 수 있어야 한다.**
교사 행동을 학습해 자동 지급을 임의 수행하는 식의 불투명 자동화는 피한다.

## 10. Class Money 적용
- 총잔액보다 Available.
- 새 수입은 목적 결정 단계 제공.
- 고급 개념을 일상 언어로 번역.
- 자동화는 preview 후 확정.
- 거래장부 focused views.
- 목표는 ‘무엇/얼마/언제’로 단순화.
- 색에만 의존하지 않는 상태 UI.

## 공식 근거
- https://support.ynab.com/en_us/getting-started-assigning-your-money-in-ynab-SyHCkywTZl
- https://support.ynab.com/en_us/auto-assign-a-guide-r1gBNbBJo
- https://support.ynab.com/en_us/getting-started-targets-in-ynab-r1FTiSaTbe
- https://www.ynab.com/whats-new/noticed-a-change-to-your-progress-bars
