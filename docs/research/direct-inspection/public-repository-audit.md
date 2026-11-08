# 경쟁 서비스 공개 GitHub 저장소 감사

기준일: 2026-11-08
방법: GitHub repository 검색, 공식 organization 확인, repository metadata/tree/file 직접 확인.

## 1. 핵심 결론

상용 교실경제 서비스 대부분은 현재 제품 본체의 소스를 공개 GitHub repository로 제공하지 않는다.

따라서 서비스명과 같은 동명 repository를 발견했다는 이유만으로 현재 상용제품의 내부구조 근거로 사용하면 안 된다.

## 2. 서비스별 판정

| 서비스 | 공식 공개 제품 소스 | 직접 확인 결과 |
|---|---|---|
| ClassCoin | 확인 못함 | classcoin 검색 결과는 여러 개인/학생 프로젝트. classcoin.me 공식 제품 source로 확인되지 않음 |
| ClassBank | 확인 못함 | classroom economy 제품 source repository를 확인하지 못함 |
| Cashroom | 확인 못함 | 현재 제품 source repository를 확인하지 못함 |
| ClassCents | 확인 못함 | 현재 제품 source repository를 확인하지 못함 |
| Banqer | 제품 본체는 확인 못함 | 공식 Banqer organization은 존재하나 공개 repos는 interview sample/UI fork 등으로 현재 Primary source 근거가 아님 |
| My Classroom Economy | 확인 못함 | 검색되는 MCE repositories를 공식 제품 source로 확인할 근거 없음 |
| ClassDojo | 제품 본체는 확인 못함 | 공식 classdojo organization에 공개 infra/library/policy repos가 있으나 현재 Points app source는 아님 |
| Greenlight | 제품 본체는 확인 못함 | official-name organization에서 제품 source를 확인하지 못함 |
| Rooster Money | 확인 못함 | 검색 결과는 제3자 integration 또는 비공식 프로젝트 중심 |
| YNAB | 공식 API SDK 공개 | ynab/ynab-sdk-js와 ynab/ynab-api-starter-kit이 현재 관리됨 |
| Toss | 이번 감사에서 공식 product source 확인 못함 | 실제 제품 구조 판단은 공식 사이트/도움말 관찰로 제한 |

## 3. Banqer 공식 GitHub 직접 확인

공식 organization: github.com/Banqer

확인한 공개 repositories:
- Banqer/angular_sample — description: Angular code to look at in interviews; pushed 2022-02-18
- Banqer/ui-select-banqer — Angular 1.5용 ui-select working version hard copy; pushed 2016-09-27
- 그 외 garden_planner, kibana-presenter 등

### 판정

이 자료는 Banqer 조직의 과거 기술 흔적 또는 보조 자료로 볼 수는 있지만, 현재 Banqer Primary frontend architecture의 증거가 아니다.

따라서 'Banqer가 현재 Angular 1.5로 구현되어 있다' 같은 결론은 내리지 않는다.

## 4. ClassDojo 공식 GitHub 직접 확인

공식 organization: github.com/classdojo

공개 repositories에는:
- photo-collage
- rabbitmq-queue-stream
- mongo-to-s3
- agenda
- database
- policies
- 여러 utility/library
가 존재한다.

classdojo/policies는 최근까지 관리 흔적이 있으나 정책 source이고 현재 Points UI source가 아니다.

### 판정

공식 organization이라는 사실만으로 공개 library의 구조를 현재 ClassDojo web/app 구조로 역추론하지 않는다.

## 5. YNAB 공식 공개 SDK는 실제 도메인 구조 분석에 유효

직접 확인:
- repository: ynab/ynab-sdk-js
- description: Official JavaScript client for the YNAB API
- 2026-11-05 push 확인

공개 API의 주요 영역:
- Plans
- Accounts
- Categories
- Payees
- Months
- Money Movements
- Transactions
- Scheduled Transactions

### Category model에서 직접 확인

Category에는 다음이 명시돼 있다.
- category_group
- budgeted
- activity
- balance
- goal_type
- goal_target
- goal_target_date
- goal_percentage_complete
- goal_under_funded
- goal_overall_funded
- goal_overall_left

이는 YNAB UI의 Assigned / Activity / Available / Target / Underfunded가 단순한 marketing 표현만이 아니라 공개 domain model과 강하게 연결돼 있음을 보여준다.

### Transaction model

TransactionDetail에는:
- date
- amount
- memo
- cleared
- approved
- account
- payee
- category
- transfer account/transaction pair
- matched transaction
- debt transaction type
- subtransactions
가 존재한다.

즉 transaction은 단순 금액 row가 아니라 **account + payee + category + transfer + matching + approval 상태**를 가진다.

### MoneyMovement model

별도 MoneyMovement에는:
- from_category_id
- to_category_id
- amount
- performed_by_user_id
- moved_at
- movement group
이 있다.

중요한 점은 **실제 account transaction과 예산 목적 간 money movement를 별도 개념으로 모델링한다는 것**이다.

## 6. Class Money에 주는 아키텍처 교훈

YNAB 공개 API에서 확인되는 설계 원리:

1. 돈의 실제 위치와 돈의 목적을 분리한다.
2. Goal은 progress bar가 아니라 domain data다.
3. 목적 간 배분 이동은 일반 transaction과 구분할 수 있다.
4. Scheduled transaction은 실제 transaction과 별도 객체다.
5. approval/cleared 같은 상태는 명시적 필드다.

Class Money로 번역하면:
- Account
- Allocation / Goal
- Transaction
- Allocation Movement
- Schedule Rule
을 분리하는 방향이 더 안정적이다.

## 7. 이후 repository 조사 원칙

공식 source라고 판단하려면 최소한 다음을 확인한다.
- 공식 회사/서비스 organization인가
- 서비스 홈페이지/공식 문서에서 연결되는가
- repository description이 제품과 직접 연결되는가
- 최근 activity가 있는가
- README가 현재 제품과 직접 연결되는가

조건이 부족하면 '동명 repository가 존재함'으로만 기록하고 제품 기술근거에서는 제외한다.