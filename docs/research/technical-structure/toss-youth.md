# 토스 유스 — 파일·폴더·기술 구조

정확도: **C — 현재 제품 source 비공개**

## 공개 source 여부
토스 유스 소비자 제품 본체의 공식 public source repository를 이번 조사에서 확인하지 못했다.

실제 Toss 내부 monorepo/package 구조를 추정하지 않는다.

## 외부 surface
- youth-specific mobile experience
- guardian management
- Youth Card
- Allowance Tracker
- Goal/Fan Pot
- financial learning
- mock investing
- friend transfer/message
- safety/support

## logical domains
- youth profile
- guardian relation
- prepaid balance
- transactions
- spending analytics
- goals/pots
- learning content
- simulation account
- social transfer
- safety/recovery

## 기술적으로 중요한 separation

### Available balance vs Goal/Pot
사용 가능한 돈과 목적저축을 분리.

### Real financial area vs Simulation
실제 금융기능과 모의투자/학습을 분리.

### Youth vs Guardian surface
사용자 역할별 앱 IA와 복구권한 분리.

## Class Money 대응 모듈
X 제안:
- student-shell
- teacher-shell
- available-account
- goal-account
- transaction-analytics
- reflection
- simulation-lab
- recovery

## 미확인
- 실제 mobile framework
- backend/service architecture
- DB
- event streaming
- notification stack
- payment infra