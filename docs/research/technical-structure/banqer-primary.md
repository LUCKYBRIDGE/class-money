# Banqer Primary — 파일·폴더·기술 구조

정확도: **B — 공식 조직의 부분 source는 확인, 현재 Primary 본체 source는 비공개**

## 공식 GitHub organization
- github.com/Banqer

## 직접 확인한 repositories

### Banqer/angular_sample
실제 tree:
- README.md
- simple-quiz.component.html
- simple-quiz.component.ts
- simple-quiz.styl

README가 명시적으로:
- 과거 Banqer High의 obsolete code
- interview discussion용 sample
이라고 설명한다.

따라서 현재 Banqer Primary app source가 아니다.

simple-quiz.component.ts에서 확인되는 과거 sample 구조:
- Angular Component
- Input questions
- Output completion event
- BrowserStorage를 통한 진행위치 저장
- correct/incorrect callback
- question validation

### Banqer/ui-select-banqer
Angular 1.5용 ui-select historical working copy.

## 현재 제품에서 외부로 확인되는 기술 경계

- browser-based product
- Teacher Dashboard
- Student Dashboard
- module/expansion activation
- Class Store open/closed runtime state
- cart / checkout / My Stuff / claim
- learning content와 simulation 연결

## 현재 확인할 수 없는 내부 구조

- 현재 frontend framework
- backend language
- database
- API topology
- queue/scheduler
- auth implementation
- deployment platform

## 기술적 해석에서 지켜야 할 경계

공식 organization에 과거 Angular code가 있다는 이유로 현재 Primary가 Angular라고 기록하지 않는다.

## Class Money에 대응되는 기술 모듈

X 제안:
- module-registry
- classroom-module-state
- teacher-dashboard
- student-dashboard
- store
- checkout
- inventory
- fulfillment/claim
- learning-content
- simulation-engine