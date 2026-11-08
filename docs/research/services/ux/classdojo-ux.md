# ClassDojo — 즉시 입력·그룹·보고서 UI·UX 심층 분석

기준일: 2026-11-08  
목적: 경제모델이 아니라 수업 중 초저마찰 입력 UX 분석.

## 1. 복잡성의 원천
교사는 수업을 진행하면서 개인, 그룹, 전체에게 서로 다른 Skill을 즉시 기록해야 한다. 동시에 보고서, 활동, 스토리, 채팅, 알림 등 여러 기능이 존재한다.

## 2. 핵심 해법: 학생 타일 + Skill
교사의 순간적 사고를:
누구에게? → 무엇을?
두 질문으로 축소한다.

개인:
학생 타일 → Skill

그룹:
Groups 탭 → 그룹 → Award group → Skill

Class Money의 빠른 지급 UI가 배워야 할 구조다.

## 3. 그룹을 별도 객체로 만듦
학생을 매번 여러 명 선택하지 않고 Group을 재사용한다.

Class Money:
- 모둠
- 직업팀
- 임시 그룹
을 저장할 수 있게 하되,
각자 지급과 공동기금 지급은 완전히 다른 버튼으로 표현한다.

## 4. 보고서와 현재 표시값 분리
Redeem된 포인트는 현재 bubble에서는 빠지지만 report에는 기록이 남는다.

이는 Class Money에서:
현재 사용가능 잔액과 과거 거래 원장은 별개라는 개념으로 번역할 수 있다.

단 금융원장은 Reset으로 지우면 안 된다.

## 5. Undo를 즉시 제공
잘못 지급한 포인트를 빠르게 되돌릴 수 있다.

Class Money:
지급 완료 직후 5~10초 안에 보이는 Undo를 제공하고, 시간이 지나면 거래 상세의 정정으로 이동.

## 6. 모바일 내비게이션에서 배울 점
2026년 학교용 모바일 개편은 하단에 School / Classes / Chats / Notifications, 상단에 Calendar / Points / Directory 같은 문맥 탭을 둔다. 통합 Inbox/Notifications와 빠른 class 이동도 강조한다.

Class Money 교사 모바일:
하단 핵심 탭은 홈 / 학급 / 지급 / Inbox / 더보기 정도가 적합하다.

## 7. 화면 위치 기억
ClassDojo는 사용자가 이전에 보던 위치/탭으로 돌아가게 하는 방향을 강조한다.

Class Money도 여러 반을 오가는 교사에게:
- 마지막 반
- 마지막 학생 필터
- 마지막 거래 기간
을 기억할 수 있다.

## 8. UX 위험
포인트 UI가 너무 간편하면 금융거래에서도 같은 수준으로 무조건 단순화하려는 유혹이 생긴다.

하지만 Class Money의 고액/전체 지급은:
대상 인원 + 총액 + 이유
재확인이 필요하다.

즉 저위험 지급과 고위험 거래는 UI 마찰 수준이 달라야 한다.

## 9. Class Money 적용
강하게:
- 학생 타일
- 그룹 객체
- 사유 템플릿
- 빠른 Undo
- 통합 알림
- 모바일 핵심 탭
- 마지막 위치 기억

차별화:
- 금액/대상에 따른 위험 기반 확인
- 모든 거래는 원장 기록
- 행동 포인트와 경제화폐 분리

## 10. Craft Anything 실측 항목
- 개인 지급 클릭수
- 그룹 생성/재사용
- 그룹 포인트 지급
- Undo 위치와 시간
- 보고서 진입
- 모바일 탭 이동
- 여러 반 전환
- 통합 Notification 필터

## 공식 근거
- https://help.classdojo.com/hc/en-us/articles/205494185-How-to-Set-Up-and-Award-Points-to-Groups
- https://help.classdojo.com/hc/en-us/articles/205647205-How-to-Redeem-Class-Points
- https://help.classdojo.com/hc/en-us/articles/37495808286093-Meet-the-New-Mobile-App-for-Schools
