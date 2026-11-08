# ClassCents — 파일·폴더·기술 구조

정확도: **C — 제품 source 비공개**

## 공개 source 여부
현재 ClassCents 제품 본체의 공식 public source repository를 확인하지 못했다.

## 외부 delivery 구조
- web-based teacher interface
- optional student dashboard
- phone/tablet/Chromebook student access
- printable login cards
- CSV/Excel/paste roster input
- CSV export / printable statements

## 핵심 logical modules
- classroom
- roster
- currency settings
- jobs
- job assignment
- job completion
- payday scheduler
- quick Give/Deduct
- reason presets
- groups / target selection
- shop / rewards / stock
- redemptions
- balance
- transaction history
- undo
- savings
- goals
- badges
- leaderboard
- student credentials
- export/print

## 가장 중요한 architecture 특성
학생 login이 없어도 teacher interface만으로 핵심 경제가 완주된다.

따라서 product architecture상:
- Teacher-operated path
- Student self-service path
가 동일 domain을 공유하는 이중 interaction layer로 보는 것이 적합하다.

실제 코드구조는 미확인.

## automation boundary
- daily/weekly/monthly payday
- app을 열지 않아도 실행

server-side scheduler가 필요하다는 기능적 요구는 명확하지만 구현은 미확인.

## identity boundary
- student email 불필요
- teacher-generated credentials
- printable card

실제 credential storage/auth implementation은 미확인.

## Class Money 대응 모듈
X 제안:
- teacher-app
- student-app
- shared-domain
- roster-import
- credentials
- jobs-payday
- quick-transactions
- store
- ledger
- savings-goals
- export-print

## 미확인
- frontend framework
- backend
- DB
- session/auth technology
- hosting