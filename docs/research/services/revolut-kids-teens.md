# Revolut Kids & Teens 심층 분석

기준일: 2026-11-08  
분석 목적: 연령별 자율성, 보호자 승인, Challenges/Goals/Analytics 참고  
주의: 지역에 따라 대상 연령과 기능 조건이 다를 수 있으므로 절대값보다 구조를 분석한다.

## 1. 왜 분석하는가

Revolut Kids & Teens는 실제 금융서비스 안에서:
- 아이가 직접 쓰는 앱
- 보호자가 감독하는 앱
을 분리하면서 연령에 따라 자율성을 다르게 준다.

Class Money에서 교사와 학생, 저학년과 고학년 권한을 다르게 설계하는 데 참고 가치가 있다.

## 2. 핵심 구조

공식 소개에서 확인:
- 자녀 전용 앱
- 보호자 승인
- allowance
- Challenges/chores/tasks
- Goals
- spending analytics
- 연령에 따른 결제/송금 기능 차이
- 보호자/공동 보호자 관리

## 3. ‘학생용 앱이 따로 있다’는 의미

아이에게 성인 금융앱을 그대로 축소해 보여주지 않는다.

Class Money도:
교사 UI의 read-only 축소판이 학생 UI가 되어서는 안 된다.

학생에게 필요한 핵심:
- 내 돈
- 내 목표
- 내 역할
- 내 거래
- 내 선택

교사에게 필요한 핵심:
- 학급
- 정책
- 승인
- 오류
- 통계

정보구조부터 분리.

## 4. Goals

목표액을 설정하고 progress를 확인하며 일반 사용 돈과 저축 돈을 분리하는 구조.

Class Money:
목표별 가상 지갑을 별도로 만들 필요 없이 ledger account 또는 allocation bucket으로 설계 가능.

중요한 UX:
‘총저축 80’보다
‘미술도구 목표 80/120’
처럼 의미 중심으로 표시.

## 5. Challenges

보호자가 과업을 만들고 완료하면 pocket money를 지급.

Class Money:
- 직업 정기업무
- 임시과업
을 분리한다.

Challenge형 과업은:
- 업무 설명
- 마감일
- 보수
- 완료 제출
- 승인
을 갖는다.

## 6. 연령 기반 기능 차이

Revolut은 지역별로 특정 연령 이상에서 일부 기능을 사용할 수 있게 한다.

Class Money에서 ‘연령’ 자체를 강제 규칙으로 쓰기보다는 학년별 기본 프리셋으로 사용.

예:
1~2학년:
- 송금 없음
- 2개 예산범주
- 간단 목표

5~6학년:
- 승인형 거래
- 세금/예산 시뮬레이션
- 경제 보고서

교사가 조정 가능.

## 7. 부모 승인 모델

실제 금융에서는 보호자 승인이 안전을 위한 필수 요소가 될 수 있다.

Class Money에서는 모든 학생 행동을 승인시키면 교사 업무가 폭증한다.

따라서 ‘위험 기반 승인’이 적합하다.

자동 승인:
- 본인 checking→savings 이동
- 기본 상점 소액 구매

교사 승인:
- 고액 구매
- 학생 간 거래
- 학생 운영자 지급
- 대출
- 특별 상품

## 8. Analytics

Revolut은 spending trends를 아이가 직접 볼 수 있게 한다.

Class Money에서도 데이터는 교사 통계만이 아니라 학생 자기성찰 도구가 되어야 한다.

학생:
- 이번 주 쓴 돈
- 저축한 돈
- 지난주 대비
- 목표 변화

## 9. 공동관리자 모델

Co-Parent처럼 제한된 제2관리자 개념은 Class Money의 co-teacher와 연결된다.

권한을 단순 ‘교사이면 전부 가능’으로 하지 않고:
- 조회
- 지급
- 상점
- 정책설정
- 원장 export
를 분리할 수 있다.

## 10. Class Money에 가져올 것

강하게:
1. 학생 전용 정보구조
2. Goals
3. Challenges
4. 학년별 권한 프리셋
5. 위험 기반 승인
6. 학생용 spending analytics
7. co-teacher 세분 권한

제외:
- 실제 카드
- 실제 P2P 결제
- 실제 금융 계좌
- 상품 구독 구조

## 11. Craft Anything 후속 실측

- 부모 앱과 자녀 앱의 첫 화면 차이
- Challenge 생성/완료
- Goal 생성
- analytics
- 연령별 기능 잠금 표시
- 승인 알림
- co-parent 권한 범위

## 12. 현재 판단

Revolut Kids & Teens의 핵심 시사점은 ‘아동에게 자율성을 주되 같은 수준의 자율성을 모든 행동에 주지 않는다’이다.

Class Money도 기능별 위험도에 따라 학생 자율성과 교사 승인을 다르게 설계하는 것이 적절하다.

## 공식 근거
- https://www.revolut.com/revolut-kids-and-teens-parent-and-guardians/
- Revolut Kids & Teens Terms의 Challenges & Goals 설명
