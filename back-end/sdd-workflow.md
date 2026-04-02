---
description: SDD 개발 스킬. Jira 티켓 또는 자연어 요구사항 기반으로 컨벤션/용어사전을 준수하며 SDD 순서대로 분석/설계/구현합니다.
---

이 프로젝트를 SDD(Spec-Driven Development) 방식으로 개발합니다.

## 0단계: 프로젝트 식별

`settings.gradle.kts` (또는 `settings.gradle`)에서 프로젝트명을 추출하세요:

```bash
grep -oP '(?<=rootProject\.name\s*=\s*")[^"]+' settings.gradle.kts 2>/dev/null || grep -oP '(?<=rootProject\.name\s*=\s*")[^"]+' settings.gradle 2>/dev/null
```

추출된 값을 `{SERVICE_NAME}`으로 사용합니다. 이후 모든 단계에서 이 값을 참조하세요.

## 1단계: 컨텍스트 로드

아래 3개 파일을 반드시 읽고 숙지하세요. 이후 모든 분석/설계/구현에서 이 컨벤션과 용어를 준수해야 합니다.

1. `common-ai-spec/back-end/convention.md` — 백엔드 코딩 컨벤션
2. `common-ai-spec/glossary/glossary.md` — 공통 도메인 용어사전
3. `common-ai-spec/back-end/glossary/{SERVICE_NAME}.md` — 서비스 전용 용어사전

3번 파일이 존재하지 않으면 사용자에게 알리고, 공통 용어사전만으로 진행하세요.

## 2단계: 요구사항 파악

입력: `$ARGUMENTS`

**입력이 Jira 티켓 패턴(`[A-Z]+-\d+`)인 경우:**

```bash
curl -s -u "$JIRA_EMAIL:$JIRA_API_TOKEN" \
  "$JIRA_BASE_URL/rest/api/3/issue/$ARGUMENTS?expand=renderedFields"
```

응답을 파싱하여 아래 형식으로 요구사항을 정리하세요:
- 티켓 요약 (제목, 상태, 타입, 담당자)
- 핵심 요구사항 (bullet point)
- 서브태스크 (있으면)
- 주요 댓글에서 의사결정/추가 요구사항 추출

**입력이 자연어인 경우:**

입력 텍스트를 요구사항으로 직접 사용합니다. 핵심 변경사항과 영향 범위를 정리하세요.

**입력이 비어있으면:** 사용자에게 요구사항을 입력하도록 요청하세요.

## 3단계: SDD 분석 및 설계

요구사항을 기반으로 아래 SDD 순서에 따라 영향 분석과 구현 계획을 수립하세요. 각 Phase 분석 결과를 사용자에게 보여주고 확인을 받은 후 다음 단계로 진행합니다.

### Phase 1: 엔티티 분석

- 새 엔티티가 필요한지 판단
- 기존 엔티티 수정이 필요한지 판단
- 관계(1:1, 1:N, M:N) 변경 여부 분석
- 결과를 사용자에게 제시하고 확인

### Phase 2: Entity + Flyway 마이그레이션

- Entity 클래스 생성/수정
    - `@Entity` only (no `@Table`), 예약어는 복수형
    - Enum은 `@Enumerated(EnumType.STRING)` 사용
    - `BaseTimeEntity` 상속
- Flyway SQL 작성
    - 경로: `src/main/resources/db/migration/release/` 하위 최신 릴리즈 폴더
    - 파일명: `V{yyyy}.{MM}.{dd}.{티켓번호}__{description}.sql`
    - TimeZone: UTC, datetime 타입

### Phase 3: Domain Tree

아래 순서대로 생성/수정:

1. **Repository** — JpaRepository 인터페이스
2. **Service Interface** — 도메인 서비스 인터페이스 정의
3. **ServiceImpl** — `@Service`, 구현체
4. **Mapper** — Entity ↔ DTO 변환, `to` prefix 함수명
5. **DTO** — 내부 레이어 데이터 전달용 (필요 시)

### Phase 4: Usecase

- 기존 Usecase 수정 vs 새 Usecase 생성 결정
- `@Usecase` 어노테이션 사용 (프로젝트 커스텀 어노테이션)
- 여러 Service를 조합할 때는 `@Facade` 사용 검토
- Usecase → Facade(선택) → Service → Repository 레이어 구조 준수

### Phase 5: Controller + VO (API 필요 시)

- Request/Response VO 정의
- Controller에서는 VO로 외부 통신
- URL: kebab-case, 복수형, HTTP Method로 기능 표현
- 함수 인자 2개 이상이면 줄바꿈, 5개 초과 시 DTO/VO로 전달

## 4단계: 구현

사용자가 설계를 승인하면 Phase 2 → 3 → 4 → 5 순서대로 코드를 작성합니다.

**컨벤션 체크리스트** (코드 작성 시 매번 확인):

- [ ] 패키지명: all lowercase (`sourcing`, `shippinglabel`)
- [ ] 클래스명: PascalCase, 명사
- [ ] 메서드명: camelCase, 동사로 시작
- [ ] 변수명: camelCase, 명사
- [ ] 상수: UPPER_SNAKE_CASE
- [ ] Entity: `@Entity` only, 예약어 복수형, Enum은 String
- [ ] Mapper 함수: `to` prefix
- [ ] Controller 제외 모든 함수에 return type 표기
- [ ] 용어사전의 엔티티명/설명 준수

**도메인 패키지 구조:**

```
domain/{도메인명}/
├── constant/       # Enum, 상수
├── controller/     # REST Controller
├── dto/            # 내부 레이어 전달 DTO
├── entity/         # JPA Entity
├── exception/      # 도메인 예외
├── mapper/         # Entity ↔ DTO 변환
├── repository/     # JPA Repository
├── service/        # Service Interface + Impl
├── usecase/        # @Usecase
├── facade/         # @Facade (선택)
└── vo/             # Request/Response VO
```