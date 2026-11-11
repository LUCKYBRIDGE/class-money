# 반짝 모의투자 — 파일·폴더·기술 구조

기준일: 2026-11-11

**증거 수준:** C+  
현재 제품 전체 repository/source는 공개되지 않았으나, 실제 URL과 공개 개발기록에서 **일부 실제 파일명·폴더명·초기 DB 설계**를 확인할 수 있다.

## 1. 확인된 실제 공개 경로

현재 직접 확인:

```text
/API/stock/
├─ ad.html                 # 현재 제품 소개/landing
├─ index.php               # Teacher / Student 역할 선택 landing
├─ teacher_login.php       # 현재 Teacher CTA
└─ student_login.html      # 현재 Student CTA
```

2026-04-06 개발기에서 추가 확인된 당시 파일:

```text
/API/stock/
├─ admin.html
├─ student.html            # 당시 글에는 아직 만들기 전이라고 명시
├─ api_update_student.php
└─ api_delete_student.php
```

### 중요
과거 `admin.html`, `student.html`이 현재 production에서도 같은 이름으로 쓰인다고 단정하지 않는다.

## 2. 파일 확장자로 확인 가능한 기술 단서

- `.html` — 정적/클라이언트 페이지 존재
- `.php` — 서버측 PHP endpoint/page 사용이 최소 일부 확인
- `/API/stock/` — 메인 커뮤니티와 별도의 stock module path

현재 전체 framework나 PHP framework 사용 여부는 확인되지 않는다.

## 3. 메인 플랫폼 기술 단서

반짝넷 공개 페이지는 서비스 전체에 대해:
- Rhymix 표준 보안 엔진
- HTTPS
- password one-way hashing
- session management

을 사용한다고 설명한다.

다만 이것이 `/API/stock/`의 모든 custom endpoint 내부 구현에 동일하게 적용되는지는 별도 source가 없어 확정하지 않는다.

## 4. 초기 개발기에서 제안된 DB schema

2026-04-04 “구조 잡기” 게시물에는 다음 DB 초안이 공개돼 있다.

### users

```text
id
name
current_cash
initial_cash
class_code
```

### stocks

```text
stock_code
stock_name
market_type
current_price
is_active
```

### holdings

```text
user_id
stock_code
quantity
avg_price
```

### transactions

```text
user_id
stock_code
type (BUY / SELL)
price
quantity
created_at
```

### 정확도 주의
이 schema는 공개 개발과정의 **초기 설계안**이다. 현재 production DB schema라고 확인된 것은 아니다.

## 5. 현재 기능상 추가로 필요한 logical domain

현재 `ad.html`의 미장/환전/매매일지/시간제어를 설명하려면 초기 schema 외에 최소 다음 개념이 필요하다.

```text
Class
StudentIdentity / AccessCode
CurrencyBalance (KRW, USD)
Stock / Market
Holding
Trade
ExchangeTransaction
FXRateSnapshot
TradeJournal
AccessSchedule
PortfolioValuation
```

이 이름들은 **Class Money 분석용 논리 모델**이며 실제 서비스 DB/table명이 아니다.

## 6. Market Data 구조 — 확인과 미확인

### 초기 개발 제안
2026-04-04 게시물에서는:
- KIS Open API
- Yahoo Finance
를 후보로 검토했다.

### 1차 완성 게시물
2026-04-06 게시물 본문은:
- 네이버 증권과 10초 단위 연동
- 서버 보호를 위해 200개 대표종목
- 교사가 종목 추가 가능

이라고 설명한다.

### 같은 시기의 홍보 이미지
“1초 단위”라는 표현이 있다.

### 현재 2026-11 `ad.html`
- “국장·미장 시세 기반”
- 환전 지원

까지만 직접 확인되며 현재 provider/refresh interval은 공개되지 않는다.

### 결론
현재 기술문서에는:
- Provider = UNKNOWN
- Refresh interval = UNKNOWN
으로 기록하는 것이 정확하다.

## 7. Server-side Price Update

초기 구조글은 서버가 주기적으로 시세를 가져와 `stocks.current_price`를 갱신하는 방식을 제안했다.

브라우저가 외부 시세 API를 직접 호출하면 CORS/키노출 문제가 있어 서버 proxy/update 계층을 두는 설계가 자연스럽다.

다만 현재 production이 동일한 scheduler/cache 구조인지 확인되지 않았다.

## 8. Transaction Consistency 요구

매수:

```text
cash sufficient?
→ cash debit
→ holding quantity increase
→ avg price update
→ trade log
```

매도:

```text
holding sufficient?
→ holding decrease
→ cash credit
→ trade log
```

현재 KRW/USD가 있으므로 미국주식 거래는 통화까지 포함한 atomic operation이 필요하다.

### Class Money에서 반드시 고려할 것
- DB transaction
- double submit protection
- idempotency key
- stale price handling
- exchange-rate snapshot
- valuation timestamp
- reversal/correction policy

## 9. QR / Access Code 구조

개발기에서:
- 학생별 QR
- 개별 QR 인쇄
- 학생 이름 수정
- 학생 삭제
- 학생 계정으로 바로 입장

flow가 확인된다.

현재 landing도 학생별 코드 또는 QR을 공식 onboarding으로 설명한다.

### 기술적 의미
학생에게 이메일 계정을 요구하는 대신:
Teacher-created student identity
→ access token/code
→ QR representation
구조로 보는 것이 적합하다.

실제 token format/session policy는 미확인.

## 10. 현재 기능 기준 logical module tree

```text
stock/
├─ landing/
├─ teacher-auth/
├─ student-access/
├─ classroom/
├─ students/
├─ market-data/
│  ├─ kr-market/
│  ├─ us-market/
│  └─ fx/
├─ trading/
│  ├─ buy/
│  ├─ sell/
│  └─ validation/
├─ portfolio/
├─ exchange/
├─ trade-journal/
├─ ranking/
├─ teacher-dashboard/
├─ access-schedule/
└─ reports/
```

이 tree는 **실제 source tree가 아니라 현재 제품을 설명하기 위한 logical architecture**다.

## 11. 공개 repository

이 조사에서 반짝 모의투자 본체의 공식 public GitHub repository는 확인하지 못했다.

따라서:
- framework
- DB engine
- source folder
- deployment
- market-data provider
를 추정하지 않는다.

## 12. Class Money 기술대응

반짝 모의투자의 구조는 Class Money의 core wallet 안으로 직접 넣기보다:

```text
simulation/
└─ market/
   ├─ virtual-account/
   ├─ quote-provider/
   ├─ fx/
   ├─ orders/
   ├─ holdings/
   ├─ portfolio/
   ├─ journal/
   └─ teacher-controls/
```

처럼 별도 bounded context로 두는 편이 안전하다.
