# Order API - Spring Boot

A simple Spring Boot REST API for managing orders.  
Supports creating new orders and retrieving all existing orders.

---

## 1. Project Overview

This API demonstrates a basic **Spring Boot** application with:
- REST endpoints using `@RestController`
- Data persistence with Spring Data JPA
- A simple entity `Order`

---

## 2. Project Structure
src/main/java/com/example/demo
│
├── controller
│   └── OrderController.java
│
├── repository
│   └── OrderRepository.java
│
└── model
└── Order.java

## 3. Request Flow

```plaintext
Client (Postman, Frontend App, etc.)
        |
        v
OrderController (REST API Layer)
        |
        v
OrderRepository (Data Access Layer)
        |
        v
Database (H2 / MySQL / PostgreSQL)
        |
        v
Response sent back to Client

4. Class Diagram

classDiagram
    class Order {
        +Long id
        +String itemName
        +int quantity
        +double price
    }

    class OrderController {
        +createOrder(Order order) ResponseEntity
        +getAllOrders() ResponseEntity
    }

    class OrderRepository {
        +save(Order order) : Order
        +findAll() : List~Order~
    }

    OrderController --> OrderRepository
    OrderRepository --> Order

5. Example Endpoints

Create Order
POST /api/orders
Content-Type: application/json

{
  "itemName": "Laptop",
  "quantity": 1,
  "price": 1200.00
}

Get All Orders
GET /api/orders

6. Technologies Used
	•	Java 17+
	•	Spring Boot 3.x
	•	Spring Web
	•	Spring Data JPA
	•	H2 Database (for development)
	•	Maven

7. References
	•	Spring Boot Docs
	•	Spring Data JPA Docs
