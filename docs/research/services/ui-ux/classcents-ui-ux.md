# ClassCents — 기능 얽힘·UI·UX 심층 분석

기준일: 2026-11-08  
핵심: **교사 단독 운영과 학생 자율 운영을 모두 지원하면서 입력 마찰을 최소화**

## 1. 기능 구조

\`\`\`mermaid
flowchart LR
  R[Roster]
  J[Jobs]
  P[Payday]
  G[Give/Deduct]
  S[Shop]
  SV[Savings/Goals]
  L[Student Login]
  T[Transactions]
  EX[Export/Statements]

  R --> J --> P --> T
  R --> G --> T
  R --> S --> T
  R --> SV --> T
  L --> J
  L --> S
  L --> SV
  T --> EX
\`\`\`

복잡한 기능이 있지만 운영의 기본축은 **학생명부와 Transaction**이다.

## 2. 가장 큰 UX 해법: 학생 로그인은 선택사항

학생이 로그인하지 않아도 교사가:
Jobs / Payday / Give / Deduct / Rewards redemption
을 모두 처리 가능하다.

이것은 단순 기능이 아니라 **운영 실패를 막는 이중 UX**다.

Mode A:
교사 1대 기기로 전체 경제 운영.

Mode B:
학생이 각자 dashboard 사용.

Class Money도 이 구조를 채택하면 학교 기기환경에 강해진다.

## 3. Roster 입력의 복잡성 해소

CSV/Excel/paste를 지원한다.

학급앱의 첫 UX에서 가장 흔한 실패는 학생 25명을 한 명씩 입력하게 하는 것이다.

Class Money 등록 UI:
큰 textarea에
\`\`\`
1 김하늘
2 박바다
3 이새봄
\`\`\`
붙여넣기 → 열 자동 인식 → 미리보기 → 확정.

엑셀 업로드는 보조.

## 4. Give/Deduct의 공통 인터랙션

대상:
- 개인
- Group
- 전체

Reason:
- 저장된 템플릿

금액:
- 템플릿 기본값 또는 수정.

이 조합으로 다양한 지급 케이스를 하나의 UI로 해결한다.

Class Money도 ‘개인지급 화면’, ‘모둠지급 화면’, ‘전체지급 화면’을 따로 만들 필요가 없다.

## 5. Payday 자동화

Job에 금액과 주기를 붙이고 daily/weekly/monthly로 실행.

또 Job Done을 요구할 수 있다.

복잡성:
급여 = 시간 + 직업 + 학생 + 완료상태.

UI 해법:
사용자가 스케줄러를 직접 구성하게 하기보다 몇 가지 cadence 선택지를 제공.

Class Money도 cron 같은 고급 설정 금지.
- 매주 금요일
- 격주 금요일
- 매월 첫 수업일
정도의 언어로.

## 6. Login Card UX

학생 이메일 대신 출력 가능한 username/password card.

특히 password가 두 단어+숫자이며 l/1/I 혼동이 적은 폰트를 쓴다고 설명한다.

이것은 작은 UI 디테일이지만 실제 교실에서 매우 중요하다.

Class Money:
- 8장/A4 인쇄
- QR + 짧은 코드 병행
- 숫자 0/O 등 혼동 회피
- 분실 시 재발급
- 공유 태블릿 학생 전환

## 7. 학생 구매 UX

공식 예:
현재 Balance
Cost
New Balance
를 구매 전 보여준다.

이 3줄은 매우 좋은 초등 금융 UI다.

Class Money:
\`\`\`
지금 쓸 수 있는 돈 24
이 상품 -20
사고 나면 4
\`\`\`

총자산/저축과 혼동되지 않게 ‘사용 가능’ 기준.

## 8. Save UX

Savings와 named Goal을 분리한다.

Goal은 ‘$8 of $12, $4 to go’처럼 남은 금액까지 직접 표현.

좋은 점:
퍼센트만 보여주는 progress bar보다 초등학생에게 구체적.

Class Money:
금액 + 시각 progress + 예상기간.

## 9. One Balance across classrooms — UX 단순성 vs 도메인 복잡성

사용자 입장에서는 여러 교실에서 하나의 balance라 편할 수 있다.

하지만 내부적으로는:
- 어느 반에서 돈을 벌었는지
- 어느 반 상점에서 쓸 수 있는지
- 교사별 정책 충돌
이 복잡해진다.

Class Money 기본은 학급별 balance.
학교 공용 경제는 명시적으로 연결.

## 10. Leaderboard

기능상 쉽고 동기부여가 될 수 있지만 개인 자산을 경쟁 UI로 보여주는 것은 Class Money에서 피한다.

대안:
- 공동 목표 progress
- 개인 목표
- ‘이번 주 경제 참여율’ 같은 학급 지표.

## 11. 복잡성 해소 패턴

| 문제 | 해결 |
|---|---|
| 학생 계정 준비 | 로그인 선택 |
| 대량 명부 | CSV/paste |
| 다양한 지급범위 | 개인/그룹/전체 공통 UI |
| 반복급여 | Payday |
| 설명 없는 돈 이동 | Reason |
| 오류 | Undo |
| 학생 인증 | printable card |
| 구매결정 | Current/Cost/New |

## 공식 근거
- https://www.classcents.com/
- https://www.classcents.com/guides/how-to-set-up-a-classroom-economy
