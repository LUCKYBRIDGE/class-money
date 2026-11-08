# ClassBank — 파일·폴더·기술 구조

정확도: **C — 제품 source 비공개**

## 공개 source 여부
현재 ClassBank classroom economy 제품의 공식 public source repository를 확인하지 못했다.

실제 file/folder tree는 알 수 없다.

## 외부에서 확인되는 client/surface
- Teacher dashboard
- Student account
- Student Helper role surfaces
- Co-teacher access
- School/District layer
- Help Center

## 외부 기능 기준 logical modules
- organization / school
- classes
- students
- bonuses / fines
- jobs
- job applications
- employment
- payroll / auto pay
- bills / recurring expenses
- store / inventory / purchases
- savings / interest
- transactions
- reports / exports
- student helper permissions
- co-teacher permissions
- SIS / attendance integration for school plans

## 역할/권한 구조
외부 문서에서 확인:
- Teacher
- Student
- Store Clerk
- HR Representative
- Banker
- Co-teacher
- school/district admin layer

Job title과 helper permission이 별도 설정으로 존재한다.

## automation boundary
- auto pay
- recurring bills
- interest
- school plan attendance automation

내부 scheduler, queue, retry, idempotency 구현은 미확인.

## data/report boundary
공개 report 영역:
- All Transactions
- Student Transactions
- Student Jobs
- Store Purchases
- Student List
- Job Details

여러 domain object가 독립적으로 기록된다는 외부 근거는 있지만 실제 schema는 미확인.

## Class Money 대응 모듈
X 제안:
- org
- classroom
- roster
- jobs
- applications
- payroll
- bills
- store
- ledger
- savings
- permissions
- reports
- scheduler
- integration-adapters

## 미확인
- frontend stack
- backend stack
- DB
- API
- auth/session
- deployment