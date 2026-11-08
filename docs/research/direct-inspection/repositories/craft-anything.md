# Craft Anything repository 직접 분석

상세 분석은 ../craft-anything-repository.md에 있다.

## 직접 확인한 핵심 repository 구조
- apps/craft-anything
- apps/craft-anything-cli
- apps/craft-anything-web
- crates/engine
- crates/engines
- crates/analysis
- crates/evidence
- crates/formats
- crates/ai
- crates/mcp
- crates/platform

## 실제 source에서 확인한 웹 분석 파이프라인
crates/ai/src/rebuild/study.rs:
web_site_open
→ web_site_capture
→ desktop/phone states capture
→ same-site route capture
→ Deep mode에서 JS analysis + 10초 watch.

## Clean Room enforcement
crates/engine/src/clean_room.rs에서 허용 tool allowlist를 코드로 관리한다.

## website capture
crates/engine/src/tools/website_tools.rs에서 여러 width screenshot, rendered layout/tokens, links/forms, states를 수집한다.

## 현재 릴리스
2026-11-06 v0.5.0 공개.

## 이 프로젝트에서의 사용 원칙
Class Money 경쟁서비스는 우선 Clean Room 관점으로 관찰하고, 공식 공개 source가 있는 경우에만 repository-level 분석을 추가한다.