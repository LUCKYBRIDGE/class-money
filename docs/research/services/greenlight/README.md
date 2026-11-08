# Greenlight — Canonical Service Folder

> 이 폴더를 Greenlight 분석의 **최신 정본(canonical)**으로 사용한다. 기존 flat/dossier/ui-ux/structure 문서는 세부 근거와 이전 분석을 보존하기 위해 유지한다.

**성격:** 아동 돈 배분·목표·권한  
**증거 수준:** C — 소비자 제품 source 비공개

## 한 문장 구조

수입을 Spend/Savings/Goal 등에 배분하고, Chore 상태와 Reward 지급, 자녀별 Permission을 분리한 가족 금융.

## 폴더 문서

1. [페이지·내비게이션](01-pages-navigation.md) — 어떤 페이지/화면이 있고 어떻게 이어지는가.
2. [UI·UX·버튼/컨트롤](02-ui-ux-controls.md) — 사용자가 무엇을 보고 누르며 어떤 피드백을 받는가.
3. [기능·흐름·상태](03-features-flows.md) — 기능 간 의존관계와 상태전이.
4. [파일·폴더·기술 구조](04-technical-structure.md) — 공개 source와 외부에서 확인되는 기술 모듈.
5. [얽힌 문제와 해결방식](05-complexity-solutions.md) — 제품이 실제 복잡성을 어떤 방식으로 풀었는가.
6. [근거·미확인·기존 문서](06-evidence-unknowns.md) — 확인범위와 후속 실측.

## 분석 원칙

- 공개 화면/공식 Help/공식 source에서 확인된 사실과 추론을 분리한다.
- 공개 source가 없으면 실제 내부 파일명·framework·DB를 만들어내지 않는다.
- UI 디자인 복제가 아니라 문제 해결 원리와 구조만 가져온다.
- 로그인 후 실제 화면을 보지 못한 영역은 미확인으로 남긴다.
