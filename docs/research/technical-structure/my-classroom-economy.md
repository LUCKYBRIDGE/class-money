# My Classroom Economy — 파일·폴더·기술 구조

정확도: **C — 소프트웨어 source보다 문서/인쇄 artifact가 시스템 본체에 가까움**

## 제품 성격
My Classroom Economy는 현재 분석대상 중 가장 소프트웨어 repository와 거리가 멀다.

실제 시스템을 구성하는 것은:
- Program Guide PDF
- Job Application
- Job Offer
- Job Posters
- Paycheck
- Bank Log
- Bank Slips
- Fine Ticket
- Offense Log
- Rental Agreement
- Rent Log
- Deed
- Auction Record
- Auction Paddle
- Certificates
같은 문서다.

## 문서를 software folder처럼 대응하면
개념적으로:
- jobs/
- payroll/
- banking/
- rent/
- fines/
- loans/
- auctions/
- reflection/
- printables/
로 분리할 수 있다.

하지만 이는 X 제안이며 원 서비스 실제 repository tree가 아니다.

## 기술적 workflow
Teacher-defined rules
→ printed artifacts
→ student/manual processing
→ dual ledger comparison
→ monthly cycle
→ year-end reflection.

## state storage
상태는 주로:
- 학생 종이장부
- banker log
- teacher log
- 계약서/수표/티켓
에 분산 저장된다.

즉 DB 대신 물리적 문서와 역할이 state machine을 구현한다.

## Class Money 기술설계에 주는 교훈
디지털화할 때:
- 계산/중복/누락은 시스템화
- 계약/예상/확인/회고는 UI와 printable로 남김
- digital record와 printable artifact가 동시에 존재하는 hybrid architecture가 적합.

## 공개 GitHub
공식 product source repository는 확인하지 못했다.