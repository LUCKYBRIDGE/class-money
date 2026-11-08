# ClassDojo — 파일·폴더·기술 구조

정확도: **B — 공식 공개 organization/부분 source만 확인**

## 공식 GitHub organization
- github.com/classdojo

## 공개 repository 유형

직접 확인:
- policies
- agenda
- database
- photo-collage
- rabbitmq / S3 관련 utility
- 기타 library/infrastructure

## classdojo/policies 실제 tree

- README.md
- child-privacy.md
- premium-features.md
- privacy.md
- security.md
- terms.md
- third-party-service-providers.md
- website-privacy.md

README는 이 repository가 Terms/Privacy 변경이력을 공개하기 위한 목적이라고 명시한다.

따라서 현재 Points frontend/backend source가 아니다.

## 현재 제품에서 외부로 확인되는 기술 경계

- Class
- Student tiles
- Groups
- Skills
- Point Event
- Reports
- Undo
- family/student visibility

## 확인 불가

- 현재 frontend framework
- mobile native/web architecture
- point storage schema
- realtime transport
- report aggregation backend
- DB/queue/cache

## Class Money 대응 모듈

X 제안:
- class-roster
- student-selector
- group-selector
- reason-preset
- quick-award
- event-log
- report-read-model
- reversal