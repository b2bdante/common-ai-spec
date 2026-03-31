# global-checkout-service 용어

| 용어 | 설명 |
|------|------|
| CartSelectedOption | 장바구니 항목 내 선택 옵션 |
| CartSelectedOptionValue | 선택 옵션의 구체적 값 (텍스트 또는 이미지 URL) |
| CartShippingCarrier | 장바구니에 대해 계산된 배송사 운임 (일반/특급, KRW/USD) |
| CouponBudgetHistory | 쿠폰 예산 충전 기록 |
| CouponCode | 개별 쿠폰 코드 (사용 가능 수량) |
| CouponCodeHistory | 쿠폰 코드-주문 사용 이력 |
| CouponCodeHistoryItem | 주문 항목별 쿠폰 할인 상세 |
| DeliveredStoreData | 주문에 연결된 Delivered 스토어 메타데이터 (주소, 사용자) |
| ExternalOrderErrorHistory | 외부 시스템에서 받은 주문 에러 로그 |
| File | 업로드 파일 메타데이터 (원본명, S3 키, 크기, 콘텐츠 타입, URL) |
| GlobalDiscountRate | 시스템 전역 할인율 설정 (결제 방법 또는 할인 타입별) |
| MaxShippingPrice | 셀러/카테고리별 최대 배송비 상한 |
| OrderItemDiscount | 주문 항목에 적용된 할인 (할인율, 타입, 금액) |
| OrderItemOption | 주문 항목의 선택 상품 옵션 |
| OrderItemOptionGroup | 주문 항목 옵션 그룹 (text/select/image 타입) |
| PaymentRefund | 결제 환불 (주문, 항목, 사유, 금액, 수수료) |
| ProductOptionGroup | 관련 상품 옵션 그룹 (타입: text/select/image, 필수 여부) |
| ProductStandardWeight | 상품 표준 중량 참조 |
| QueuePublishErrorHistory | SQS 메시지 발행 실패 에러 로그 |
| SellerFeePolicy | 셀러별 수수료 정책 설정 (수수료 타입, 값, 임계값, 통화) |
| SellerProductSpec | 셀러별 상품 사양 (중량, 치수, 카테고리) |
| StandardWeightDim | 상품 카테고리별 표준 중량 및 치수 |
| TossPaymentsPayment | Toss Payments 결제 응답 객체 (전체 결제 상세) |
| TossPaymentsWebhookHistory | Toss Payments 웹훅 이벤트 로그 |
| WeightAndDim | AI 추정 상품 중량 및 치수 (너비, 높이, 길이, 중량, 카테고리) |