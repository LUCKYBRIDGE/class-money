# Class Money repository 자체 직접 분석

기준일: 2026-11-08

대상: LUCKYBRIDGE/class-money main tree 직접 확인.

## 현재 상태
README에 명시된 대로 아직 구현 코드가 없는 기획·벤치마킹 repository다.

현재 주요 영역:
- docs/architecture
- docs/product
- docs/research

## 강점
연구가 단순 기능목록을 넘어 다음까지 확장돼 있다.
- economy kernel
- teacher operations
- student learning loop
- risk register
- benchmark metrics
- service dossiers
- UX
- structures
- direct inspection

## 직접 tree에서 확인한 문제
서비스별 분석이 여러 위치에서 중복된다.
- docs/research/services/*.md
- docs/research/services/dossiers/*.md
- docs/research/services/ui-ux/*.md
- docs/research/services/ux/*.md
- docs/research/structures/*.md
- docs/research/direct-inspection/services/*.md

분석이 깊어질수록 같은 서비스의 최신 판단이 어디에 있는지 찾기 어려워진다.

## 권장 정리 방향
서비스별 하나의 폴더로 모으는 편이 낫다.

예:
docs/research/services/classcoin/
  evidence.md
  product-anatomy.md
  ux.md
  implications.md

그리고 synthesis와 architecture는 서비스 밖에 유지.

## 단, 즉시 이동하지 않는 이유
현재 README와 여러 문서 링크가 기존 경로에 의존한다.

따라서:
1. direct-inspection evidence를 먼저 충분히 쌓고
2. canonical service folder를 만든 뒤
3. 기존 문서는 redirect/index 역할로 남기고
4. 링크를 점진적으로 교체
하는 방식이 안전하다.

## 다음 개발 전 repository 요구
실제 구현을 시작할 때 최소:
- app source
- migrations/schema
- tests
- ADR/decision-log
- seeded demo class
- fixtures for 25 students
- transaction invariant tests
가 추가돼야 한다.