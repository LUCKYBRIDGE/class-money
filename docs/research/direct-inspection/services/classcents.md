# ClassCents 직접 관찰

기준일: 2026-11-08

## 직접 연 페이지
- https://www.classcents.com/
- https://www.classcents.com/guides/how-to-set-up-a-classroom-economy

## 홈페이지가 제품 사용순서를 그대로 설명
Teacher:
Name the money → Payday Jobs → Shop → Transactions.

Setup:
1. Name the money and open Shop
2. Pay as the week goes
3. See every Balance

Student:
Earn → Spend → Save.

설명 IA와 실제 핵심 workflow가 거의 동일하다.

## Teacher-first 구조
홈에서 학생 login optional을 반복해서 강조한다.

학생이 로그인하지 않아도:
- Jobs
- Payday
- Give
- Deduct
- Redeem
이 교사 화면에서 작동한다.

이는 단순 fallback이 아니라 제품의 핵심 설계다.

## 공개 UI 문구
Purchase:
- Current Balance
- Cost
- New Balance

Goal:
- current of target
- amount to go

사용자가 transaction 후 상태를 계산하지 않아도 한눈에 본다.

## Roster
- CSV
- Excel
- spreadsheet paste

반복 학생폼 입력을 피한다.

## Quick transaction
- one student
- Group
- whole class
- Saved Reason

대상 범위와 reason preset으로 반복입력 비용을 줄인다.

## Payday
- daily
- weekly
- monthly
- app을 열지 않아도 실행
- Job Done requirement optional

## Undo / History
- 모든 Transaction 기록
- Give/Deduct undo
- whole-class action도 undo
- CSV export
- printable statement

오류수정이 부가기능이 아니라 핵심 운영기능이다.

## Login Card
- 학생 이메일 불필요
- 8 cards/page
- username + two-word + three-digit password
- l/1/I 혼동이 적은 typeface

인증 UX가 교실 출력물까지 포함한다.

## 경제 운영 가이드
공식 setup guide는:
- weekly payday가 관리성과 신뢰성의 균형이 좋다고 설명
- 상품 가격을 하루치/주급/3–4주 저축 수준으로 계층화
- deduction은 optional이며 rare/small을 권장
- 경제를 며칠에 나눠 도입

## One Balance across classrooms
같은 학생의 Balance가 여러 classroom에서 공유된다.

Class Money에서는 반별 정책 충돌 가능성이 있어 기본은 class-scoped wallet이 더 안전하다.

## 공개 GitHub 판정
현재 ClassCents 제품 source 공식 public repository는 확인하지 못했다.

## Class Money에 가져올 것
- Teacher-only mode
- paste-first roster
- login card
- Current/Cost/New
- Saved Reason
- batch undo
- automatic payday
- printable statement

## 가져오지 않을 것
- public balance leaderboard
- 기본 cross-class wallet