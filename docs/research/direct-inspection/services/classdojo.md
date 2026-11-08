# ClassDojo 직접 관찰

기준일: 2026-11-08

## 직접 연 페이지
- https://www.classdojo.com/points/
- https://help.classdojo.com/hc/en-us/articles/205494185-How-to-Set-Up-and-Award-Points-to-Groups
- https://help.classdojo.com/hc/en-us/articles/209619243-How-to-Undo-a-Point

## 홈페이지에서 직접 확인한 포지셔닝
Points page는 기능을 quick and easy feedback으로 설명한다.

첫 핵심 행동:
- student success 관찰
- custom skill
- 즉시 point
- report/trend

Class Money가 참고할 부분은 금융기능이 아니라 **교사가 수업을 끊지 않는 고빈도 입력 UX**다.

## Group 구조
공식 Help의 Web 흐름:
1. Open class
2. Groups tab above student tiles
3. Add group
4. 학생 선택
5. Create group

Award:
Group → Award group → Skill.

중요하게도 Group report는 별도 존재하지 않고 group point가 참여 학생 각각의 report에 기록된다.

즉 ClassDojo Group은 경제적 공동계좌가 아니라 **대상 선택 집합**이다.

## Undo 구조
최근 잘못 준 point는 현재 화면에서 바로 Undo.
과거 오류는 Reports에서 수정.

시간적으로 가까운 실수는 즉시 복구하고, 오래된 기록 수정은 detailed history로 보낸다.

Class Money에서는 이 UX를 가져오되 원장 자체를 삭제하지 않고 reversal을 생성하는 편이 안전하다.

## 공개 GitHub 직접 감사
공식 organization classdojo를 확인했다.

공개 repositories에는:
- policies
- agenda
- database
- photo-collage
- 여러 infra/library
가 있으나 현재 Points 제품 UI source는 공개돼 있지 않다.

공개 library를 현재 product architecture로 역추론하지 않는다.

## Class Money에 가져올 것
- student tile을 action surface로 사용
- group selector
- preset reason
- recent undo
- quick surface / detailed report 분리
- 교사용 고빈도 action 최소화

## 가져오지 않을 것
- behavior point를 자동으로 money로 환산
- negative point를 automatic fine으로 전환
- 공개 자산 ranking

## 현재 미확인
- 실제 teacher login 후 class tile density
- mobile award animation
- projector mode
- report filtering depth