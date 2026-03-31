# crossborder-service 용어

| 용어 | 설명 |
|------|------|
| ApiAtomyBackChangeOrders | Atomy 반품/교환 주문 기록 (입고/출고 주소, 자재 코드, 요청 상태) |
| ApiAtomyOrders | Atomy API에서 수집한 원본 주문 데이터 (판매 상세, 가격 KRW/USD, 고객 정보, 배송 주소) |
| ApiHistory | API 호출 로그 (요청/응답). ApiType(EXPECTED_ORDER 등)으로 분류 |
| AtomyAzaOrders | Atomy AZA 마켓플레이스 주문 데이터 (상품 상세, 가격, 수취인, 택배/송장 추적) |
| AzaProduct | Atomy AZA 마켓플레이스 상품 마스터 (치수, 중량, HS 코드, FDA 번호, 다국어 이름) |
| OrderApiFlag | 주문별 API 전송 상태 플래그 (확인, 송장, 출고일, 배송 완료) |
| OrderDetail | 크로스보더 주문 상세 항목 (자재 코드/이름 KR/EN, 수량, 가격 KRW/USD, HS 코드, 중량) |
| ProductKitItem | ProductKit 내 개별 상품 (킷 SKU와 Product 연결, 수량) |
| Rate | 국가별 중량 기준 배송 요금표 (국가 코드별 컬럼: US, JP, AU 등) |
| RuRate | 러시아 전용 배송 요금표 (중량, 가격) |
| TotalRate | 종합 배송 요금표. Rate와 동일 구조 |