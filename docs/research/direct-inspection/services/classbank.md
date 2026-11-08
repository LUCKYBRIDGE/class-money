# ClassBank 직접 관찰

기준일: 2026-11-08

## 직접 연 페이지
- https://www.classbank.com/
- https://help.classbank.com/en/articles/6499058-how-do-i-get-started-with-classbank
- https://help.classbank.com/en/articles/5949828-student-helper-jobs-banker-hr-manager-and-store-clerk
- https://help.classbank.com/en/articles/6499914-classbank-suggested-settings

## 홈페이지에서 직접 확인한 설명 구조
How ClassBank Works가 먼저 네 가지 행동으로 제품을 압축한다.
- Award Bonuses
- Assign Jobs
- Charge Bills
- Manage your Store

그 뒤 saving, budgeting, financial literacy, school/district로 확장한다.

기능 전체를 보여주기보다 **핵심 4 action을 mental model로 먼저 제공**한다.

## 실제 Getting Started 구조
공식 가이드에서 대부분의 교사에게 먼저 권하는 것:
1. Classes
2. Students
3. Bonuses
4. Store

Optional:
5. Jobs
6. Bills
7. Savings / Interest
8. Co-teachers

Progressive Disclosure가 단순 해석이 아니라 실제 온보딩 구조임을 확인했다.

## Roster 입력 경로
- Class Code
- Manual
- Spreadsheet import
- School subscription search

학교별 환경 차이를 하나의 가입방식으로 강제하지 않는다.

## 설정 위치
- Class → Setup → Bonuses/Fines
- Class → Store → All Items
- Class → Jobs → Add Job
- Setup → Bills
- Blue Panel gear → Edit Class → Savings
- Class → Co-Teacher

설정이 중앙 Settings 하나에 몰려 있지 않고 기능 맥락에 분산된다.

## Student Helper 권한
공식 Help에서 직접 확인:
- Store Clerk: 구매 승인 + 상품 편집
- HR Representative: job board + jobs 편집
- Banker: transaction 전송

중요한 점은 Student Helper permission을 준 것과 실제 Job으로 채용/급여를 받는 것이 별도라는 점이다.

즉 **역할명과 시스템 권한이 분리**되어 있다.

## Audit
학생 helper가 보낸 transaction은 교사가 All Transactions에서 filter/search할 수 있다.

Class Money에서 helper 기능을 도입할 경우 반드시 actor, role, target, amount, timestamp가 감사로그에 남아야 한다.

## 경제 Balance 가이드
3–5학년 공식 예시:
- salary 약 100/month
- expense 약 80/month
- base spending 약 20/month

핵심은 수치 자체보다 **정기수입 > 정기필수비용** 원칙이다.

## 공개 GitHub 판정
현재 ClassBank 제품 본체의 공식 public source repository는 확인하지 못했다.

## 현재 미확인
- 학생 account first fold
- store purchase 실제 상태
- helper permission 실제 메뉴 제한
- co-teacher 권한 세분성
- auto pay 실패 상태
- 반응형 UI

## Class Money에 가져올 것
- 최소 시작: 반/학생/지급/상점
- roster 입력 다중경로
- job과 permission 분리
- helper action 감사로그
- 경제밸런스 실시간 시뮬레이터
- 중앙 기능상태 페이지 + 기능 내부 설정의 이중구조

## 주의
ClassBank의 bonus/fine 체계는 행동점수와 경제자산을 강하게 연결할 수 있어 Class Money 기본모델로 그대로 사용하지 않는다.