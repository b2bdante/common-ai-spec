# Backend Coding Convention

# 패키지

### Naming Convention
- all lowercase
- 패키지 명이 두 단어 이상일때도 모두 소문자로 작성
  - 예) orders(O), shippinglabel(O), shippingLabel(X)
- package 의 하위 클래스가 두 개 이상일때, 폴더 생성(선택)


# Entity, DTO, VO

### Entity
- `@Entity` Annotation만 사용, `@Table` Annotation 사용 안함
- 예약어의 경우 복수형으로 사용 (Orders, Users)
- **Unique Index** 같은 경우 테스트에서 사용해야 하기 때문에 코드에 명시합니다. (2024-04-03 추가)
- **Enum Type** 사용 시, **성별**과 같이 **불변**하는 **Enum**을 제외하고는 **String**으로 명시합니다. (2024-04-03 추가)

```kotlin
@Entity
class Orders {
  val createdAt: LocalDateTime // table 저장은 datetime
} // (O)

@Entity
class Order {} // (X) query를 만들때, 백스틱(`)을 넣어야 함

@Entity
@Table("Orders")
class Order {} // (X)
```

### DTO
- 내부 레이어 데이터 전달
- Service -> UseCase로 전달시 DTO 리턴(Service의 리턴 값)

```kotlin
@Service
class OrderService(
	val orderRepository: OrderRepository
) {
	fun getOrder(
		orderId: Long
	): OrderDTO = orderRepository
			.findByIdOrNull(orderId)
			?.let(OrderMapper::toDTO)
			?: throw OrderException("주문을 찾을 수 업습니다. orderId($orderId)")
}
```

### VO
- 외부 데이터 전달
- 외부에서 데이터 받을때는 `XXXRequest`
- 외부에 데이터 전달할때는 `XXXResponse`

```kotlin
@Controller
@RequestMapping("orders")
class OrderController(
	val orderUsecase: OrderUsecase
) {
	@PostMapping
	fun createOrder(
		@RequestBody @Valid newOrderRequst: NewOrderRequest
	): OrderResponse = orderUseCase.createOrder(newOrderRequst)
}
```

- Request VO에서 NotNull Validation을 위해 Nullable 한 프로퍼티를 선언하는 대신에 GlobalException Handler를 사용한다.

```kotlin
data class SignInRequest(
  @field:NotBlank
  @field:NotNull // (X)
  val email: String?, // (X)

  @field:NotBlank
  val password: String // (O)
)

@ExceptionHandler(HttpMessageNotReadableException::class)
fun handleHttpMessageNotReadableException(e: HttpMessageNotReadableException) {
  when (val caused = e.cause) {
    is MissingKotlinParameterException -> {
      log.warn(e) { "${caused.parameter.name} 필드가 누락되었습니다." }
    }
    else -> throw e
  }
}
```

# Coding Convention

### Class
- Naming: Pascal
- 명사로 작성

```kotlin
class OrderService {} // (O)

class GetOrder {} // (X)
class OrderGetter {} // (O)
```

### Method
- Naming: Camel
- 함수의 이름은 동사로 시작

```kotlin
class Order {
	fun getOrder() {} // (O)

	fun newOrder(newOrderRequest: NewOrderRequest) // (X)
	fun createOrder(newOrderRequest: NewOrderRequest) // (O)
}
```

- 함수 인자
  - 최대 5개
  - 5개가 넘어가면 DTO나 VO로 전달

```kotlin
fun createOrder(
	userId: Long,
	productId: Long,
	productName: String,
	price: Int,
	quantity: Int,
	createdAt: LocalDateTime
) {} // (X)

fun createOrder(
	newOrderRequest: NewOrderRequest
) {} // (O)
```

- 함수 인자가 두개 이상 넘어가면 줄 바꿈

```kotlin
fun createOrder(userId: Long, productId: Long) {} // (X)
fun createOrder(
	userId: Long,
	productId: Long
) {} // (O)
```

- Mapper 함수
  - Mapper에서는 예외적으로 함수의 이름이 `to`로 시작한다.

### Variable (변수)
- Naming: Camel
- 명사로 작성

```kotlin
val customer: Customer // (O)

val createCustomer: Customer // (X)
val newCustomer: Customer // (O)
```

### Const (상수)
- Naming: Upper Snake

```kotlin
object class Constants {
	val DEFAULT_PER_PAGE_ROW_COUNT = 10 // (O)
	val DEFAULT_MAX_PER_PAGE_ROW_COUNT = 100 // (O)
}
```

### Json
- Naming: Camel

```json
{
	"productTitle": "새 상품",
	"price": 1000,
	"items": [
		"itemTitle": "빨강"
	],
	"createdBy": {
		"id": "1",
		"name": "관리자 박씨"
	}
}
```

### URL
- Naming
  - URL: kebab
  - queryString: Camel

```
/api/v1/orders/change-order-price
/api/v1/orders?pageNum=1
```

- 복수형 사용, 단일 객체는 복수형 뒤에 id

```
/api/v1/order   // (X)
/api/v1/orders  // (O) 모든 주문 목록
/api/v1/orders/1 // (O) 1번 주문
```

- Http Method로 표현되는 기능은 url 표시 안함
- 단 PATCH일 경우에는 기능을 명시

```
// 주문 생성
/api/v1/orders/create // (X)
/api/v1/orders POST   // (O)

// 주문 조회
/api/v1/orders/getOrder // (X)
/api/v1/orders GET      // (O)

// 주문 업데이트
/api/v1/orders PUT // (O)

// 주문 부분 업데이트
/api/v1/orders/change-order-price PATCH
```

- 전체 목록에서 검색을 수행시는 query parameter로 표현

```
/api/v1/orders?query=new&queryType=name // (O)

/api/v1/orders/1

/api/v1/orders?ids=1,2,3    // (O)
/api/v1/orders/in?ids=1,2,3 // (X)

/api/v1/orders/search // (X) orders 의 검색은 queryparameter 존재 유무로 알 수 있음
```

- admin 주소에는 api 버전 정보 앞에 `admin` 추가

### Usecase
- 두 단어라 UseCase로 적을 수 있으나 항상 붙어 다니는 단어이며 하나의 단어처럼 사용되기에 개발에서는 Usecase로 사용
- Bean 선언시 Usecase Annotation 사용

```kotlin
// Usecase Annotation 선언
@Target(AnnotationTarget.CLASS)
@Retention(AnnotationRetention.RUNTIME)
@MustBeDocumented
@Component
annotation class Usecase

@Usecase
class CustomerUsecase(
  private val customerService: CustomerService
)
```

## Facade
- 여러 UseCase에서 동일한 흐름(flow)을 공유할 때 `@Facade` 어노테이션을 사용한다
- Facade는 여러 Service를 조합하여 공통 비즈니스 플로우를 실행한다
- UseCase -> Facade,Services -> Services 순서로 호출한다 (Facade 사용할때만)

### WebClient
- WebClient 역시 Repository 이므로 VO가 아닌 Entity처럼 동작하도록 구현
- 리턴 타입을 XBorderCustomerSignInResponse가 아닌 XBorderCustomerSignIn를 리턴해야 함

```kotlin
interface XBorderRepository {
  fun getCustomer(): Mono
}

@WebClientRepository
class XBorderWebClient(
  val xBorderWebClient: WebClient
) : XBorderRepository {
  override fun getCustomer(): Mono = xBorderWebClient
    .get()
    .uri("/customers/sign-in")
    .retrieve()
    .bodyToMono(XBorderCustomerSignIn::class.java)
}
```

# Test 작성
- 테스트 코드 작성 예시를 참고하여 테스트 작성
- database 통합 테스트의 경우 testcontainer를 통해 테스트를 수행한다. 그러므로 Entity를 정의할때, table 쿼리가 생성 가능하도록 Entity Class를 작성해야 한다.

```kotlin
@Entity
@Table(
  indexes = [
    Index(name = "idx__email__password", columnList = "email, password")
  ]
)
class Customer(
  @Column(nullable = false)
  val email: String,

  @Column(nullable = false)
  val password: String,

  @Id
  @GeneratedValue(strategy = GenerationType.IDENTITY)
  val id: Long
)
```

# Profile
- 로컬: application-local.yml
- 스테이징(테스트) 서버: application-staging.yml
- 실서버(production): application-prod.yml
- test case: application-test.yml

# DB 사용
- test: testcontainer mariadb
- dev, test: 개발 mariadb
- prod: 실서버 mariadb

# Flyway
- Flyway 폴더 구조는 릴리즈별로 폴더를 분리합니다.
- Hotfix가 있을경우 현재 진행하고있는 릴리즈가 아닌 이전 릴리즈 폴더에 핫픽스 sql을 생성
- 파일네이밍은 `V{년도}.{월}.{일}.{Jira 티켓번호}__example.sql` 형식으로 작성
- 핫픽스일경우 `V{년도}.{월}.{일}.{Jira 티켓번호}__hotfix_example.sql` 형식으로 작성

```
/db
└── /migration
    └── /release
            └── /release-1.0
                    ├── V2025.02.03.847__init_schema.sql
                    └── V2025.02.21.176__add_user_table.sql
            └── /release-1.1
                    ├── V2025.03.11.341__add_order_table.sql
                    └── V2025.03.14.344__modify_user_table.sql
                    ├── V2025.03.31.628__hotfix_user_profile_null.sql
```

# TimeZone
- DB 및 서버의 Time Zone은 UTC로 통일
- 시각을 저장하는 DB column의 타입은 datetime 사용

# 타입 추론
- Controller 레이어를 제외한 모든 function(method)은 return type을 표기합니다.
- 코드 내에서는 타입 추론을 권장합니다.

# 네이티브 쿼리 형식
- 네이티브 쿼리 사용 시 예시

```kotlin
@Query("""
    SELECT cm
      FROM CarrierManager cm
      JOIN FETCH cm.carrier
      JOIN FETCH cm.country
     WHERE cm.carrier.id = :carrierId
""")
fun findAllWithCarrierAndCountryByCarrierId(carrierId: Long): List

@Query("""
    SELECT cm
      FROM CarrierManager cm
      JOIN FETCH cm.carrier
      JOIN FETCH cm.country
     WHERE cm.carrier.id
        IN :carrierIds
""")
fun findAllWithCarrierAndCountryByCarrierIdIn(carrierIds: List): List
```
