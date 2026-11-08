# ClassCoin — 파일·폴더·기술 구조

정확도: **C — 현재 제품 source 비공개**

## 공개 source 여부
ClassCoin 이름의 GitHub repository는 검색되지만 classcoin.me 현재 제품의 공식 source라는 근거를 확인하지 못했다.

따라서 실제 src/components/api/db 구조는 기록하지 않는다.

## 외부에서 확인되는 제품 surface
- public website
- teacher sign-in
- student class-code entry
- kiosk/scoreboard surface
- teacher management dashboard
- student economy/game surface
- guide/documentation site

## 외부 기능을 기준으로 나뉘는 기술 모듈
- class / student identity
- scoreboard / quick award
- quests / routines
- jobs / payroll
- store
- wallet / transaction history
- savings / interest
- tax / treasury
- property / investment / marketplace
- loans / credit
- notifications
- quizzes / missions
- game modules / separate game currency
- settings / feature visibility

## 확인되는 자동화 경계
- scheduled payroll
- interest
- tax
- treasury recurring spending

내부 scheduler, queue, retry implementation은 미확인.

## 데이터/권한 경계
외부 동작상 최소 Teacher / Student / Public-Kiosk surface가 분리돼 있다.

실제 RBAC schema, session implementation, audit data model은 미확인.

## 기술적으로 중요한 제품 특성
2026-10-26 업데이트에서 feature visibility, settings regrouping, preview, failed notification recovery가 확인된다.

이는 내부적으로 feature flag/state/policy layer가 존재할 가능성을 시사하지만 실제 구현형태는 미확인이다.

## Class Money 대응 모듈
X 제안:
- identity
- classroom
- quick-award
- jobs-payroll
- ledger
- store
- savings
- tax-treasury
- modules
- notifications
- policy-preview
- game-economy-adapter

## 미확인
- frontend framework
- backend/runtime
- DB
- API
- realtime mechanism
- scheduler implementation
- hosting/deployment