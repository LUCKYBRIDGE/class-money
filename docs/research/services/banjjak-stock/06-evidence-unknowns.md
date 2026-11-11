# 반짝 모의투자 — 근거·미확인

기준일: 2026-11-11

## 1. 직접 관찰한 현재 페이지

### 현재 소개
- https://sub-teacher.com/API/stock/ad.html

브라우저에서 현재 페이지 전체 텍스트 구조를 직접 확인.

### 역할 선택
- https://sub-teacher.com/API/stock/index.php

공개 crawler에서도 Teacher / Student 두 CTA를 직접 확인.

### 현재 소개 페이지에서 링크되는 인증
- https://sub-teacher.com/API/stock/teacher_login.php
- https://sub-teacher.com/API/stock/student_login.html

페이지 URL은 현재 landing의 실제 href에서 확인했으나, 이 조사에서는 로그인 이후 내부화면까지 직접 조작하지 않았다.

## 2. 공개 개발기록

### 시작하기
- https://sub-teacher.com/board7/55396

초기:
- 국내시장
- 실제 시세 API 후보
- 학생 포트폴리오
- buy/sell
- 랭킹
아이디어 확인.

### 구조 잡기
- https://sub-teacher.com/board7/55407

초기 설계안:
- users
- stocks
- holdings
- transactions
table 구조와 buy/sell logic 확인.

### QR 로그인
- https://sub-teacher.com/board7/55570

당시 실제/계획 file:
- /API/stock/admin.html
- /API/stock/student.html
- api_update_student.php
- api_delete_student.php

학생 관리 row:
- 입장
- QR/인쇄
- 수정
- 삭제

### 1차 완성
- https://sub-teacher.com/board7/56145

본문에서:
- 실제 서비스 index.php
- 네이버 증권과 10초 단위 연동
- 200개 대표종목
- 교사 종목추가
- 실제 학생화면 screenshot
확인.

## 3. 공개 시각자료에서 확인

2026-04-06 슬라이드:
- 실제시장 유사 거래화면
- QR Login
- Teacher Dashboard
- 수업 45분 Flow
- 1초 단위 시장 데이터 표현

실제 학생화면 screenshot:
- 삼성전자 매수 modal
- 일봉 차트
- 호가창
- 수량 - / +

## 4. 현재 `ad.html`에서 확인한 최신 확장

- 국장 + 미장
- KRW + USD
- 원화·달러 환전
- portfolio
- ranking
- trade journal
- teacher dashboard
- student account code/QR
- access time
- multi-device web
- 실제 돈이 아닌 교육용 simulation

## 5. 자료 간 충돌/주의

### 시세 갱신주기
- 홍보 slide: 1초 단위
- 1차 완성 게시물: 네이버 증권 10초 단위
- 현재 landing: 구체 주기 없음

따라서 현재값 = UNKNOWN.

### 시세 Provider
- 초기 제안: KIS / Yahoo
- 1차 완성: Naver Securities
- 현재: provider 비공개

따라서 현재 provider = UNKNOWN.

### DB Schema
초기 개발기 schema는 설계안이며 production schema로 검증되지 않음.

## 6. 현재 미확인

- Teacher login 이후 실제 Dashboard IA
- Student login 이후 현재 production 화면 전체
- 현재 buy/sell validation
- 거래 fee/slippage 여부
- 실제 quote provider
- refresh interval
- US market symbol universe
- 환율 provider
- 환전 spread/rounding policy
- 장 운영시간/장마감 처리
- 시장 휴일
- concurrent order atomicity
- DB engine
- PHP framework
- session/token format
- data retention
- ranking privacy controls
- trade-journal 저장 schema

## 7. 후속 실측 체크리스트

권한 있는 테스트 환경에서:
1. 교사 반 생성
2. 학생 25명 붙여넣기/등록
3. 초기자금 일괄설정
4. QR 전체인쇄
5. 학생 코드 로그인
6. KRW→USD 환전
7. 국장 매수/매도
8. 미장 매수/매도
9. 동시 double-click order
10. 잔액 부족
11. 보유수량 초과매도
12. 거래가능시간 밖 접근
13. 시장 닫힘
14. 시세 provider 오류
15. 매매일지 작성
16. Teacher Dashboard 집계
17. 랭킹 공개범위
18. 모바일 360 / 태블릿 768 / desktop 1280
