# Craft Anything 기반 후속 실측 조사 프로토콜

## 현재 상태
**실행되지 않음**: 이 문서는 실측 과제 정의다. Craft Anything으로 외부 앱을 직접 열어 화면을 기록하거나 자동 비교를 돌렸다고 주장하지 않는다. 공개 공식 설명을 먼저 정리한 결과는 [벤치마킹](benchmark-2026-11.md)에서 확인한다.

원 프로젝트: https://github.com/storytold/craft-anything

## 사용 원칙
- **Clean Room 모드**로 공개/접근 허용된 화면에서 관찰한 동작·레이아웃·텍스트만 증거화한다.
- 권한 없이 앱 내부 리소스, 비공개 소스, 인증 제한 영역을 우회하지 않는다.
- 원본 이미지·로고·문장·소스코드를 복제하지 않고 제품의 해결 원리만 추출한다.
- 관찰한 것/추정/확인 불가를 분리하고 각 결과에 URL·관찰일·화면폭·시나리오·스크린샷 경로를 기재한다.

## 우선 시나리오 (서비스별 동일한 과제)
1. 교사: 신규 학급 개설 및 학생 25명 등록.
2. 교사: 직업 5개 생성, 급여/주기 설정, 학생 배정.
3. 교사: 전체 25명 지급, 5명 모둠 지급, 1명 잘못 지급한 내역 정정.
4. 학생: 지갑 잔액·입출금 내역 조회.
5. 학생: 상점 상품 주문 → 교사 승인/거절 → 환불 검증.
6. 교사: 경제 수치·거래 내역 내보내기.
7. 학생: 저축목표 설정, 남은 기간/금액 확인(해당 서비스 지원 시).
8. 공통: 360px(폰), 768px(태블릿), 1280px(PC) UI와 키보드 이동.

## 증거 템플릿
```yaml
service: 
url:
observed_at: 
access: public | authorized_account | inaccessible
mode: clean_room
scenario:
viewport: 
steps:
  - action:
    result:
    clicks:
evidence:
  screenshots: []
  notes: []
finding:
confidence: confirmed | inferred | unknown
class_money_implication:
limitations:
```

## 평가 루브릭
각 범주 0~4점(0=사용 불가/매우 불편, 2=보통, 4=우수), 실제 테스트하지 않았으면 **N/A**.
- 교사 업무 효율: 주요 업무 조작 수/소요.
- 학생 이해도: 잔액·거래의 의미, 오류 안내, 학습 도움.
- 접근성: 모바일/태블릿, 키보드, 시각 안내.
- 운영 신뢰성: 중복처리, 승인, 정정, 이력.
- 금융교육 타당성: 소득-지출-저축-선택 연결.
- 공정성·안전성: 학생 권리/개인정보/과열 유도.

총점 비교는 모든 앱에 동일 시나리오를 완료한 경우에만 실시. 제공 기능 부재와 테스트 불가능을 혼동하지 않는다.

## 결과 보관 규칙
- `docs/research/observations/<service>/<date>-<scenario>.md` — 실측 기록
- `docs/research/evidence/<service>/` — 사용 권한이 확보된 스크린샷만
- 비교 결론은 출처/캡처 번호·적용 우선순위·미해결 질문과 함께 문서화.
