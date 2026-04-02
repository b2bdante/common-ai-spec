Jira 티켓 $ARGUMENTS 기반으로 delibird-shipment를 개발합니다.

## 1단계: Jira 티켓 읽기

```bash
curl -s -u "$JIRA_EMAIL:$JIRA_API_TOKEN" \
  "$JIRA_BASE_URL/rest/api/3/issue/$ARGUMENTS?expand=renderedFields"
```

응답을 파싱하여 요구사항을 정리하세요.

## 2단계: 컨텍스트 참조

아래 문서를 읽고 컨벤션과 용어를 숙지하세요:

- `common-ai-spec/back-end/convention.md` (백엔드 코딩 컨벤션)
- `common-ai-spec/glossary/glossary.md` (공통 도메인 용어)
- `common-ai-spec/back-end/glossary/delibird-shipment.md` (서비스 전용 용어)

## 3단계: 구현 계획 수립

티켓 요구사항을 분석하고, 컨벤션에 맞는 구현 계획을 세우세요:
- 영향받는 레이어 (api/core/infrastructure/mapper)
- 생성/수정할 클래스 목록
- 테스트 계획

## 4단계: 코드 작성

컨벤션을 준수하여 코드를 작성하세요.

## 서비스 개요

배송 라벨 생성 서비스. 다중 배송사 라벨 발행, 통관 신고(Custom/CustomItem), 배송 요금 계산, ShipHero 연동, B2B 라벨 요청 처리.