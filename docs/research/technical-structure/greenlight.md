# Greenlight — 파일·폴더·기술 구조

정확도: **C — 소비자 제품 source 비공개**

## 공개 source 여부
현재 Greenlight 소비자 제품 본체의 공식 public source를 확인하지 못했다.

## 외부 surface
- parent mobile app
- child mobile experience
- family/shared chores surface
- card/payment infrastructure
- Help Center

Class Money는 실제 금융인프라를 분석대상에서 제외하고 family money-management architecture만 본다.

## 외부 기능 기준 logical modules
- family
- parent/admin
- child profile
- allowance
- chores
- chore completion/review
- earnings
- allocation rules
- spend bucket
- savings
- giving
- goal
- permissions
- transfer requests
- shared Family Hub

## 중요한 technical boundary
Allowance/earning 발생과 allocation을 분리한다.

Chore도:
- task state
- review state
- reward/payment state
가 분리돼야 외부 동작을 설명할 수 있다.

Goal은 money container + permission behavior를 가진다.

## validation layer
공개 Help에서:
- allocation total 100%
- multi-child category compatibility
를 save 전에 검사.

즉 domain validation이 UI form validation 이상의 역할을 한다.

## permission layer
child별 action permission이 독립 toggle.

Class Money에서는 RBAC만으로 부족하고 policy/permission service가 필요하다는 근거.

## Class Money 대응 모듈
X 제안:
- profiles
- tasks
- reward-rules
- allocations
- accounts
- goals
- permissions
- approvals
- shared-view
- validation

## 미확인
- native framework
- backend/API
- banking integration architecture
- DB
- queue/scheduler
- hosting