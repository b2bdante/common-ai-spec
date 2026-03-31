# x-border-service 용어

| 용어 | 설명 |
|------|------|
| CarrierServiceShippableCountry | 배송사 서비스별 배송 가능 국가 (중량 제한 포함) |
| CustomerCarrierManager | 고객별 사용 가능 배송사 매핑 |
| DeletedOrder | 소프트 삭제/보관된 주문 (원본 데이터 보존) |
| DeletedOrderItem | 삭제된 주문의 항목 |
| FileStorage | 첨부 파일 저장 기록 (첨부 타입, 사용자 연결) |
| GlobalSellingCustomer | e-connect 글로벌셀링 플랫폼 고객 연동 (OAuth 토큰) |
| Invoice | 고객 청구서 (청구서 번호, 금액, 정산 상태) |
| Notice | 시스템 공지사항 (제목, 내용, 작성자) |
| NoticeFile | 공지사항 첨부 파일 |
| ResetPasswordManager | 비밀번호 재설정 토큰 관리 (토큰, 고객 ID, 만료) |
| Shipback | 반송 요청 (배송 ID, 고객, 창고, 사유, 픽업 상세) |
| ShipmentRemark | 관리자의 배송 메모/비고 |
| TrackingQueue | 추적 업데이트 처리 큐 (페이로드, 메시지 ID, DLQ 여부) |