# 반짝 모의투자 — 기능·흐름·상태

기준일: 2026-11-11

## 1. 핵심 기능

### 교사
- 반 만들기
- 학생 일괄등록
- 초기 자금 설정
- 거래 가능 종목 관리
- 학생별 코드/QR 배포
- 학생 접속 가능 시간 설정
- 학생 투자현황 확인
- 학급 수익률/포트폴리오 분석

### 학생
- 코드/QR 입장
- 국장/미장 선택
- 종목 검색/탐색
- 원화/달러 환전
- 매수
- 매도
- 포트폴리오 확인
- 수익률 확인
- 랭킹 확인
- 매매일지 작성

## 2. 교사 Setup Flow

```text
Teacher Login
→ Class Create
→ Student Register
→ Initial Cash Set
→ Tradable Universe Set
→ Access Time Set
→ QR / Code Distribute
→ Class Open
```

초기 개발기에는 “학생 등록 → 초기자산 → 종목범위”가 핵심 관리자 기능으로 제안됐고, 현재 소개 페이지에는 여기에 접속시간 통제가 추가돼 있다.

## 3. 학생 Login Flow

```text
QR Scan / Student Code
→ Student Identity Resolve
→ Class Access Rule Check
→ Student Trading Home
```

별도 학생회원가입을 없애 수업 시작 시간을 줄인다.

## 4. 국내주식 거래 Flow

```text
거래소
→ 국장 선택
→ 종목 검색
→ 종목 상세
→ 차트/가격/호가 확인
→ 수량 설정
→ 매수/매도
→ 현금/보유수량 변경
→ 거래기록
→ 포트폴리오
→ 매매일지/회고
```

## 5. 미국주식 Flow

```text
보유 KRW
→ 환전
→ 보유 USD
→ 미장 선택
→ 미국 종목 탐색
→ USD 가격으로 매수
→ USD/주식 포트폴리오
→ 필요 시 USD→KRW 환전
```

이 흐름은 **통화계정과 시장계정의 분리**를 요구한다.

## 6. 환전 Flow

권장 상태모델로 해석하면:

```text
환율 조회
→ KRW→USD 또는 USD→KRW 선택
→ 금액 입력
→ 적용 환율 / 예상 결과 확인
→ 환전 실행
→ 두 통화 balance 변경
→ FX transaction 기록
```

현재 내부 구현은 비공개이므로 실제 DB transaction 구조는 확인하지 못했다.

## 7. Portfolio

현재 marketing에서 확인:
- 현금
- 원화
- 달러
- 종목
- 보유수량
- 평균 매입가
- 종목별 수익률
- 총/학급 수익률

### 중요한 계산
국장과 미장을 함께 합산하려면:
USD 자산을 특정 기준환율로 KRW 환산해야 한다.

따라서 Dashboard 수익률에는:
- valuation currency
- applied FX rate
- valuation timestamp
가 명시돼야 정확하다.

현재 공개 페이지에서는 이 계산정책까지 확인되지 않았다.

## 8. Trade Journal / Reflection Loop

```text
정보 탐색
→ 종목 선택
→ 판단 이유 기록
→ 거래
→ 가격 변화
→ 결과 확인
→ 매매일지 회고
→ 학급 토론
```

서비스가 “주식게임”에 머무르지 않게 만드는 핵심 학습루프다.

## 9. Teacher Review Flow

```text
학생 활동
→ Teacher Dashboard Aggregate
→ 학생/종목/수익률 관찰
→ 매매일지 비교
→ 왜 선택했는가 질문
→ 위험/수익/정보 신뢰 토론
```

## 10. 주요 상태

### Student Access
- CLOSED / OUTSIDE_ALLOWED_TIME
- OPEN
- LOGGED_IN

### Market
- KR
- US

### Currency
- KRW
- USD

### Order — 외부기능상 최소 필요
- prepared
- validated
- executed
- rejected

실제 주문 상태 구현은 확인하지 못했다.

### Holding
- no position
- holding
- partially sold
- closed

### Journal
- none
- written
- reviewed

## 11. 초기 설계와 현재 확장 비교

### 2026-04 초기
- KOSPI/KOSDAQ
- 가상 원화
- holdings
- buy/sell
- class ranking

### 현재 2026-11 공개페이지
- 국장 + 미장
- KRW + USD
- 환전
- 매매일지
- 교사 접속시간 제어
- 학생별 코드/QR
- 학급 분석

기능 증가로 인해 단순 `users/stocks/holdings/transactions`만으로는 현재 제품 전체를 설명하기 어렵다.
