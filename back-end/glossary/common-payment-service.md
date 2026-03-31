# common-payment-service 용어

| 용어 | 설명 |
|------|------|
| DeliveredService | Delivered 플랫폼 서비스 타입 (GLOBAL_SHIP, WEBUY 등). 결제/프로바이더 설정 분리 단위 |
| Provider | 결제 프로바이더 설정 (게이트웨이 타입 예: TOSS, 결제 방법 타입). ServiceProvider/SellerProvider의 베이스 클래스 |
| SellerProvider | 셀러별 결제 프로바이더 설정 (Provider 확장) |
| ServiceProvider | DeliveredService별 결제 프로바이더 설정 (Provider 확장) |
| TossPayment | Toss Payments 전용 결제 서브클래스 (paymentKey 추가) |
| TossPaymentsHistory | Toss Payments API 응답 전체 스냅샷 (결제키, 금액, 상태, 카드/이체/가상계좌 상세) |