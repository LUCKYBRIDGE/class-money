# ClassBank — 기능 얽힘·UI·UX 심층 분석

기준일: 2026-11-08  
핵심: **모듈형 복잡성 관리 + 역할 기반 UI**

## 1. 기능 관계
\`\`\`mermaid
flowchart LR
 C[Class] --> ST[Students]
 ST --> BO[Bonuses/Fines]
 ST --> JO[Jobs]
 ST --> BI[Bills]
 ST --> SA[Savings/Interest]
 ST --> SH[Store]
 BO --> TR[Transactions]
 JO --> TR
 BI --> TR
 SA --> TR
 SH --> TR
 HE[Student Helpers] --> JO
 HE --> SH
 HE --> TR
\`\`\`

기능이 많지만 모든 반이 전부 사용하지 않는다는 전제에서 설계된다.

## 2. 복잡함을 푸는 핵심: Progressive Disclosure
공식 시작 가이드는 Class→Students→Bonuses→Store를 먼저 권하고 Jobs/Bills/Savings/Co-teachers는 나중에 추가하도록 한다. 이것은 ‘기능 목록’이 아니라 **작동 가능한 최소 경제부터 만들게 하는 온보딩**이다.

Class Money:
- 첫 설정에서 3~4개 과업만 완료.
- 고급 모듈은 홈에서 숨김.
- 기능을 켤 때 학생 화면 변화도 미리보기.

## 3. 정보구조
Jobs는 Class 안, Bills는 Setup, Savings는 class 설정에서 켜는 식으로 기능이 실제 운영 맥락에 배치된다.

장점: 기능 내부에서 설정을 찾기 쉽다.  
위험: 새 사용자는 “어디에서 켜지?”를 기억해야 한다.

Class Money 개선:
- 각 기능 안에 상세설정.
- 별도 ‘경제 기능’ 화면에는 ON/OFF와 상태, 바로가기만 제공.

## 4. Student Helpers — 복잡한 관리자 UI를 역할별로 잘라냄
공식 역할:
- Store Clerk → 주문 승인/상품 편집
- HR Representative → 직업게시판/직업 편집
- Banker → 거래 전송

핵심 UX는 ‘학생에게 교사화면을 보여주고 권한을 막는 것’이 아니라 **필요한 영역만 보이게 한다는 것**이다.

Class Money:
일반학생 / 상점도우미 / 직업도우미 / 은행도우미의 navigation 자체를 다르게 구성.

## 5. 경제 설정의 복잡성
ClassBank는 학년별 급여·비용·상품 가격 범위를 별도 가이드로 제공한다. 도움말을 읽어 숫자를 옮기는 방식은 진입에 도움은 되지만 맥락 전환이 필요하다.

Class Money 개선:
입력 즉시
- 월 정기수입
- 정기지출
- 여유액
- 대표상품 구매 예상기간
- 구조적 적자
를 같은 화면에서 계산한다.

## 6. 학생 UI
공식 학생 튜토리얼은 로그인, 계좌관리, 직업지원, 상점, 저축처럼 **학생의 실제 과업**으로 나눈다.

Class Money는 학년별 용어 레이어를 둘 수 있다.
- 저학년: 내 돈 / 일하기 / 모으기 / 쓰기
- 고학년: 지갑 / 직업 / 저축 / 상점 / 거래내역

## 7. 선택형 모듈이 만드는 UX 문제
기능이 꺼져 있으면 설명에서 본 메뉴가 실제 반에는 없을 수 있다.

권고:
- 미사용 기능은 기본적으로 완전 숨김.
- 활성화 순간 1회 소개카드.
- 학생에게 ‘잠긴 메뉴’ 수십 개를 보여주지 않음.
- 교사는 활성화 전 학생화면 preview 가능.

## 8. Bills UX에서 배울 안전 원칙
공식 철학은 비용을 못 내도 교실 자원 접근을 박탈하지 않는다는 것이다.

Class Money 미납 UI:
“실패/벌”보다 “이번 계획에서 20이 부족합니다. 어떤 선택을 바꿀까요?”처럼 학습 문제로 표현.

## 9. 가져올 UI·UX 원칙
- 최소기능부터 시작.
- 역할별 화면 자체를 다르게.
- 추천값을 실시간 경제 시뮬레이션으로 발전.
- 비활성 기능은 숨김.
- 기능 활성화 시 1회 설명.
- 고정비 실패를 처벌 UI로 만들지 않음.

## 공식 근거
- https://help.classbank.com/en/articles/6499058-how-do-i-get-started-with-classbank
- https://help.classbank.com/en/articles/5949828-student-helper-jobs-banker-hr-manager-and-store-clerk
- https://help.classbank.com/en/articles/6499914-classbank-suggested-settings
- https://help.classbank.com/en/articles/12996486-how-do-students-use-classbank-student-video-tutorials
