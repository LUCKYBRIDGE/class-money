# YNAB — 파일·폴더·기술 구조

**증거 수준:** A/B — 공식 SDK와 Starter Kit 공개, 소비자 앱 본체는 비공개

## 공개 source 판정

- ynab/ynab-sdk-js 공식 current SDK.
- ynab/ynab-api-starter-kit 공식 학습용 app.
- Starter Kit stack을 소비자 YNAB app stack으로 오인하지 않음.

## 외부에서 확인되는 기술 모듈

- Official JS SDK
- Plans API
- Accounts API
- Categories API
- Transactions API
- Money Movements API
- Scheduled Transactions API
- Starter Kit Vue 3 + webpack + OAuth

## 파일·폴더 기록 원칙

- 실제 공식 repository가 있으면 **실제 path와 file name**을 적는다.
- 제품 본체 source가 비공개면 위 목록은 실제 folder tree가 아니라 외부 동작으로 확인되는 **logical module boundary**다.
- framework, database, backend language, hosting을 근거 없이 추정하지 않는다.

## 현재 확인하지 못한 내부구조

- 실제 YNAB consumer frontend tree
- 실제 backend services/DB
- 내부 event processing

## Class Money 구현으로 옮길 때

이 서비스의 내부 구현을 복제하지 않는다. 확인된 제품 경계와 상태모델만 우리 도메인 모듈 설계의 참고로 사용한다.
