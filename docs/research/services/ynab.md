# YNAB 심층 분석

기준일: 2026-11-08  
분석 목적: 개인 예산 앱의 ‘돈에 목적을 부여하는 UX’를 Class Money 학생 경험에 적용  
주의: YNAB는 교실경제 앱이 아니며 실제 금융 기능을 복제하지 않는다.

## 1. 왜 분석하는가

교실경제 앱은 학생에게 ‘잔액’을 보여주기 쉽다.

하지만 잔액만 보여주면 학생의 핵심 질문은:
‘얼마나 있지?’
가 된다.

YNAB의 핵심 사고는:
‘이 돈은 무엇을 해야 하지?’
이다.

이 전환이 Class Money 학생 앱의 핵심 차별화가 될 수 있다.

## 2. 핵심 방법

YNAB 공식 방법의 핵심:
Give every dollar a job.

받은 돈을 category에 배분하고, 실제 소비는 category의 Available 금액을 보고 결정한다.

개념:
- Ready to Assign
- Categories
- Assigned
- Available
- Targets
- Underfunded
- Transactions
- Reconcile

## 3. Class Money로 번역

성인 금융 용어를 그대로 쓰지 않는다.

YNAB → Class Money:
- Ready to Assign → 아직 정하지 않은 돈
- Category → 돈의 자리/목적
- Assigned → 이곳에 모아둔 돈
- Available → 지금 쓸 수 있는 돈
- Target → 목표
- Underfunded → 목표까지 부족한 돈
- Reconcile → 거래 확인

## 4. 학생 홈 설계에 주는 영향

나쁜 예:
총 잔액 200

좋은 예:
- 지금 자유롭게 쓸 수 있는 돈 80
- 목표 ‘책갈피’ 60/100
- 다음 주 필요할 돈 40
- 공동체에 보탤 돈 20
- 아직 계획하지 않은 돈 0

학생은 총액보다 ‘선택 가능한 범위’를 본다.

## 5. Zero-Based Planning의 교육적 의미

현재 가진 돈만 배분한다.

Class Money에서는 미래 급여를 미리 써버리는 습관을 막을 수 있다.

규칙:
- 예정 급여는 참고 정보
- 실제 입금 전에는 예산으로 배분 불가
- 대출 모듈을 켠 경우에만 별도 차입자금

이것은 초등학생에게 ‘미래 돈을 이미 가진 것처럼 생각하지 않기’를 가르친다.

## 6. Targets

YNAB Targets는:
- 얼마
- 언제까지
를 목표로 삼고 부족한 정도를 보여준다.

Class Money:
학생 목표:
- 상점 상품
- 가상 경험
- 자유 입력 목표

표시:
현재 40 / 목표 100
매주 15씩 모으면 약 4주

하지만 정확한 미래를 보장하는 문구 대신 현재 설정 기준의 예상으로 표현.

## 7. Underfunded의 시사점

YNAB는 목표에 비해 부족한 카테고리를 눈에 띄게 한다.

Class Money:
‘부족함’을 실패처럼 표시하지 않는다.

예:
‘목표까지 30 더 필요해요.’
‘이번 주 10을 더 넣으면 3주 후 예상.’

교사 대시보드에서는:
구조적으로 모든 학생이 목표를 달성하기 어려운 경제설정을 감지.

## 8. Auto-Assign

YNAB는 목표/과거 사용에 따라 자동 배분을 도울 수 있다.

Class Money에서는 학생의 선택을 빼앗지 않도록:
‘추천 배분’을 제공하고 학생이 확정.

예:
급여 100
추천:
- 자유사용 50
- 목표저축 30
- 다음 주 계획 10
- 공동체 10

[이대로 나누기] [직접 바꾸기]

## 9. Reconcile

실제 계좌와 기록을 맞추는 YNAB의 reconcile 개념은 교실경제에서도 교육적으로 유용하다.

Class Money 활동:
‘이번 주 거래가 맞는지 확인해보세요.’
학생이:
- 급여
- 상점
- 저축
- 정정
을 보고 이상 거래 신고.

이는 금융문해력과 데이터 검증을 동시에 강화.

## 10. Flexibility

YNAB는 계획을 바꾸는 것을 실패가 아니라 정상적인 조정으로 본다.

Class Money도:
목표저축에서 자유사용으로 돈을 옮길 때 ‘실패’라고 하지 않는다.

대신:
‘계획을 바꾸면 목표 도착 예상이 1주 늦어집니다.’
처럼 trade-off를 보여준다.

## 11. Class Money에 가져올 것

가장 강하게:
1. 잔액보다 Available
2. 수입 즉시 목적 배분
3. 목표
4. 부족액/예상기간
5. 추천 배분
6. 계획 변경의 trade-off
7. 거래 확인 활동

가져오지 않을 것:
- 성인 금융용 복잡한 category 체계
- 신용카드 예산 로직
- 월별 회계 UI를 그대로 복제
- 은행계좌 import

## 12. 초등용 단순화 원칙

저학년:
‘쓸 돈 / 모을 돈’

중학년:
‘쓸 돈 / 목표 / 모아둘 돈’

고학년:
‘자유사용 / 목표 / 다음 지출 / 공동체’

카테고리를 무한 생성하게 하지 않고 기본 2~4개에서 시작.

## 13. Craft Anything 후속 실측

- 수입을 category에 assign하는 실제 화면
- Available이 소비결정에 어떻게 노출되는지
- Target 설정
- Underfunded 표시
- Auto-Assign
- overspending 이후 재배분
- 모바일에서 category 정보 밀도

## 14. 현재 판단

YNAB 분석은 Class Money의 학생 홈을 바꿀 수 있다.

Class Money가 단순 ‘학급 통장’이라면:
잔액 → 거래내역 → 상점.

경제교육 도구라면:
목적 → 선택 가능 금액 → 목표 → 거래 → 결과.

후자를 채택하는 것이 더 적절하다.

## 공식 근거
- https://www.ynab.com/guide/foundations-the-ynab-method
- https://support.ynab.com/en_us/getting-started-ynab-basics-and-key-terms-BJCaIHaTZe
