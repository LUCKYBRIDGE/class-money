# 서비스별 기능 얽힘·UI·UX 분석 인덱스

기준일: 2026-11-08

이 폴더는 서비스별 기능 목록을 반복하지 않는다. 각 앱/웹이 **복잡하게 얽힌 기능을 사용자에게 어떤 구조로 풀어냈는지**를 분석한다.

## 분석 축

각 서비스에서 공통적으로 다음을 본다.

1. **Feature graph** — 기능이 어디서 발생하고 어디로 연결되는가.
2. **Information Architecture** — 기능을 메뉴/대시보드/모듈로 어떻게 나누는가.
3. **Progressive Disclosure** — 처음부터 무엇을 숨기고 언제 보여주는가.
4. **Primary Flow** — 가장 자주 하는 일을 몇 단계로 만드는가.
5. **Common Interaction Pattern** — 서로 다른 기능을 같은 UI 패턴으로 통일하는가.
6. **State Model** — 예정/대기/승인/완료/실패/정정 같은 상태를 어떻게 보여주는가.
7. **Role Separation** — 교사/학생/보조역할/보호자의 UI가 어떻게 다른가.
8. **Automation vs Learning** — 자동화하면서도 학생이 알아야 할 과정은 남기는가.
9. **Error Recovery** — Undo, refund, 재시도, 복구를 어떻게 풀어내는가.
10. **Mobile/Shared Device** — 학생 기기·공유 태블릿 상황에 어떻게 대응하는가.
11. **Class Money 적용** — 원리를 가져올지, 변형할지, 제외할지.

> 현재 UI 분석은 공식 공개 페이지/도움말에서 확인 가능한 구조를 기반으로 한다. 로그인 뒤 실제 픽셀·클릭수·반응시간은 Craft Anything 실측 과제로 남긴다.

---

## 교실경제 서비스

### [ClassCoin UI·UX](classcoin-ui-ux.md)
**복잡성:** 학급경영 + 경제 + 게임 + 금융 기능이 한 서비스에서 연결됨.  
**푸는 방식:** 큰 기능군, 역할별 가이드, 기능 숨김, 설정 재그룹화, 경제규칙 영향 미리보기.  
**가장 중요한 참고:** 기능이 많아질수록 ‘추가’보다 **숨김과 우선순위**가 중요.

### [ClassBank UI·UX](classbank-ui-ux.md)
**복잡성:** Bonuses/Jobs/Bills/Store/Savings를 반마다 선택적으로 사용.  
**푸는 방식:** 최소 기능으로 시작하고 모듈을 나중에 열기, 학생 Helper별 제한 UI.  
**가장 중요한 참고:** **Progressive Disclosure와 역할 기반 navigation.**

### [Cashroom UI·UX](cashroom-ui-ux.md)
**복잡성:** 급여·청구·구매·저축·경매·대출 등 매우 다른 거래.  
**푸는 방식:** Pending → Math Check → Record라는 공통 인터랙션, One Bell, 거래유형별 복구.  
**가장 중요한 참고:** 기능을 줄이지 않고 **상호작용 패턴을 통일**.

### [Banqer Primary UI·UX](banqer-primary-ui-ux.md)
**복잡성:** 소득부터 세금·부동산·보험까지 경제세계가 단계적으로 확장.  
**푸는 방식:** 금융 개념별 Expansion, 교사/학생 Dashboard, 기능별 수업자료.  
**가장 중요한 참고:** 기능을 **학습 모듈 단위로 개방**.

### [ClassCents UI·UX](classcents-ui-ux.md)
**복잡성:** 교사 혼자 운영할 수도 있고 학생 각자가 참여할 수도 있음.  
**푸는 방식:** 학생 로그인 선택, 명부 붙여넣기, 개인/그룹/전체 공통 지급, 자동 Payday, Login Card.  
**가장 중요한 참고:** **Teacher-only와 Student-self-service의 이중 운영모드.**

### [My Classroom Economy UI·UX](my-classroom-economy-ui-ux.md)
**복잡성:** 취업·급여·은행·월세·경매 등 물리적 교실경제 절차.  
**푸는 방식:** Job application, paycheck, bank log, auction paddle 등 행위별 종이 인터페이스.  
**가장 중요한 참고:** 모든 것을 하나의 대시보드에 압축하지 않고 **행위별 작은 인터페이스**로 분해.

---

## 행동 피드백

### [ClassDojo UI·UX](classdojo-ui-ux.md)
**복잡성:** 수업 중 매우 높은 빈도로 반복되는 학생 피드백.  
**푸는 방식:** 학생/모둠 선택 → 사전 정의 Skill → 즉시 지급 → 최근 Undo, 상세는 Reports.  
**가장 중요한 참고:** **빠른 입력 UI와 상세 기록 UI를 분리.**

---

## 아동·청소년 금융 서비스

### [Greenlight UI·UX](greenlight-ui-ux.md)
**복잡성:** 수입을 소비/저축/기부/목표에 나누고, 아이마다 권한이 다름.  
**푸는 방식:** 목적별 money bucket, 100% allocation validation, 과업 상태, permission 토글.  
**가장 중요한 참고:** **돈이 들어오는 순간 목적을 정하게 함.**

### [Rooster Money UI·UX](rooster-money-ui-ux.md)
**복잡성:** 정기 allowance와 추가 earning, 반복 과업.  
**푸는 방식:** allowance chore와 extra earner 분리, 추천과업, 반복 일정.  
**가장 중요한 참고:** 경제를 기능이 아니라 **생활 루틴**으로 보여줌.

### [Revolut Kids & Teens UI·UX](revolut-kids-teens-ui-ux.md)
**복잡성:** 아이 자율성, 보호자 승인, 연령별 기능, Goals/Challenges.  
**푸는 방식:** 부모/아이 화면 분리, progressive access, 위험 기반 승인.  
**가장 중요한 참고:** 권한을 role 하나가 아니라 **행동의 위험도별로 나눔.**

### [토스 유스 UI·UX](toss-youth-ui-ux.md)
**복잡성:** 방대한 금융 플랫폼을 어린 사용자가 사용.  
**푸는 방식:** Youth Home, ‘충전한 만큼만 사용’이라는 명확한 경계, 용돈기입장·목표 저금통.  
**가장 중요한 참고:** 복잡한 금융 기능을 **어린 사용자 전용 정보구조와 쉬운 언어**로 번역.

---

## 개인 예산

### [YNAB UI·UX](ynab-ui-ux.md)
**복잡성:** 계좌·거래·카테고리·목표·자동배분 등 복잡한 예산 모델.  
**푸는 방식:** Ready to Assign, Available, Targets, Auto-Assign preview처럼 ‘돈의 목적’을 중심으로 추상화.  
**가장 중요한 참고:** 기능을 없애지 않고 **사용자가 내부 모델을 몰라도 사용할 수 있게 언어와 흐름을 단순화.**

---

# 서비스별 대표 UX 전략

| 서비스 | 복잡성 해소의 대표 전략 | Class Money에서 사용할 위치 |
|---|---|---|
| ClassCoin | 기능 숨김 + 영향 미리보기 | 고급 모듈/경제설정 |
| ClassBank | Progressive Disclosure | 온보딩 |
| Cashroom | 공통 transaction flow | 학생 거래 |
| Banqer | 개념별 Expansion | 학습모듈 |
| ClassCents | 이중 운영모드 | 학교 기기환경 |
| My Classroom Economy | 행위별 인터페이스 | 출력물/수업활동 |
| ClassDojo | 사전 정의 + Quick Action | 수업 중 지급 |
| Greenlight | 목적별 allocation | 급여/저축 |
| Rooster Money | cadence/routine | 직업·과업 |
| Revolut Kids & Teens | risk-based permission | 권한/승인 |
| 토스 유스 | youth-specific IA | 학생 홈 |
| YNAB | purpose-based abstraction | 학생 예산 |

# Class Money 통합 시 주의

좋은 패턴을 모두 합친다고 좋은 제품이 되지는 않는다.

예를 들어:
- ClassDojo의 즉시 지급을 너무 강조하면 행동보상 앱이 된다.
- Greenlight/YNAB의 budget bucket을 너무 많이 만들면 초등학생에게 복잡해진다.
- Banqer식 모듈을 모두 열어두면 Progressive Disclosure가 사라진다.
- ClassCoin처럼 확장기능이 많아져도 ClassCents의 단순 운영성이 유지되어야 한다.

따라서 최종 설계 기준은:

**교사에게는 가장 적은 결정과 클릭, 학생에게는 가장 필요한 경제적 결정만 남긴다.**
