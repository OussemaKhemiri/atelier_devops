# Microservice Architecture

```mermaid
graph TD
    U[User] --> F[Frontend]
    
    subgraph Docker Host
        F --> A[API Gateway]
        A --> K[Keycloak]
        A --> E[Eureka]
        
        subgraph Microservices
            M1[Product Service]
            M2[Order Service]
            M3[User Service]
            M4[Inventory Service]
            M5[Payment Service]
        end
    end

    M1 --> DB1[(Product DB)]
    M2 --> DB2[(Order DB)]
    M3 --> DB3[(User DB)]
    M4 --> DB4[(Inventory DB)]
    M5 --> DB5[(Payment DB)]

    %% Styling for boxes
    classDef box fill:#f8f9fa,stroke:#333,stroke-width:2px;
    class U,F,A,K,E,M1,M2,M3,M4,M5,DB1,DB2,DB3,DB4,DB5 box;
```
## Component Legend

| Component         | Description                                                                 |
|-------------------|-----------------------------------------------------------------------------|
| User              | End-user interacting with the system                                       |
| Frontend          | Web interface (React/Angular/Vue)                                          |
| API Gateway       | Entry point for all requests (Spring Cloud Gateway)                        |
| Keycloak          | Authentication and authorization server                                    |
| Eureka            | Service discovery server                                                   |
| Product Service   | Manages product catalog and inventory                                      |
| Order Service     | Handles order processing and tracking                                      |
| User Service      | Manages user profiles and authentication                                   |
| Inventory Service | Tracks stock levels and availability                                       |
| Payment Service   | Processes financial transactions                                           |
| *DB               | Dedicated database for each service (shown with entity name)               |
