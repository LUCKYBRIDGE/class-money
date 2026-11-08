# NatWest Rooster Money — 파일·폴더·기술 구조

**증거 수준:** C — 제품 source 비공개

## 공개 source 판정

- 현재 product source 공식 public repo 확인 못함.

## 외부에서 확인되는 기술 모듈

- Parent Client
- Child Client
- Tasks
- Schedules
- Submissions
- Approvals
- Payout Policy
- Batch Commands
- Exceptions
- History
- Shared-device Session

## 파일·폴더 기록 원칙

- 실제 공식 repository가 있으면 **실제 path와 file name**을 적는다.
- 제품 본체 source가 비공개면 위 목록은 실제 folder tree가 아니라 외부 동작으로 확인되는 **logical module boundary**다.
- framework, database, backend language, hosting을 근거 없이 추정하지 않는다.

## 현재 확인하지 못한 내부구조

- 현재 app framework
- backend/DB
- push stack
- scheduler
- 실제 child/parent navigation

## Class Money 구현으로 옮길 때

이 서비스의 내부 구현을 복제하지 않는다. 확인된 제품 경계와 상태모델만 우리 도메인 모듈 설계의 참고로 사용한다.
