# 반짝 모의투자 — 파일·폴더·기술 구조

기준일: 2026-11-11

정확도: **C+ — 일부 실제 파일경로와 초기 설계 공개, 제품 전체 source 비공개**

## 현재 직접 확인 경로

```text
/API/stock/
├─ ad.html
├─ index.php
├─ teacher_login.php
└─ student_login.html
```

## 과거 개발기에서 확인한 path

```text
/API/stock/
├─ admin.html
├─ student.html           # 당시 아직 미작성이라고 언급
├─ api_update_student.php
└─ api_delete_student.php
```

## 초기 DB 설계안

- users
- stocks
- holdings
- transactions

세부는 canonical:
- ../services/banjjak-stock/04-technical-structure.md

## 확인 가능한 기술
- HTML 페이지
- PHP server endpoint/page
- browser-based responsive service
- QR/access-code identity
- server-mediated market data가 필요한 구조
- KRW/USD multi-currency
- domestic/US market
- teacher/student role separation

## 현재 확인 불가
- 전체 source repository
- PHP framework
- database engine
- current quote provider
- FX provider
- scheduler/cache
- transaction isolation
- deployment architecture

## Class Money 적용
시장 simulation은 core economy와 별도 bounded context로 설계 권고.
