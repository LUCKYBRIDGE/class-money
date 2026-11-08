# Revolut Kids & Teens — 기능 얽힘·UI·UX 심층 분석

기준일: 2026-11-08  
분석 목적: 아동 자율성·보호자 승인·Goals/Challenges·연령별 기능의 UI 구조 분석.

## 1. 복잡성의 본질
아동 계정은 보호자가 관리하지만 아이가 직접 쓰며, 일부 기능은 연령·위험도에 따라 다르게 열린다.

\`\`\`mermaid
flowchart LR
 P[Parent App] --> A[Allowance/Add Money]
 P --> CH[Challenges]
 P --> PE[Approvals/Permissions]
 K[Kids & Teens App] --> GO[Goals]
 K --> AN[Analytics]
 K --> CH
 A --> K
 CH --> E[Extra Pocket Money]
 E --> GO
 PE --> PAY[Payments/Transfers]
\`\`\`

핵심 문제는 ‘아이에게 얼마나 맡길 것인가’를 하나의 ON/OFF로 풀 수 없다는 점이다.

## 2. 역할별 앱/정보구조
보호자는 자신의 앱에서 계정을 만들거나 승인하고, 아이는 Kids & Teens 앱을 사용한다. 관리자와 사용자의 primary action을 같은 화면에 섞지 않는다.

Class Money도 Teacher shell과 Student shell을 routing/navigation부터 분리한다.

## 3. 연령별 Progressive Access
공식 서비스는 연령에 따라 계정 생성·결제·송금 등의 사용 가능 범위가 달라진다.

Class Money 변환:
- 1~2학년: 내 돈/목표/상점
- 3~4학년: +직업/저축/간단 예산
- 5~6학년: +세금/시장/승인형 송금

학년은 기본 프리셋이며 교사가 조정한다.

## 4. Challenges
과업과 보수를 한 객체로 묶는다.

Class Money 과업 카드:
- 해야 할 일
- 마감
- 보수
- 상태

상태:
할 일 → 완료 제출 → 확인 중 → 지급됨.

과업완료와 지급상태를 분리해 실패를 추적한다.

## 5. Goals
목표 저축은 spending money와 분리된다.

학생 홈:
- 사용 가능
- 목표
- 일반 저축

‘총잔액’ 하나보다 의사결정에 유용하다.

## 6. Analytics
아이 스스로 spending trends를 볼 수 있게 한다.

Class Money도 학생용:
- 이번 주 수입/지출
- 목표 변화
- 주요 소비유형
- 지난주 대비
를 자기성찰용으로 제공한다.

## 7. 위험 기반 승인
모든 행동을 승인하지 않고 위험이 큰 행동만 통제한다.

자동 가능:
- 본인 지갑→본인 저축
- 교사가 허용한 소액 기본상점 구매

승인 필요:
- 고액구매
- 학생간 송금
- 학생 운영자 지급
- 대출
- 특별 거래

이렇게 해야 승인함이 폭증하지 않는다.

## 8. Co-Parent에서 얻는 권한 UX
제2관리자에게 제한된 관리권한을 주는 구조는 Class Money의 Co-teacher에 유용하다.

권한을:
조회 / 지급 / 상점 / 학생관리 / 경제정책 / export
로 세분화한다.

## 9. 학생에게 보이지 않아야 할 복잡성
학생은 승인 규칙, 공동관리자, 보안정책을 편집할 필요가 없다.

결과만 이해하면 된다:
“이 거래는 선생님 확인이 필요해요.”

## 10. Class Money 적용
- 교사/학생 shell 분리.
- 학년별 progressive access.
- 과업과 보수를 같은 카드에 연결.
- 목표저축과 spending money 분리.
- 학생 자기 analytics.
- 위험 기반 승인.
- co-teacher 권한 세분화.
- 관리자 복잡성을 학생 화면에서 제거.

## 공식 근거
- https://www.revolut.com/revolut-kids-and-teens-parent-and-guardians/
- Revolut Kids & Teens Terms — Challenges & Goals / approval / Co-Parent sections
