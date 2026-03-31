# simpleglobal-billing-shipping-calculation-service 용어

| 용어 | 설명 |
|------|------|
| CalculateHistory | 배송비 계산 실행 기록 (상태, 단계 로그) |
| CalculatedShipment | 특정 배송의 배송비 계산 결과 (요금, 존, 중량, 마크업) |
| CalculationTriggerHistory | 배치 계산 트리거 이벤트 추적 (페이지네이션, 날짜 범위) |
| CoreCarrierBaseRate | 창고/배송사/중량/존별 기본 배송 요금 |
| CoreCustomerMarkUp | 고객별 배송비 마크업 |
| CoreCustomerZoneMarkUp | 고객별 존 기반 배송비 오버라이드 |
| CoreDimFactor | 배송사 서비스별 체적 중량 계수 |
| CoreShippingZone | 목적지 국가/우편번호와 배송 존 매핑 |
| CountryHsCodeTariff | 특정 국가/HS 코드의 관세율 |
| CountryHsCodeTariffHistory | 국가/HS 코드 관세율 변경 이력 |
| CountryMutualTariff | 국가별 일반/상호 관세율 (HS 코드 비특정) |
| CountryMutualTariffHistory | 상호 관세율 변경 이력 |
| Incoterms | 배송사 서비스별 인코텀즈 설정 (DDP/DAP 지원) |
| OneCompany | ShipStation/OneShip 연동 회사 엔티티 |
| OneOrder | OneShip 시스템 주문 (회사/창고 ID) |
| OneOrderTag | OneShip 주문 태그 |
| OneShipment | OneShip 배송 기록 (송장번호, 출고일, 비용, 치수) |
| OneShipmentServiceCode | OneShip 서비스 코드 참조 |
| OneStore | OneShip 스토어 엔티티 (스토어명, 회사, 마켓플레이스) |
| OneStoreMapping | OneShip 스토어-창고 매핑 |
| OneTag | OneShip 태그/라벨 엔티티 |
| OneWarehouse | OneShip 창고 (코드, 약칭) |
| ProxyPaymentHistory | 관세 대납 결제 이력 (배송사, 관세 금액, 요청/응답 가격) |
| SchedulerHistory | 배치 스케줄러 실행 이력 |