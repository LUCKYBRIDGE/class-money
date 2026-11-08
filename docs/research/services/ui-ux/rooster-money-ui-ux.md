# NatWest Rooster Money — 기능 얽힘·UI·UX 심층 분석

기준일: 2026-11-08  
핵심: **정기 용돈과 추가 과업을 같은 시스템 안에서 구분하고, 반복 루틴을 단순하게 유지**

## 1. 기능 관계
\`\`\`mermaid
flowchart LR
 A[Allowance] --> W[Wallet/Tracker]
 C[Allowance Chores] --> A
 E[Extra Earners] --> W
 S[Stars/Virtual Rewards] --> W
 G[Savings Goals] --> W
 P[Parent] --> A
 P --> C
 P --> E
 K[Child] --> C
 K --> E
 K --> G
\`\`\`

복잡성은 ‘정기적으로 주는 돈’과 ‘추가로 벌 수 있는 돈’을 한 화면에서 혼동하지 않는 데 있다.

## 2. 핵심 UX: Allowance Chore vs Extra Earner
공식 도움말은 과업을:
- allowance를 받기 위해 필요한 chore
- 별도 추가보수가 있는 extra earner
로 구분한다.

이 구분은 Class Money에 매우 적합하다.

Class Money:
- 기본 참여소득
- 직업 기본업무
- 추가 과업 보수

세 층을 화면에서 명확히 구분.

모든 행동이 돈으로 바뀌는 구조를 피할 수 있다.

## 3. 반복 일정을 사람이 이해하는 언어로
과업에 특정 요일/반복일정을 부여한다.

Class Money에서는 cron 같은 기술적 설정 대신:
- 매일
- 매주 금요일
- 매월 첫째 주
- 한 번만
형태로 제공.

교실 스케줄에 맞게 ‘수업일만’ 같은 옵션은 별도 검토.

## 4. 과업 생성 UI
공식 흐름:
Chores → + → 추천 과업 또는 직접 생성 → 이름/이미지/메모 → 유형 → 일정.

좋은 점:
빈 폼부터 쓰게 하지 않고 추천 과업을 먼저 제공.

Class Money 직업/과업 생성도:
[추천에서 고르기] [직접 만들기]
두 경로를 둔다.

## 5. Child Dashboard에서 역할을 단순화
아이는 자신에게 필요한:
- 해야 할 일
- 받을 돈
- 모으는 목표
를 본다.

관리자의 반복 설정은 보이지 않는다.

Class Money 학생 홈에서 ‘직업 설정’ 같은 시스템 용어를 노출하지 않고:
오늘 할 일 / 다음 급여 / 추가로 할 수 있는 일
정도로 번역.

## 6. Stars와 Money의 단계화
Rooster는 어린 사용자에게 실제 돈 이전에 stars/virtual rewards로 earning/saving/spending 개념을 연습하게 하는 흐름이 있다.

Class Money:
저학년 모드에서는 복잡한 금융 용어 없이 단순 정수 화폐와 그림 중심.
고학년에서 세금·예산·이자 개념 확장.

단, 동일 서비스에서 화폐 종류를 너무 많이 만들면 혼란스러우므로 학급당 주 경제재화는 하나로 유지.

## 7. 완료 상태와 부분 지급
과업 완료 여부에 따라 allowance 지급정책을 다르게 운영할 수 있는 관점이 있다.

Class Money UI:
완료 상태:
- 완료
- 일부 완료
- 면제
- 확인 필요

지급 상태:
- 예정
- 지급됨
- 보류

둘을 섞지 않는다.

결석/지원 필요 학생에게 ‘미완료=무급’이 자동 적용되지 않게 교사 예외가 필요.

## 8. 루틴 중심 디자인
Rooster가 참고 가치가 있는 이유는 복잡한 투자 기능보다 **생활 리듬**이다.

Class Money 홈도 주기성을 드러낸다.
- 오늘: 할 일
- 이번 주: 금요일 급여
- 이번 달: 목표/정기 활동

학생이 다음 경제 이벤트를 예측할 수 있어야 계획이 가능하다.

## 9. 추천 콘텐츠의 UI 역할
연령별 chore 아이디어는 교사가 빈 화면에서 모든 직업을 발명하는 부담을 줄인다.

Class Money:
학년별 직업·과업 라이브러리.
선택하면 이름/설명/추천 보수가 채워지고 교사가 수정.

추천값은 정답이 아니라 시작점임을 표시.

## 10. Class Money 적용
- 정기소득/추가소득 UI 분리.
- 추천 직업/과업.
- 반복일정 프리셋.
- 완료상태와 지급상태 분리.
- 학생에게 다음 급여를 명확히 표시.
- 학년별 단순화 모드.
- 반복 루틴 중심 홈.

## 공식 근거
- https://support.roostermoney.com/en/articles/2943433-set-extra-earners-to-earn-additional-money-card-feature
- https://roostermoney.com/feature/chores-guide/
- https://roostermoney.com/feature/getting-started-with-roostermoney-tracker/
