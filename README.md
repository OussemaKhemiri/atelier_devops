# Project Documentation

## Entity Overview

The system contains the following core entities:

### 1. User
- **id**: `Integer` (Unique identifier)
- **username**: `String` (Unique login name)
- **email**: `String` 
- **createdAt**: `DateTime`
- **isActive**: `Boolean`
- **roles**: `List<String>`

### 2. Product
- **productId**: `UUID`
- **name**: `String`
- **description**: `String`
- **price**: `Double`
- **stockQuantity**: `Integer`
- **category**: `String`

### 3. Order
- **orderId**: `String`
- **userId**: `Integer` (Foreign key to User)
- **products**: `List<Product>`
- **totalAmount**: `BigDecimal`
- **orderDate**: `LocalDateTime`
- **status**: `Enum` (PENDING, SHIPPED, DELIVERED)

### 4. Address
- **addressId**: `Long`
- **street**: `String`
- **city**: `String`
- **state**: `String`
- **zipCode**: `String`
- **isPrimary**: `Boolean`

### 5. Payment
- **paymentId**: `UUID`
- **orderId**: `String`
- **amount**: `BigDecimal`
- **paymentMethod**: `String`
- **transactionDate**: `Instant`
- **isSuccessful**: `Boolean`

### 6. Review
- **reviewId**: `Long`
- **productId**: `UUID`
- **userId**: `Integer`
- **rating**: `Integer` (1-5)
- **comment**: `String`
- **createdAt**: `ZonedDateTime`
