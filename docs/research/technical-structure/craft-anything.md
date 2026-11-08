# Craft Anything — 파일·폴더·기술 구조

정확도: **A — 공식 source 직접 확인**
공식 repository: storytold/craft-anything의 실제 tree/source를 직접 확인.

## Repository 상위 구조

- apps/craft-anything — Desktop application
- apps/craft-anything-cli — CLI
- apps/craft-anything-web — Web application
- crates/engine — tool registry, session, Clean Room policy, website/browser/project tools
- crates/engines — CDP/Ghidra/JADX/Frida 등 분석 engine adapter
- crates/analysis — JavaScript/HAR/native analysis
- crates/evidence — evidence model
- crates/formats — file/binary format decoder
- crates/ai — build/rebuild orchestration
- crates/mcp — MCP integration
- crates/platform — filesystem/process/capture/platform helpers
- docs — architecture/status/documentation

## 직접 확인한 핵심 파일

- crates/engine/src/clean_room.rs
  - Clean Room 허용 tool allowlist
  - 내부 source/filesystem 접근 제한

- crates/engine/src/tools/website_tools.rs
  - web_site_open
  - web_site_capture
  - web_page_states_capture
  - screenshot/layout/assets/forms/links 수집

- crates/engine/src/tools/browser_tools.rs
  - browser 관련 tool implementation

- crates/ai/src/rebuild/study.rs
  - website study orchestration
  - route 탐색
  - multi-width capture
  - Deep mode 추가분석

- docs/STATUS.md
  - 현재 구현/검증 상태

## 기술 구조

핵심 language/runtime:
- Rust workspace
- desktop / CLI / web frontends
- browser/CDP 기반 external observation
- evidence-first architecture
- MCP layer

## Website Study 외부 파이프라인

Website URL
→ Open private browser
→ Multi-width capture
→ Visible layout/token extraction
→ Menu/dialog/tab state capture
→ Same-site route traversal
→ Deep mode: JavaScript/routes/endpoints/network watch

## 구조적 특징

1. Tool execution과 AI orchestration이 분리.
2. Evidence record와 결과물을 분리.
3. Clean Room은 prompt 규칙이 아니라 engine-level allowlist.
4. 웹 분석도 single screenshot이 아니라 responsive route/state graph로 취급.

## Class Money 연구에서의 역할

이 repository 자체를 복제하는 것이 아니라 경쟁서비스 증거 수집 포맷의 기준으로 사용한다.