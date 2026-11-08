# Craft Anything 저장소 직접 분석

기준일: 2026-11-08
대상: https://github.com/storytold/craft-anything
직접 확인: GitHub repository tree, README, Clean Room source, website tool source, rebuild study source, STATUS, 최신 release.

## 1. 저장소 전체 성격

공개 저장소를 직접 열어보면 Craft Anything은 단일 UI 앱이 아니라 Rust workspace다.

주요 축:
- apps/craft-anything — desktop app
- apps/craft-anything-cli — CLI
- apps/craft-anything-web — web app
- crates/engine — tool registry, sessions, Clean Room policy, browser/runtime/project tools
- crates/engines — CDP/Ghidra/JADX/Frida 등 engine adapters
- crates/analysis — JavaScript/HAR/native analysis
- crates/evidence — evidence model
- crates/formats — binary/file format decoders
- crates/ai — build/rebuild orchestration
- crates/mcp — MCP layer
- crates/platform — capture/process/filesystem/platform helpers

즉 제품 핵심은 단순 AI 프롬프트가 아니라 **증거 수집 엔진 + 도구 레지스트리 + rebuild orchestration**이다.

## 2. Clean Room은 코드 레벨 allowlist

직접 확인한 crates/engine/src/clean_room.rs에서 Clean Room 허용 tool id가 명시적 목록으로 정의되어 있다.

웹 관련 허용 도구:
- web_site_open
- web_site_capture
- web_page_states_capture
- web_page_screenshot_take
- web_pixels_compare
- web_site_close
- web_walkthrough_check

내부 코드·파일·페이지 소스를 보는 도구는 Clean Room 허용목록 밖에 있고, 이 모드에서 거절하도록 구현되어 있다.

### 연구에 주는 의미

Class Money 분석에서도 반드시 다음을 나눈다.
- 실제 공개 화면에서 본 것
- 공식 공개 source에서 확인한 것
- 외부 동작으로부터 추론한 것
- 로그인/비공개라 모르는 것

## 3. web_site_capture가 실제로 수집하는 것

직접 확인한 crates/engine/src/tools/website_tools.rs의 설명과 구현 기준:

- 요청한 여러 width의 full-page PNG
- rendered HTML
- font family, size, weight
- text/background colors
- border radius
- shadow
- spacing
- content width
- CSS custom properties
- CSS가 layout을 전환하는 width
- width별 page/heading/text size
- section padding/gap/content column/items per row
- visible landmark, heading, control, image의 위치
- image/stylesheet/script/font/request asset list
- links
- form outline

Clean Room에서는 form value, cookie, storage value를 읽지 않는다.

### Class Money 경쟁분석 적용

기존의 'UI가 단순하다' 같은 문장을 다음 측정값으로 교체할 수 있다.
- 최상위 navigation 항목 수
- 핵심 CTA의 위치
- content column width
- breakpoint
- card density
- section gap
- heading hierarchy
- modal/menu/tab 상태

## 4. web_page_states_capture

소스상 visible menu, pop-up, tab, collapsed section 가운데 aria-expanded, aria-haspopup, unselected tab, summary 같은 상태를 하나씩 열어 screenshot과 변화 상태를 기록한 뒤 원상복구한다.

임의의 form submit을 누르는 일반 crawler가 아니다.

경쟁서비스에서는 다음을 관찰하기 좋다.
- hamburger navigation
- advanced settings accordion
- modal
- store filter/tab
- help drawer
- hidden module menu

## 5. 실제 Website Study 파이프라인

crates/ai/src/rebuild/study.rs를 직접 확인하면 Website Study는 다음 순서다.

1. web_site_open
2. web_site_capture
3. desktop 및 phone width에서 web_page_states_capture
4. 시작 페이지의 same-site link에서 route 선택
5. route별 multi-width capture
6. 여유가 있으면 한 단계 더 깊은 route 탐색
7. Deep mode라면 JavaScript 분석과 10초 page watch를 추가하고 how-it-works 문서 생성

즉 Craft Anything의 웹 분석은 landing screenshot 하나가 아니라 **route graph + responsive state + visible interaction state**를 조사하도록 설계되어 있다.

## 6. Clean Room과 Deep의 실제 차이

Clean Room:
- visitor-visible screenshots
- visible text/layout
- menus/dialogs/tabs
- 외부에서 보는 runtime state

Deep:
- loaded JavaScript bundle 분석
- module/route/endpoints
- source map
- network/WebSocket observation

상용 경쟁서비스는 Clean Room 관점만으로도 제품 분석에 충분한 부분이 많다. 공식 공개 repository가 있을 때만 R1 source 분석을 별도로 수행하는 것이 안전하다.

## 7. Evidence-oriented 구조

README와 source 모두 결과를 answer 하나가 아니라 evidence record로 다룬다.

핵심 개념:
- authority
- confidence
- coverage
- limitation
- location

Class Money 연구문서에서도 최소한 observed / inferred / unknown을 구분하는 이유다.

## 8. 현재 release와 상태

GitHub release를 직접 확인한 결과:
- 최신 release: v0.5.0
- published: 2026-11-06
- macOS / Windows / Linux / FreeBSD 배포파일 제공

STATUS는 2026-11-05 갱신본이며 early alpha로 설명한다. Desktop/CLI/MCP와 website workflow가 동작한다고 적혀 있지만 일부 agent/backend/runtime 경로는 실제 live verification이 제한되어 있다고 밝힌다.

따라서 Craft Anything 자체의 결과도 evidence와 limitation을 함께 검토하는 것이 맞다.

## 9. 이번 분석 프로젝트에 적용하는 방식

각 서비스에서:
1. public home
2. product/how-it-works
3. help/getting-started
4. student-facing explanation
5. settings/permissions explanation
6. error/recovery docs
7. mobile/shared-device docs
를 직접 연다.

공개 GitHub repository가 있다면:
1. official ownership
2. 현재 제품과의 관련성
3. repository tree
4. model/schema
5. public API
6. 최근 activity
를 확인한다.

## 10. 현재 실행 한계

현재 작업환경에는 Chromium은 있지만 Craft Anything CLI와 Rust toolchain이 기본 설치되어 있지 않았다. 공식 v0.5.0 release는 직접 확인했지만 이 세션에서 Craft Anything binary를 실행해 capture artifact를 생성한 단계까지는 진행하지 않았다.

따라서 현재의 직접관찰 수준은:
- 공개 사이트 페이지 직접 열기
- 공식 GitHub repository/source 직접 열기
이고, Craft Anything의 multi-width pixel/layout capture 실행은 후속 E2 실측으로 남긴다.