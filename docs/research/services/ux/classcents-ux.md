# ClassCents — 복잡성·정보구조·UI·UX 심층 분석

기준일: 2026-11-08  
증거 수준: 공식 홈페이지와 가이드에서 공개된 화면 예시·운영 흐름 중심.

## 1. 복잡성의 원천
ClassCents는 Jobs, Payday, Shop, Give/Deduct, Groups, Savings, Goals, Badges, Leaderboard, Transaction history, CSV export를 제공한다. 그런데 핵심 대상은 교사다. 따라서 가장 큰 UX 문제는 많은 기능을 얼마나 적은 준비와 조작으로 굴리는가이다.

## 2. 핵심 해법: Teacher-first
공식 설명은 학생 로그인 없이도 Jobs, Payday, Give/Deduct, Reward redemption을 교사 화면에서 운영할 수 있다고 명시한다.

즉 학생 디지털 경험은 선택이고 경제 운영은 교사만으로도 완결된다.

Class Money에 매우 유용한 패턴:
- Teacher-only mode를 정식 모드로 제공.
- 학생 계정은 학습 깊이를 늘리는 확장 기능.
- 기기·계정 문제가 경제 운영을 멈추지 않게 함.

## 3. 온보딩 단순화
공식 가이드의 흐름은:
1. 화폐 이름
2. 직업
3. 급여와 Payday
4. 상점
5. 보너스/차감
6. 저축
7. 학급에 도입

또한 roster는 CSV/Excel/붙여넣기로 처리한다.

Class Money는 초기 설정에서 학생 입력을 가장 먼저 자동화해야 한다.

## 4. 정보계층
공식 홈페이지가 제시하는 학생 경험:
Earn / Spend / Save

이 세 동사가 매우 강하다.

Class Money 학생 홈 역시 기능명보다 행동언어를 쓸 수 있다.
- 벌기
- 쓰기
- 모으기
- 내역 보기

## 5. Before/After 구매 UI
공개 예시에서:
Current Balance
Cost
New Balance

를 구매 전 함께 보여준다.

이는 초등학생에게 매우 적합하다.

Class Money는 여기에 목표 영향까지 추가할 수 있다.
현재 24.50 → 비용 20 → 남음 4.50 → 목표 달성은 1주 늦어짐

## 6. Goal UI
공식 예시는 목표명, 현재금액/목표금액, 남은금액을 함께 보여준다.

좋은 점:
- 숫자만 보여주지 않음.
- 무엇을 위해 모으는지 먼저 보임.
- 남은 금액을 자연어로 설명.

## 7. 로그인 카드 UX
학생 이메일 없이 인쇄 가능한 로그인 카드 제공.
사용자명+비밀번호는 혼동하기 쉬운 글자를 구분하기 쉬운 서체로 출력한다고 설명한다.

Class Money에서 가져올 것:
- 개인 이메일 불필요
- 출력 가능한 카드
- 큰 글자
- QR+문자코드 병행
- 코드 재발급
- 공유기기 학생 전환

## 8. 빠른 지급
Give/Deduct는 학생/Group/전체 대상으로 saved Reason을 사용할 수 있다.

Class Money는 사유 템플릿에 기본금액까지 연결해 한 번에 지급할 수 있게 한다.

## 9. Undo와 Transaction
모든 거래가 기록되고 대량 Give/Deduct도 undo 가능하다.

UX적으로 ‘실수할 수 있다는 전제’를 제품에 넣은 것이다.

Class Money:
지급 직후 snackbar형 Undo + 거래 상세에서 정식 정정 기능을 모두 제공.

## 10. 복잡성을 잘 푼 부분과 남은 문제
잘 푼 부분:
- 학생 로그인 선택
- 붙여넣기 roster
- 반복 급여 자동화
- Earn/Spend/Save의 단순 언어
- Before/After 구매
- 목표 진행률
- 일괄 지급

주의:
- 같은 학생의 Balance가 여러 classroom에서 공유되는 구조는 교실별 경제정책 간섭 가능.
- Leaderboard는 자산 공개 경쟁을 강화할 수 있음.
- 음수 Balance 허용은 초등 기본값으로 부적합.

## 11. Class Money 적용
강하게 채택:
- Teacher-only mode
- Earn/Spend/Save 행동 중심 IA
- Before/After
- 로그인 카드
- saved Reason
- 일괄 지급
- Goal
- Undo

수정:
- Balance는 학급별 격리
- Leaderboard 기본 제외
- 음수 잔액 기본 차단

## 12. Craft Anything 실측 항목
- 교사 홈에서 한 학생/모둠/전체 지급 클릭수
- roster paste 미리보기
- Reward purchase 흐름
- Goal 화면 시각계층
- 로그인 카드 생성/재발급
- 학생 로그인 유무에 따른 교사 흐름 차이
- 폰/태블릿 학생 dashboard
- 거래 Undo 피드백

## 공식 근거
- https://www.classcents.com/
- https://www.classcents.com/guides/how-to-set-up-a-classroom-economy
