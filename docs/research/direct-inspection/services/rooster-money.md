# NatWest Rooster Money 직접 관찰

기준일: 2026-11-08

## 직접 연 페이지
- https://roostermoney.com/
- https://support.roostermoney.com/en/collections/1707398-chores
- https://support.roostermoney.com/en/articles/2943417-linking-chores-to-allowance
- https://support.roostermoney.com/en/articles/2943433-set-extra-earners-to-earn-additional-money-card-feature
- https://support.roostermoney.com/en/articles/2943441-how-can-i-manage-and-approve-chores-card-feature

## 핵심 도메인 구분
공식 Help에서 Chore를 먼저 두 종류로 나눈다.
- Allowance Chore
- Extra Earner

Allowance Chore는 정기 용돈의 조건이고 Extra Earner는 추가 reward가 붙는 별도 task다.

교실에서도 공동체 기본책임 / 정기 직업업무 / 추가 유급 task를 분리해야 한다.

## 상태 중심 Chore UX
공식 Help에서 목록을 상태로 구분:
- To Approve
- Overdue
- To do
- Approved
- Not done

가능 행동:
- Approve
- Not done
- Re-open
- Skip

학생이 완료했다고 해서 즉시 경제 transaction이 확정되는 것이 아니다.

Task completion과 Reward payment를 분리하는 구조다.

## Bulk Operation
여러 chore 선택 또는 Select all 후 bulk status 변경 가능.

25명 학급에서도 같은 task를 개별 처리하지 않도록 하는 핵심 패턴이다.

## Child submission
- child own login 또는 Switch User
- complete 표시
- photo
- note
- parent notification

공유기기 사용자 전환을 공식 flow로 지원한다.

## Allowance 정책
미완료 task가 있을 때 full / percentage / prompted decision 등 payout policy를 선택할 수 있다.

Class Money에서는 결석/지원필요/면제를 별도 exception status로 둬 단순 완료비율이 부당한 감액으로 이어지지 않게 해야 한다.

## 공개 GitHub 판정
검색되는 Rooster Money 관련 repositories는 제3자 integration/비공식 프로젝트가 중심이며 현재 제품 source는 확인하지 못했다.

## Class Money에 가져올 것
- Task type 분리
- Today / Overdue / Approval queue
- Re-open / Skip / Not Done
- bulk approve
- shared-device Switch User
- payout policy
- 생활언어 schedule

## 현재 미확인
- 최신 app의 실제 Today screen density
- child/parent bottom navigation
- photo evidence flow의 현재 UI
- accessibility