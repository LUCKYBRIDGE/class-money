# Class Money — 현재 파일·폴더·기술 구조

정확도: **A — 우리 repository 직접 확인**

## 현재 repository 상태

아직 구현코드가 없는 기획·연구 repository.

현재 root:
- README.md
- docs/

## docs 구조

- docs/architecture/
  - economy-kernel-v4.md
  - implementation-plan.md

- docs/product/
  - economy-engine-and-policies.md
  - requirements.md
  - student-learning-loop-v4.md
  - teacher-operations-v4.md
  - teacher-student-journeys.md

- docs/research/
  - benchmark-2026-11.md
  - benchmark-metrics-v4.md
  - craft-anything-protocol.md
  - deep-analysis-2026-11.md
  - economic-risk-register-v4.md
  - verification-and-scorecard.md
  - services/
  - structures/
  - synthesis/
  - direct-inspection/
  - technical-structure/

## 현재 문제

서비스별 연구가 여러 폴더로 중복돼 있다.
- services root
- services/dossiers
- services/ui-ux
- services/ux
- structures
- direct-inspection/services

## 구현을 시작할 때 권장 source tree

X 제안:

- apps/
  - web/
    - teacher/
    - student/
    - shared/

- packages/
  - domain/
    - accounts/
    - ledger/
    - allocations/
    - jobs/
    - store/
    - schedules/
    - permissions/
  - ui/
  - validation/

- server/
  - api/
  - application/
  - domain/
  - persistence/
  - jobs/

- tests/
  - domain/
  - integration/
  - e2e/
  - fixtures/

- docs/
  - adr/
  - research/
  - product/
  - architecture/

## 구현 전 필수 기술결정

- frontend framework
- backend/runtime
- database
- auth model
- student code/PIN model
- scheduler
- transaction isolation
- append-only ledger
- PWA/offline 범위
- export/import format

이 문서는 구현 시작 전까지 제안 구조이며 실제 source tree가 생기면 갱신한다.