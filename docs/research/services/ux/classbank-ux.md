# ClassBank — 복잡성·정보구조·UI·UX 심층 분석

기준일: 2026-11-08  
증거 수준: 공식 Help/가이드 중심. 실제 로그인 후 전체 UI 실측 전.

## 1. 복잡성의 원천
Jobs는 급여를 만들고, Bills는 정기지출을 만들며, Store는 소비를 만들고, Savings/Interest는 장기 목표를 만든다. Bonuses/Fines는 비정기 자금흐름을 만들고 Student Helpers는 일부 교사 기능을 학생에게 위임한다.

처음부터 모두 설정하면 교사는 경제 설계자 역할까지 맡아야 한다.

## 2. 핵심 해법: Progressive Disclosure
공식 시작 가이드는 먼저 Class → Students → Bonuses → Store를 만들고, Jobs → Bills → Savings/Interest → Co-teacher를 필요할 때 추가한다.

즉 기능의 존재와 기능의 노출 시점을 분리한다.

## 3. UI/UX 의미
### 첫 거래를 먼저 만들기
학생을 넣고 돈을 줄 방법과 쓸 곳 하나를 만든다. 경제 전체를 설계하기 전에 첫 성공 경험을 만든다.

### 고급 기능 지연 노출
자동급여, 정기지출, 저축은 기본 루프가 작동한 뒤 추가.

### Student Helper 전용 접근
Banker, HR, Store Clerk에게 특정 플랫폼 영역만 준다. 역할 기반 정보구조의 좋은 사례다.

## 4. Class Money 온보딩 번역
1단계: 반 이름 / 화폐명 / 학생 붙여넣기  
2단계: 돈을 어떻게 줄지 선택  
3단계: 쓸 곳 하나 만들기  
완료 후: 직업 / 저축 / 정기지출 / 세금 확장 카드 표시

## 5. 경제 설정 UX
고정 추천값 대신 관계를 보여준다.

예:
주간 소득 100  
정기지출 70  
남는 돈 30  
대표 상품 120  
현재 설정이면 약 4주 필요

정책을 저장하기 전에 경제 결과를 미리 보여주는 것이 핵심이다.

## 6. Student Helper의 UI 복잡성
학생이 일반 학생이면서 Banker일 수 있다. 따라서 학생 홈과 운영업무를 분리해야 한다.

권고:
학생 홈에 내 운영업무 카드만 추가하고 전체 관리자 메뉴는 보여주지 않는다.

## 7. 실제 공식 흐름에서 확인되는 UX
- Student Helpers 탭에서 역할별 학생을 직접 선택.
- Jobs 탭에서 지원서/이력서를 보고 채용 또는 거절.
- 직업에 학생을 직접 drag하여 채용 가능.
- Store 탭의 Store Transactions에서 대기 구매를 검색하고 체크로 완료, X로 취소/환불.
- All Transactions에서 Student Helper가 보낸 거래만 필터 가능.

이는 복잡한 운영을 역할별 탭과 검색/필터로 푸는 방식이다.

## 8. UX 위험
- 기능별 탭이 계속 늘면 교사가 요청을 찾아다니게 됨.
- Student Helper 권한과 직업을 혼동할 수 있음.
- 미국식 금액 가이드를 무비판적으로 적용할 위험.
- Bonuses/Fines가 경제의 중심처럼 보일 수 있음.

## 9. Class Money 개선안
설정은 기능별로 두되 운영은 통합 Inbox로 합친다.

Inbox 예:
상점 승인 / 직업 지원 / 학생 보조자 거래검토 / 실패 급여

검색과 필터는 각 기능 화면보다 Inbox와 전체 거래장부에서 강하게 제공한다.

## 10. Craft Anything 실측 항목
- 첫 설정 화면 수
- 학생 25명 등록 방식
- Student Helper 메뉴 범위
- Job 지원/채용 단계 수
- Store 승인/취소 클릭 수
- 전체 거래 검색/필터
- 기능 활성화 전후 메뉴 변화
- 태블릿에서 설정 폼 밀도

## 공식 근거
- https://help.classbank.com/en/articles/6499058-how-do-i-get-started-with-classbank
- https://help.classbank.com/en/articles/5949828-student-helper-jobs-banker-hr-manager-and-store-clerk
- https://help.classbank.com/en/articles/9745965-how-to-train-student-bankers
