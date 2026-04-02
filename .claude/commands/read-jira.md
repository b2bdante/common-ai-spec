Jira 티켓 $ARGUMENTS 의 내용을 읽어와서 요구사항을 분석해주세요.

## Jira API 호출

아래 curl 명령으로 티켓을 조회하세요:

```bash
curl -s -u "$JIRA_EMAIL:$JIRA_API_TOKEN" \
  "$JIRA_BASE_URL/rest/api/3/issue/$ARGUMENTS?expand=renderedFields"
```

## 출력 형식

1. **티켓 요약**: 제목, 상태, 타입, 담당자, 우선순위
2. **요구사항 정리**: 설명에서 핵심 요구사항을 bullet point로 정리
3. **서브태스크**: 있으면 목록과 상태 표시
4. **주요 댓글**: 최근 댓글에서 의사결정/추가 요구사항 추출