# common-external-order-service 용어

| 용어 | 설명 |
|------|------|
| ExternalOrderSnapshot | 외부 주문 생성 요청 데이터의 불변 스냅샷 (JSON). 감사/재처리용 |
| InboundApiLog | 외부 주문 서비스로 들어오는 API 요청 로그 (endpoint, method, 요청/응답, 실행 시간) |
| OrderRequestResult | 자동 주문 제출 결과 추적 (성공/실패 사유) |
| OutboundApiLog | 외부 주문 서비스에서 나가는 API 호출 로그 (대상, URL, 소요 시간, 상태) |
| SourcingOrderItem | 소싱 주문 항목 (항목 코드, 일본어 이름, 수량, 이미지, 가격, 카테고리, 브랜드) |
| SourcingOrders | 소싱/풀필먼트 주문 (구매자 정보, 풀필먼트 타입, WMS 주문번호, 상태) |
| SourcingShipment | 소싱 주문 배송 정보 (국가, 주소, 수취인명/가타카나, 전화번호) |
| TracxDeliveryWebhookHistory | TracX 배송 웹훅 페이로드 기록 (성공/에러 상태) |
| WebuyErrorHistory | Webuy 연동 에러 기록 (요청 내용, 에러 메시지, 완료 추적) |