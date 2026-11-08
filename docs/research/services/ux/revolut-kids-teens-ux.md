# Revolut Kids & Teens — 연령별 자율성·Pockets·Analytics UI·UX 심층 분석

기준일: 2026-11-08  
증거 수준: 공식 지역별 Kids & Teens 페이지와 Help 기반. 실제 금융 기능은 지역별 차이가 있으므로 구조 중심 분석.

## 1. 복잡성의 원천
실제 금융서비스는 계좌, 카드, 송금, Pockets, Analytics, Challenges, Goals, 보호자 승인, 연령제한을 함께 다룬다.

핵심 UX 문제는 아이에게 자율성을 주면서도 보호자 통제를 유지하는 것이다.

## 2. 핵심 해법: Parent App과 Kid App 분리
부모와 아이가 같은 화면을 권한만 다르게 쓰는 것이 아니라 각자 역할에 맞는 앱 경험을 가진다.

Class Money:
교사 앱의 축소판을 학생에게 보여주지 않는다.

학생 IA:
내 돈 / 목표 / 할 일 / 내역

교사 IA:
학급 / 승인 / 지급 / 정책 / 거래 / 통계

## 3. Pockets
돈을 특정 목적별 하위 공간으로 분리한다.

이 구조는 학생에게 ‘총자산’보다 ‘목적’을 보게 한다.

Class Money:
쓸 돈 / 목표저축 / 공동체 / 다음 지출
정도의 2~4개 목적 공간이 적합하다.

## 4. Analytics
학생이 돈이 어디에 갔는지 직접 볼 수 있게 한다.

Class Money에서도 통계는 교사만의 도구가 아니어야 한다.

학생:
- 이번 주 수입
- 이번 주 소비
- 저축
- 지난주와 변화
- 목표 진행

## 5. Challenges
부모가 과업을 만들고 빈도와 보수를 설정하며 아이는 자신의 앱에서 Challenge를 요청할 수도 있고 보호자 승인이 필요하다.

Class Money:
교사가 모든 과업을 만들어야 하는 구조 외에 학생이:
‘이 역할을 맡고 싶어요’
‘이 추가 과업을 해도 될까요?’
를 제안하는 흐름도 가능하다.

## 6. 연령별 Progressive Autonomy
공식 페이지는 지역/연령에 따라 계정 생성, 결제, 송금 등 자율 범위가 달라짐을 보여준다.

Class Money는 법적 연령 대신 학년 프리셋을 사용할 수 있다.

1~2:
간단 잔액/목표

3~4:
직업/저축/상점

5~6:
승인형 거래/세금/시장 시뮬레이션

교사가 조정 가능.

## 7. 위험 기반 승인
모든 학생 행동을 승인시키면 교사 업무가 커진다.

권고:
자동:
본인 지갑→저축, 소액 상점 구매

승인:
고액 구매, 학생간 거래, 대출, 학생 운영자 지급

UI는 거래 위험도에 따라 마찰을 다르게 준다.

## 8. Co-parent에서 배울 것
여러 관리자가 자녀 계정을 관리할 수 있는 구조는 co-teacher 권한 설계와 연결된다.

Class Money:
공동교사에게
조회 / 지급 / 상점 / 정책 / export
를 세분화.

## 9. UX 위험
- 실제 금융 앱의 기능량을 초등 앱에 그대로 가져오면 과부하.
- 연령별 기능 차이를 단순 잠금 아이콘만으로 보여주면 이유를 이해하기 어려움.
- 송금 자율성을 교실에 그대로 적용하면 분쟁 위험.

## 10. Class Money 적용
- 교사/학생 IA 완전 분리
- 목적별 Pockets
- 학생용 Analytics
- Challenge 요청
- 학년별 기본 프리셋
- 위험 기반 승인
- co-teacher 세분 권한

## 11. Craft Anything 실측 항목
- parent/kid 홈 비교
- Pocket 생성/이동
- Analytics 정보밀도
- Challenge 생성/요청/승인
- 연령제한 기능 표현
- co-parent 관리 화면

## 공식 근거
- https://www.revolut.com/revolut-kids-and-teens-parent-and-guardians/
- https://help.revolut.com/en-IE/help/profile-and-plan/revolut-junior/18-earn/
