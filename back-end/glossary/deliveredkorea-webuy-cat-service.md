# deliveredkorea-webuy-cat-service 용어

| 용어 | 설명 |
|------|------|
| Asn | ASN(Advanced Shipping Notice). 창고로 입고되는 패키지 사전 알림 |
| AsnItem | ASN 내 개별 항목 |
| AutoShippingSetting | 고객별 자동 배송 설정 |
| BlackList | 사기 방지용 고객/주소 블랙리스트 |
| BundleOrder | 합배송을 위해 여러 구매 대행 요청을 묶은 번들 주문 |
| BunjangOrder | 번개장터 마켓플레이스 주문 (자동 결제 상태 포함) |
| BunjangProduct | 번개장터 상품 목록 |
| BunjangQueue | 번개장터 주문 처리용 SQS 큐 항목 |
| BunjangSnapshot | 주문 시점 번개장터 상품 스냅샷 |
| BunjangSnapshotImage | 번개장터 상품 스냅샷 이미지 |
| BuyRequest | 고객의 구매 대행 요청 (프록시 구매) |
| BuyRequestAdditional | 구매 대행 추가 정보/비용 |
| BuyRequestClearance | 구매 대행 통관 상세 |
| BuyRequestEvent | 구매 대행 상태 변경 이벤트 |
| BuyRequestFee | 구매 대행 수수료 내역 (핸들링, 서비스 수수료) |
| BuyRequestFeeSnapshot | 구매 시점 수수료 스냅샷 |
| BuyRequestImage | 구매 대행 상품 이미지 |
| BuyRequestOption | 구매 대행 선택 옵션 |
| BuyRequestQuotation | 구매 대행 견적서 |
| BuyRequestRefund | 취소된 구매 대행의 환불 상세 |
| BuyRequestSnapshot | 특정 시점 구매 대행 상태 스냅샷 |
| BuyRequestStatusHistory | 구매 대행 상태 변경 감사 추적 |
| Codemaster | 시스템 전역 참조 코드 테이블 |
| CouponHistory | 쿠폰 사용 이력 |
| CustomerAccessLog | 고객 로그인/접속 이벤트 로그 |
| CustomerCategory | 고객 분류/세그먼트 |
| DaisoTracking | 다이소 배송 추적 정보 |
| DomesticCarrier | 국내(한국 내부) 배송사 |
| DomesticShipments | 국내 배송 기록 |
| DomesticShippingPolicy | 국내 배송비 정책 |
| Event | 프로모션/할인 이벤트 설정 |
| FileStore | 업로드 파일 저장소 |
| GlobalCheckoutShipment | 글로벌 체크아웃 주문에서 생성된 배송 |
| GlobalCheckoutSnapshot | 글로벌 체크아웃 주문 상태 스냅샷 |
| GlobalSellingSellerOrderStatusHistory | 글로벌셀링 셀러 주문 상태 변경 이력 |
| GlobalSellingSnapshot | 글로벌셀링 주문 스냅샷 |
| Grade | 고객 멤버십/등급 레벨 |
| HandlingFeePolicy | 핸들링 수수료 계산 정책 (타입, 임계값 기준) |
| Images | 범용 이미지 저장 엔티티 |
| InclusionImage | 합포장 항목 사진 |
| KoreaPayletterInfo | 페이레터(한국 PG) 설정 데이터 |
| LabelCreatedHistory | 생성된 배송 라벨 기록 |
| LegacyItem | 레거시/마이그레이션된 항목 데이터 |
| LocationMaster | 창고 위치 마스터 데이터 |
| LuxuryBrand | 통관/컴플라이언스용 명품 브랜드 참조 |
| Market | 마켓플레이스 참조 (쿠팡, 아마존 등) |
| MarketFeePolicy | 마켓플레이스별 수수료 정책 |
| MarketUrl | 마켓플레이스 상품 페이지 URL 패턴 |
| MarketingCollection | 마케팅 캠페인 컬렉션 |
| MarketingEvent | 마케팅 프로모션 이벤트 |
| MarketingEventHistory | 마케팅 이벤트 활성화 이력 |
| MarketingEventManagement | 마케팅 이벤트 관리 |
| MarkUpSetting | 배송비 마크업 설정 |
| OptionRequestHistory | 패키지 옵션/서비스 요청 이력 |
| PackageConsoleRepack | 패키지 리패킹 요청 |
| PackageOptionPricePolicy | 패키지 옵션(리패킹, 사진 등) 가격 정책 |
| PackageReceiveType | 패키지 수령 방법 타입 |
| PackagingType | 포장 재질/방법 타입 |
| PaymentItemInfo | 항목별 결제 상세 |
| PaymentMethodFeePolicy | 결제 방법별 수수료 정책 |
| PayletterInfo | 페이레터 PG 설정 |
| PayletterRequestHistory | 페이레터 결제 요청 이력 |
| PocaMarketWebhookHistory | PocaMarket 연동 웹훅 이벤트 이력 |
| PointHistory | 포인트 적립/사용 거래 이력 |
| ProductProxySnapshot | 구매 대행(프록시) 주문 스냅샷 |
| RPAPayment | RPA(로봇 프로세스 자동화) 자동 결제 기록 |
| RPAPaymentHistory | RPA 결제 시도 이력 |
| Realpacking | 실시간 패킹 영상/검증 서비스 |
| Referrer | 고객 추천인 소스 추적 |
| ReferrerMailLog | 추천인 알림 이메일 로그 |
| RejectReason | 사전 정의된 거부 사유 코드 |
| RequestPhoto | 패키지 검수 사진 요청 |
| RequestPhotoMapping | 사진 요청-패키지 매핑 |
| SequenceOrderNumber | 자동 증가 주문번호 시퀀스 생성기 |
| ServiceHistory | 수행된 서비스(창고 작업 등) 이력 |
| ShippingAddress | 저장된 고객 배송 주소 |
| SocialLoginInformation | 고객 소셜 로그인 프로바이더 상세 |
| SplitItemInformation | 여러 패키지에 분할된 항목 정보 |
| TensoMarket | Tenso(일본 포워딩) 마켓플레이스 설정 |
| TensoQueue | Tenso 주문 처리 큐 |
| TensoShipment | Tenso 포워딩 서비스 배송 |
| TensoShopCode | Tenso 쇼핑몰 코드 매핑 |
| TensoSnapshot | Tenso 주문 처리 시점 스냅샷 |
| TensoSnapshotImage | Tenso 스냅샷 이미지 |
| TransactionItem | 거래 내 개별 항목 |
| TransactionSequence | 거래번호 시퀀스 생성기 |
| TrifFxrt | 외환 환율 데이터 |
| UnlocodeCountry | UN/LOCODE 국가 참조 (무역용 UN 위치 코드) |
| WmsTaskSnsHistory | WMS(창고관리시스템) 작업 SNS 알림 이력 |