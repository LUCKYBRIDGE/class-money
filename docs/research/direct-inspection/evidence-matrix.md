# 직접 관찰 증거 매트릭스

기준일: 2026-11-08

| 서비스 | 공식 공개 사이트 직접 확인 | 공식 Help/가이드 직접 확인 | PDF 화면 확인 | 공식 GitHub 조직/Repo 확인 | 현재 제품 본체 Source 확인 | 로그인 뒤 실제 UI |
|---|---:|---:|---:|---:|---:|---:|
| ClassCoin | O | O | - | 검색 감사 | X | X |
| ClassBank | O | O | - | 검색 감사 | X | X |
| Cashroom | O | O | - | 검색 감사 | X | X |
| Banqer Primary | 제한적 | O | - | O | X | X |
| ClassCents | O | O | - | 검색 감사 | X | X |
| My Classroom Economy | O | O | O | 검색 감사 | X | 해당 없음/종이 중심 |
| ClassDojo | O | O | - | O | X | X |
| Greenlight | O | O | - | 검색 감사 | X | X |
| Rooster Money | O | O | - | 검색 감사 | X | X |
| Revolut Kids & Teens | O | O | - | 검색 감사 | X | X |
| 토스 유스 | O | 공식 제품 페이지 | - | 검색 감사 | X | X |
| YNAB | O | O | - | O | API SDK/Starter Kit만 O | X |

## 해석

- 현재 가장 강한 repository-level 제품근거는 YNAB의 공식 API SDK다.
- Banqer와 ClassDojo의 공식 GitHub 조직은 확인했지만 현재 제품 본체 source는 공개돼 있지 않다.
- My Classroom Economy는 앱 source보다 공식 PDF/인쇄 artifact가 실제 시스템 구조를 설명하는 1차 증거다.
- 나머지 상용 서비스는 public site + official help를 주 근거로 사용한다.
- 로그인 뒤 실제 UX를 보지 못한 항목은 screen layout/click count를 확정하지 않는다.

## 다음 증거 레벨

가능한 환경에서 서비스별 E2 실측:
- 360 / 768 / 1280 viewport
- first fold screenshot
- menu/dialog/tab state
- key task click path
- success/error/recovery state
- keyboard/touch target
- shared-device logout/switch

이 실측 전에는 UX 점수를 확정하지 않는다.