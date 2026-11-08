# ClassCents 심층 분석

기준일: 2026-11-08  
분석 유형: 공식 홈페이지 공개 설명 기반  
실측 상태: 로그인 후 UI 미측정

## 1. 왜 분석하는가

ClassCents는 ‘교실경제를 얼마나 정교하게 만들 수 있는가’보다 ‘교사가 얼마나 적은 준비와 조작으로 운영할 수 있는가’를 분석하기 좋은 사례다.

Class Money가 실제 학교에서 쓰이려면 기능보다 운영 마찰을 먼저 줄여야 한다.

## 2. 제품 정체성

공식 설명:
- 화폐 이름과 기호 설정
- 포인트 정수 모드
- CSV/Excel/붙여넣기 학생 등록
- Jobs
- Payday
- Shop/Rewards
- Give/Deduct
- Group/Whole Class
- Transaction history
- Undo
- CSV export
- 학생 로그인 선택
- Savings/Goals
- Badges
- Leaderboard

무료 교사용 교실경제 도구로 포지셔닝한다.

## 3. 가장 중요한 특징: 학생 로그인 없이도 운영 가능

교사가 자신의 화면만으로:
- 직업
- 급여
- 지급/차감
- 상품 사용
을 운영할 수 있다.

학생 계정은 선택 사항이다.

이 패턴은 초등학교에서 매우 강력하다.

현실:
- 모든 학생이 이메일 계정을 쓰기 어려울 수 있음.
- 공유 태블릿 환경이 많음.
- 수업 중 로그인 문제 하나가 전체 활동을 멈출 수 있음.

Class Money:
‘Teacher-only mode’를 정식 운영 모드로 제공할 가치가 크다.

학생 디지털 참여는 추가 단계가 되어야 한다.

## 4. 학생 등록

CSV, Excel, spreadsheet paste를 지원한다고 공개한다.

Class Money에서 가장 필요한 등록 UX:
- 번호+별칭 여러 줄 붙여넣기
- 미리보기
- 중복 학생번호 표시
- 기존 학생과 병합/건너뛰기
- 학기 이관

25명 등록은 폼 25번 입력이 되어서는 안 된다.

## 5. Payday 자동화

직업별로 daily/weekly/monthly 자동 지급.

또한 학생이 Job done을 표시해야 지급되도록 설정할 수 있다.

이 기능은 ‘시간 기반 자동급여’와 ‘완료 검증 기반 급여’를 동시에 보여준다.

Class Money:
급여 규칙의 지급조건:
- 무조건
- 학생 완료 제출
- 교사 승인
- 담당 학생 승인 + 교사 감사

각 직업별 선택.

## 6. 즉시 지급 UX

Give/Deduct:
- 한 학생
- Group
- 전체
- 저장된 Reason

이 조합은 수업 중 업무를 크게 줄인다.

Class Money의 수업 중 지급 패널:
학생 범위 → 저장 사유 → 금액 → 실행.

금액 입력보다 사유 템플릿이 먼저 선택되는 설계도 고려할 수 있다. 왜 돈이 움직였는지가 장부에 항상 남게 하기 위해서다.

## 7. Undo와 기록

모든 Transaction을 기록하며 일괄 Give/Deduct도 되돌릴 수 있다고 설명한다.

핵심:
오류 수정이 예외 기능이 아니라 주요 사용 흐름이다.

Class Money:
- 최근 거래 직후 Undo
- 오래된 거래는 상세→정정
- 원 거래와 역거래 연결
- 학생에게도 정정이 표시됨

## 8. 학생 개인정보와 인증

학생 이메일 불필요.
교사가 학생을 추가하고 Login card의 username/password를 생성한다.

좋은 점:
- 개인 이메일 수집 최소화.
- 교사가 계정 생성을 통제.
- 공유 기기 접근 가능.

Class Money 개선점:
- 출력 가능한 개인 코드/PIN
- 코드 재발급
- 자동 세션 종료
- 학생 바꾸기
- 로그인 카드 분실시 폐기

## 9. 하나의 Balance가 여러 Classroom에 공유되는 구조

공식 설명에서 같은 학생은 여러 교실에 들어가도 하나의 Balance를 유지한다고 한다. Jobs, Rewards, Badges는 교실별이다.

이것은 Class Money가 그대로 따르면 안 되는 중요한 차이다.

장점:
- 학교 전체 단일 화폐를 만들기 쉬움.
- 학생이 교과별로 돈을 모을 수 있음.

위험:
- 다른 교사가 만든 경제정책이 서로 간섭.
- 한 반에서 발생한 보상이 다른 반의 구매력에 영향.
- 학년 변경과 계정 병합이 복잡.
- 학교 전체 경제를 원치 않는 교사에게 예상 밖 동작.

Class Money 기본:
학급별 지갑 완전 분리.

확장 기능:
학교 공용 지갑을 명시적으로 연결.

## 10. Leaderboard에 대한 비판

ClassCents는 class leaderboard를 기능으로 공개한다.

Class Money에서는 기본 제외 권고.

이유:
- 잔액은 직업, 결석, 역할, 교사 보너스 등 많은 요인의 결과.
- 잔액순위를 능력/성실 순위로 오해할 수 있음.
- 경제적 실패를 공개적으로 드러냄.

대안:
개인 순위 대신 학급 공동 목표, 개인 목표 진행률.

## 11. 마이너스 잔액

공식 예시에 음수 Balance가 등장한다.

Class Money에서는 마이너스가 기본적으로 허용되면 안 된다.

P0:
결제 → 잔액 부족 거절.

P2 부채 시뮬레이션:
별도 debt account와 한도로 명시.

## 12. Class Money에 가져올 것

강하게:
1. 교사 단독 운영 모드
2. 붙여넣기/CSV 등록
3. 자동 Payday
4. 완료 검증형 급여
5. 그룹/전체 빠른 지급
6. Reason 템플릿
7. Undo
8. 학생 이메일 없는 계정
9. CSV export

변형:
- Savings/Goals → 학습 중심 UI 강화
- Badges → 경제 이정표
- 학교 공용화폐 → 별도 명시적 모드

제외:
- 공개 잔액 leaderboard 기본값
- 여러 반 지갑 자동 공유
- 일반 지갑의 무제한 마이너스

## 13. Craft Anything 후속 실측

- 25명 붙여넣기 등록
- 학생 로그인 카드 생성/재발급
- 한 학생/모둠/전체 지급 실제 클릭수
- 저장 Reason 재사용 방식
- Payday 설정
- Job done 검증
- Undo 후 학생 내역 표시
- Reward redemption
- Teacher-only와 Student login 모드 차이
- 여러 class에 동일 학생 등록할 때 Balance 병합 동작

## 14. 현재 판단

ClassCents는 Class Money의 ‘제품 운영성’ 벤치마크다.

Class Money가 아무리 교육적으로 뛰어나도 교사가 매일 학생 25명을 개별 선택하고 로그인 문제를 해결해야 한다면 지속 사용되지 않는다.

따라서 ClassCents에서 가장 강하게 가져와야 할 것은:
‘학생이 앱을 쓰지 않아도 경제는 돌아가며, 학생이 앱에 들어오면 더 깊은 학습이 가능하다’는 이중 구조다.

## 공식 근거
- https://www.classcents.com/


## 심화 보완: 12개 분석축

### A. 사용자와 권한
ClassCents의 가장 중요한 권한 선택은 학생 로그인이 없어도 경제가 완전히 돌아간다는 점이다.

Class Money는 세 모드를 지원하는 것이 좋다.
- Teacher-only
- Shared-device student
- Personal student login

기능의 핵심이 학생 계정 존재에 종속되지 않아야 한다.

### B. 핵심 상태
직업:
배정 → 수행확인 선택 → Payday → 자동지급

보상:
교사 Give/Deduct → 원장기록 → 필요시 Undo

Reward:
활성 → 학생 선택/교사 대리 → redeem

Savings:
지갑 → savings/goal 이동

각 상태를 단순 balance 조작이 아니라 거래객체로 남기는 것이 중요하다.

### C. 교사 JTBD
- roster를 빠르게 넣기
- 반복급여를 잊지 않기
- 수업 중 빠르게 지급
- 로그인 문제 없이 운영
- 실수를 되돌리기
- 학기말 데이터를 export

이 여섯 개는 Class Money MVP 성공기준으로 직접 사용할 수 있다.

### D. 학생 JTBD
학생이 로그인한다면:
- 현재 Balance
- Job
- Shop
- Savings/Goal
- Transactions
를 단순하게 본다.

로그인하지 않는 학생도 경제에서 소외되지 않아야 한다.

### E. 여러 학급 Balance 공유
ClassCents는 동일 학생의 balance가 여러 classroom에서 공유된다고 설명한다.

Class Money에서는 기본적으로 이 정책을 채택하지 않는다. 이유:
- 담임반 경제와 교과전담 경제가 서로 다른 규칙일 수 있음
- 한 반의 인플레이션이 다른 반에 전이
- 거래책임 소재 불명확

학교 전체 공용화폐를 만들 때만 명시적으로 wallet scope를 school로 확장한다.

### F. 마이너스 잔액
공식 예시에 음수 balance가 보인다.

Class Money:
- 일반 wallet은 0 미만 금지
- debt 모듈만 별도 부채계정
- insufficient funds를 명시적으로 표시

이것이 초등 사용자에게 더 명료하다.

### G. Reason 중심 거래
저장된 Reason으로 Give/Deduct하는 구조는 수업 중 매우 유용하다.

Class Money는 금액 프리셋보다 '사유+금액' 템플릿을 저장하는 편이 낫다.

예:
도서정리 완료 +10
주간 직업급여 +50
특별 프로젝트 +20

교사는 나중에 사유별 통계도 볼 수 있다.

### H. 자동급여의 조건
Job done을 먼저 표시해야 급여를 받게 할 수 있는 점은 직업 모델을 유연하게 만든다.

Class Money 직업 지급방식:
- unconditional scheduled
- student check + auto
- teacher approval
세 종류가 적절하다.

### I. 개인정보와 공유기기
인쇄 로그인 카드와 이메일 없는 계정은 학교환경에 매우 적합하다.

추가 요구:
- 카드 분실 시 즉시 재발급
- 기존 credential 폐기
- 공유기기 자동로그아웃
- 학생 전환버튼
- 화면에 비밀번호 장시간 노출 금지

### J. 교육적 깊이 보완
ClassCents의 운영 UX는 간결하지만 Class Money는 여기에:
- 거래 전/후 잔액
- 저축 기회비용
- 주간 회고
- 경제 밸런스
를 더해 교육적 차별화를 만들 수 있다.

### K. 제품결정
Adopt:
- teacher-only
- roster paste/import
- login cards
- automatic payday
- group/whole-class give
- reason template
- undo/export

Adapt:
- goals
- leaderboard
- multi-class identity

Avoid:
- 자동 지갑통합
- 공개자산순위
- 일반지갑 음수 허용

### L. 남은 실측
- 25명 roster import 시간
- login card 재발급
- payday 실패
- job done 조건
- group 지급 실제 단계
- undo의 감사로그
- student login 없는 상태에서 reward 전달
- 공용기기 세션

## V4 심층 해부 — 지속 가능한 교사 운영의 최소조건

### 1. ClassCents의 가장 중요한 제품 지표는 기능수가 아니라 유지비용이다

공식 가이드는 초기 설정을 한 prep period 안에 하고, 익숙해진 뒤 classroom economy가 하루 약 5분 정도의 운영으로 가능하다고 설명한다.

이 수치가 모든 교실에 그대로 적용된다는 뜻은 아니지만, ClassCents가 제품 문제를 ‘교사의 운영시간’으로 정의한다는 점이 중요하다.

Class Money도 기능별 성공조건을 시간으로 가져야 한다.

제품 목표 예:
- 25명 등록 3분
- 전체 지급 10초
- 개인 오지급 정정 15초
- 10개 주문 승인 30초
- 직업 5개 일괄배정 2분

실제 사용자테스트 후 숫자를 조정한다.

### 2. Teacher-only는 축소판이 아니라 완전한 운영모드다

학생 로그인 없이도 Jobs, Payday, Give/Deduct, Reward redemption이 작동한다는 것은 학교 환경에서 매우 큰 장점이다.

Class Money는 학생앱이 없어도 다음이 모두 가능해야 한다.
- 급여
- 직업
- 상점 구매 대리
- 저축 대리
- 거래내역
- 출력

학생 로그인은 자율성/학습깊이를 늘리는 옵션이어야 한다.

이 구조가 필요한 현실적 이유:
- 1:1 기기 없음
- 비밀번호 문제
- 저학년 타이핑
- 공용 태블릿
- 수업시간 부족

### 3. Currency precision은 학년별 난도 조절 기능이다

ClassCents는 whole-number points와 dollars/cents를 선택하게 한다.

Class Money에서는 currency precision을 교육적 설정으로 다룬다.

1~2학년:
정수

3~4학년:
정수 기본, 필요시 10단위/100단위

5~6학년:
소수 화폐 선택 가능

기술적으로는 내부 원장을 정수 최소단위로 유지해 부동소수점 오류를 피한다.

### 4. 상점 가격은 급여와 상대적으로 설계되어야 한다

ClassCents 공식 가이드는:
- small reward 약 하루 급여
- medium 약 주급
- large 약 3~4주 급여
처럼 가격을 급여와 관계지어 설명한다.

이 패턴이 Class Money 설정 마법사의 핵심이 될 수 있다.

교사가 상품가격을 입력하면 앱이:
‘이 상품은 평균 주급의 4.8배입니다. 목표저축용 장기상품으로 적합합니다.’
처럼 설명할 수 있다.

가격의 절대값보다 경제 안에서의 시간비용이 더 중요하다.

### 5. Jobs는 교실 운영 자동화와 경제교육을 동시에 해결한다

공식 가이드는 실제 필요한 교실업무를 직업으로 만들라고 권장한다.

이것은 중요한 기준이다.

나쁜 직업:
이름만 멋있고 실제 일이 없음

좋은 직업:
- 기기 정리
- 도서 관리
- 준비물 관리
- 전달
같이 실제 학급 운영을 돕는다.

Class Money 직업 추천기는 학년뿐 아니라 교실 실무 카테고리로 추천하는 것이 좋다.

### 6. Deductions에 대한 제품 철학

ClassCents 가이드는 deduction/fine은 선택이며 드물고 작게 쓰는 것이 좋다고 명시한다.

Class Money도 이 철학을 제품 기본값으로 강제할 수 있다.

- Fine 기능 기본 OFF
- 처음 켤 때 교육적 주의 안내
- 월간 차감상한
- 학생별 과도한 차감 경고
- 교사에게 벌금보다 보상 중심 권고

단순 가이드 문구보다 제품 기본값이 더 강력한 정책이다.

### 7. 한 Balance를 여러 Classroom이 공유하는 설계의 장단점

ClassCents는 학생이 여러 반에 있어도 하나의 Balance를 공유한다.

장점:
- 학생 입장에서는 하나의 화폐
- 교사 간 연결된 학교경제 가능

단점:
- 서로 다른 반 규칙이 같은 지갑에 영향
- 어느 교사가 만든 인플레이션인지 추적 어려움
- 학급 간 가격체계 충돌

Class Money 기본:
wallet scope = classroom

추후 school economy에서만:
wallet scope = school
을 명시적으로 선택.

### 8. 로그인카드의 세부 UX가 중요하다

ClassCents는 학생 ID를 이메일 대신 인쇄 카드로 주고, 서로 헷갈리는 글자가 적은 글꼴을 사용한다고 설명한다.

Class Money에서 가져올 세부사항:
- 사람이 읽기 쉬운 두 단어 + 숫자 형태
- 1/l/I, O/0 혼동 최소화
- QR은 보조수단
- 카드 재발급 즉시 이전 credential 폐기
- 로그인 후 학생 바꾸기 버튼 크게 제공

### 9. 최종 판단

ClassCents는 Class Money의 ‘운영성 기준점’이다.

다른 서비스의 금융기능을 도입하더라도 아래를 깨면 안 된다.
- 교사단독 운영 가능
- 자동급여
- 빠른 일괄지급
- undo
- 이메일 없는 학생접근
- 단순한 상점
- 거래 export

Class Money의 고급 기능은 이 최소 운영성을 훼손하지 않는 방식으로만 추가해야 한다.

추가 근거:
- https://www.classcents.com/
- https://www.classcents.com/guides/how-to-set-up-a-classroom-economy