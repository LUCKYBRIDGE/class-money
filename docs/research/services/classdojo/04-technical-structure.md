# ClassDojo — 파일·폴더·기술 구조

**증거 수준:** B — 공식 GitHub 조직/부분 source 확인, 현재 Points 본체 source 비공개

## 공식 GitHub organization

- github.com/classdojo

## 직접 확인한 공개 repository 유형

- policies
- agenda
- database
- photo-collage
- RabbitMQ/S3 관련 utility
- 기타 infra/library

### classdojo/policies 실제 확인

```text
policies/
├─ README.md
├─ child-privacy.md
├─ premium-features.md
├─ privacy.md
├─ security.md
├─ terms.md
├─ third-party-service-providers.md
└─ website-privacy.md
```

README는 이 repository가 Terms/Privacy 변경이력을 공개하기 위한 목적임을 명시한다.

따라서 Points UI/engine source가 아니다.

## 외부에서 확인되는 Points logical modules

```text
ClassDojo Points
├─ Class / Roster
├─ Student Selector
├─ Group Selector
├─ Skills
├─ Quick Point Event
├─ Notes
├─ Undo
├─ Reports
└─ Visibility / Family Settings
```

실제 내부 folder tree가 아니라 공개 기능을 설명하는 모듈 경계다.

## Class Money 기술 대응

```text
teacher/
├─ student-selector/
├─ group-selector/
└─ quick-award/

domain/
├─ reason-presets/
├─ transactions/
├─ batches/
└─ reversals/

read-models/
└─ reports/
```

특히:
- StudentGroup = 대상 선택
- GroupAccount = 공동기금

을 별도 도메인으로 둔다.

## 현재 확인 불가
- 현재 frontend framework
- mobile/web architecture
- point storage schema
- realtime transport
- report aggregation backend
- DB/cache
