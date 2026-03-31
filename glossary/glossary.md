# 용어사전

## 공통 도메인 용어

### 사용자 / 인증

| 용어 | 설명 |
|------|------|
| User | 인증된 사용자의 공통 인터페이스 (getUserId, getUsersName, getRole, getService) |
| Admin | 내부 관리자 사용자 |
| Customer | 최종 고객/비즈니스 계정 (이메일, 회사 정보, 주소, 배송 타입, 할인율) |
| Seller | 셀러/판매자 (샵 제목, 로고, 통화, 수수료 정책) |
| Token | 인증 토큰 (access/refresh token, 사용자 정보, 역할, 서비스 범위) |
| Staff | 창고 직원 |

### 주문

| 용어 | 설명 |
|------|------|
| Orders | 주문 (셀러, 구매자 정보, 주소, 결제 방법, 상태, 총액 KRW/USD). 예약어이므로 복수형 사용 |
| OrderItem | 주문 내 개별 항목 (상품명, 가격, 수량, HS 코드, 중량) |
| OriginOrders | 상위 서비스(WEBUY, GLOBAL_CHECKOUT 등)에서 발생한 원본 주문 |
| BuyRequest | 고객의 구매 대행 요청 (프록시 구매) |
| BundleOrder | 합배송을 위해 여러 구매 대행 요청을 묶은 번들 주문 |
| Cart | 구매할 상품이 담긴 장바구니 |

### 상품

| 용어 | 설명 |
|------|------|
| Product | 상품 (이름, 이미지, 가격, 재고). 서비스에 따라 크롤링 상품 또는 판매 상품 |
| ProductOption | 상품의 옵션/변형 (옵션명, 추가 가격, 재고) |
| ProductKit | 세트/번들 상품 정의 (SKU, 이름, 킷 타입) |
| ProductBarcode | 해외 상품 코드와 국내 상품 코드/바코드 매핑 |
| HscodeManager | HS 코드 관리/조회 (통관 분류용) |

### 배송

| 용어 | 설명 |
|------|------|
| Shipment | 핵심 배송 엔티티 (고객, 주문, 배송사, 추적, 주소, 중량, 비용, 상태) |
| ShipmentItem | 배송 내 개별 항목 (이름, 가격, 수량, HS 코드, 원산지 국가) |
| ShipmentHistory | 배송 상태 변경 감사 추적 (작성자, 메시지) |
| Carrier | 배송사 (이름, 코드, 체적 중량 제수, 라벨 서비스 타입) |
| CarrierService | 배송사의 특정 서비스 (예: FedEx International Priority) |
| Address | 물리적 배송 주소 (이름, 거리, 도시, 주/도, 우편번호, 국가, 전화번호) |
| ShippingLabel | 생성된 배송 라벨 기록 |
| ShippingPrice | 배송비 내역 (원가, 고객가, 마크업, 유류할증료) |
| Shipback | 반송 요청 (배송 ID, 고객, 창고, 사유) |
| Warehouse | 물리적 창고/풀필먼트 센터 (이름, 회사, 주소, 연락처) |
| Country | 국가 참조 데이터 (코드, 이름, 전화 코드) |
| ShippingCountry | 국가 코드-국가명 매핑 및 기본 국내 배송사 |

### 패키지

| 용어 | 설명 |
|------|------|
| Packages | 창고에 보관 중인 물리적 소포 |
| PackageItem | 패키지 내 개별 항목 |
| PackageEvent | 패키지 상태 변경 이벤트 |
| PackageFee | 패키지 관련 수수료 (핸들링, 서비스) |
| Inclusion | 패키지에 포함/합포장된 항목 |
| Box | 배송 박스 규격 (치수, CBM, 중량) |

### 결제

| 용어 | 설명 |
|------|------|
| Payment | 결제 레코드 (주문번호, 결제금액, 결제 방법, 상태: CREATED/PAID/CANCEL/PARTIAL_CANCELED) |
| Refund | 결제 환불 기록 (금액, 사유) |
| Coupon | 할인 쿠폰 (셀러, 할인 방식, 예산, 유효 기간, 코드 타입) |
| Point | 고객 적립/리워드 포인트 잔액 |
| PointHistory | 포인트 적립/사용 거래 이력 |
| Transaction | 금융 거래 기록 (결제, 수수료) |
| Currency | 환율 데이터 |

### 통관 / 수출

| 용어 | 설명 |
|------|------|
| Custom | 통관 신고 정보 (내용물 타입, 포장 타입, 배송 타입, 수출자) |
| CustomItem | 통관 신고 개별 항목 (수량, 이름, HS 코드, 원산지, 가격) |
| ExportDeclaration | 수출 통관 신고 (사업자 등록, 수출자 이름/주소, 신고번호, 상태) |
| Incoterms | 배송사 서비스별 인코텀즈 설정 (DDP/DAP 지원) |

### 추적

| 용어 | 설명 |
|------|------|
| Shipment (tracking) | 추적 엔티티 (배송사, 송장번호, 태그, 등록/추적 상태, 동기화 일자) |
| CarrierConfiguration | 배송사 타입과 추적 API 대상 시스템 매핑 |
| OrderTracking | 주문 추적 이벤트 (상태 코드, 프로바이더, 위치, 태그/서브태그, 타임스탬프) |
| TrackingNumberRange | 배송사 송장번호 할당 범위 (시작/끝/현재) |

### 요금 / 정산

| 용어 | 설명 |
|------|------|
| Rate | 국가별 중량 기준 배송 요금표 |
| CoreCarrierBaseRate | 창고/배송사/중량/존별 기본 배송 요금 |
| CoreCustomerMarkUp | 고객별 배송비 마크업 |
| CoreShippingZone | 목적지 국가/우편번호와 배송 존 매핑 |
| CoreDimFactor | 배송사 서비스별 체적 중량 계수 |
| CountryHsCodeTariff | 특정 국가/HS 코드의 관세율 |
| CountryMutualTariff | 국가별 일반/상호 관세율 |
| Invoice | 고객 청구서 (청구서 번호, 금액, 정산 상태) |
| MarkUpSetting | 배송비 마크업 설정 |

### 연동 / 인프라

| 용어 | 설명 |
|------|------|
| QueueMessageHistory | SQS 메시지 처리 이력 (페이로드, 큐 URL, 메시지 ID, DLQ 여부) |
| InboundApiLog | 들어오는 API 요청 로그 (endpoint, method, 요청/응답, 실행 시간) |
| OutboundApiLog | 나가는 API 호출 로그 (대상, URL, 소요 시간, 상태) |
| ApiHistory | API 호출 로그 (요청/응답, ApiType으로 분류) |
| AiPrompt | AI 프롬프트 설정 (번역, 수출 검사 등). 타입과 역할(system/user)로 구분 |
| Snapshot | 특정 시점의 주문/상품 상태 불변 스냅샷 (감사/재처리용) |
| DeliveredService | Delivered 플랫폼 서비스 타입 (GLOBAL_SHIP, WEBUY 등). 결제/프로바이더 설정 분리 단위 |
