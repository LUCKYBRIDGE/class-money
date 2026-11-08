# Banqer 공식 공개 repository 직접 분석

기준일: 2026-11-08

## 공식 organization
https://github.com/Banqer

## 직접 확인한 angular_sample
README가 명시적으로:
- interview용 code sample
- Banqer High에서 과거 사용한 obsolete code
라고 설명한다.

따라서 현재 Banqer Primary source로 사용하면 안 된다.

## sample source에서 볼 수 있는 것
simple-quiz.component.ts는:
- Angular component
- questions input
- completion event
- local browser storage로 current question index 보존
- correct/incorrect callback
- question validation
을 포함한다.

이 코드는 과거 학습 quiz component의 설계 예일 뿐 현재 제품 구조 증거는 아니다.

## 다른 공개 repositories
ui-select-banqer는 Angular 1.5용 historical working copy.

## 판정
공식 조직의 오래된 기술 artifact가 있다는 사실과 현재 product stack을 구분해야 한다.

Class Money 분석에서는 Banqer의 현재 동작은 공식 사이트/Help에서만 판단한다.