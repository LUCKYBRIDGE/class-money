# NatWest Rooster Money — 파일·폴더·기술 구조

정확도: **C — 제품 source 비공개**

## 공개 source 여부
현재 Rooster Money 제품 본체의 공식 public source repository는 확인하지 못했다.

## 외부 surface
- parent app
- child app/user mode
- shared-device Switch User
- chore management
- allowance tracker
- Help Center

## 핵심 logical modules
- family
- child
- allowance
- allowance period
- chore
- allowance chore
- extra earner
- recurrence schedule
- submission
- approval
- re-open
- skip
- not-done
- payout policy
- reward
- pot/history
- shared-device session

## 가장 중요한 technical separation
Task state와 Payout state를 분리해야 외부 behavior를 설명할 수 있다.

Task:
TODO / SUBMITTED / APPROVED / REOPENED / SKIPPED / NOT_DONE.

Payout:
PENDING / FULL / PARTIAL / NONE / POSTED.

실제 내부 enum/schema는 미확인.

## batch processing
bulk approve/select all 지원.

Class Money에서는 25명 단위 batch command와 partial exception 처리가 핵심 technical requirement.

## schedule layer
daily/weekly/monthly/one-off 같은 사람이 이해하는 rule이 외부 UI에 나타난다.

내부 scheduler 기술은 미확인.

## Class Money 대응 모듈
X 제안:
- tasks
- schedules
- submissions
- approvals
- payout-policy
- batch-commands
- exceptions
- child-session-switch
- history

## 미확인
- native/web framework
- backend
- DB
- push notification stack
- scheduler