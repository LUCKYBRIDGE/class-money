# 직접 사이트·리포지토리 관찰

기준일: 2026-11-08

이 폴더는 기존의 공식 문서 요약보다 한 단계 높은 **직접 관찰 증거**를 모은다.

## 증거 수준

- **S1 Site-direct** — 해당 공개 사이트 URL을 실제로 열어 현재 페이지 구조·텍스트·링크·노출 순서를 관찰.
- **R1 Repo-direct** — 공식 GitHub 저장소의 실제 tree/file/source를 열어 구조·코드를 관찰.
- **D1 Docs-direct** — 공식 도움말/가이드/PDF를 직접 열어 실제 단계·상태·정책을 관찰.
- **L0 Login unknown** — 로그인 후 화면/동작이라 현재 미확인.
- **I1 Inference** — 관찰된 외부 동작을 설명하기 위한 추론. 내부 구현 사실 아님.

## 원칙

1. 검색 요약만으로 결론 내리지 않는다.
2. 상용 서비스 이름과 같은 비공식 GitHub 프로젝트를 공식 제품 소스로 오인하지 않는다.
3. 공개 저장소가 있더라도 현재 제품 본체의 소스인지 확인한다.
4. 사이트의 실제 first fold, 메뉴, 기능 설명 순서, 버튼, 상태 표현을 기록한다.
5. PDF는 원문과 페이지 화면을 함께 확인한다.
6. 로그인 후 화면을 보지 못했으면 UI를 본 것처럼 쓰지 않는다.
7. Craft Anything Clean Room이 실제로 수집하는 항목과 맞춰 관찰 필드를 유지한다.

## 문서

- [Craft Anything 저장소 직접 분석](craft-anything-repository.md)
- [경쟁 서비스 공개 사이트 직접 관찰](service-sites-2026-11-08.md)
- [공개 GitHub 저장소 감사](public-repository-audit.md)
- [직접 관찰 뒤 Class Money 설계 보정](class-money-corrections.md)

## Craft Anything과의 정렬

직접 확인한 Craft Anything v0.5.0 소스에서 웹사이트 Study는 다음 구조다.

Website URL
→ private browser open
→ multi-width capture
→ visible layout/tokens/links/forms
→ menu/dialog/tab states
→ same-site route capture
→ Deep mode인 경우 JavaScript/routes/endpoints/watch 추가

따라서 향후 실제 Clean Room 계측에서도 이 폴더의 동일 서비스 문서에 다음을 추가한다.

- viewport
- screenshot
- layout
- visible text
- opened states
- route
- click path
- observed date