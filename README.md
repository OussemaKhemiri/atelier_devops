# Library Management System

The **Library Management System** is a simple yet powerful application that allows users to manage a collection of books. It provides functionalities to add, update, delete, and view books and some advanced functionalities making it ideal for libraries, personal collections, or educational institutions.

# Architecture 
1.Containerized Library Management System with Spring Cloud Ecosystem

![Alt Text Description](diagramprojet.png)

2.Library Domain Model Class Diagram

![Alt Text Description](diagclasse.PNG)

3.Technology
## System Architecture Overview

| Architecture Layer       | Components                                                                 | Description                                                                 |
|--------------------------|----------------------------------------------------------------------------|-----------------------------------------------------------------------------|
| **Containerization**     | Docker                                                                     | Container orchestration for service deployment                              |
| **API Gateway**          | Netflix Zuul                                                               | Routing and API request filtering                                           |
| **Service Discovery**    | Eureka Server                                                              | Service registry for microservice coordination                              |
| **Authentication**       | Keycloak                                                                   | Identity and Access Management (IAM) solution                               |
| **Frontend**             | Angular                                                                    | Web interface                                                               |
| **Microservices**        | Loan, Book, Publisher, Genre, Author, Card                                 | Domain-specific services                                                    |
| **Databases**            | H2, MySQL, MongoDB                                                         | Polyglot persistence strategy                                               |
| **OpenFeign**            | Spring OpenFeign                                                           | Declarative REST client for service-to-service communication                |
| **Configuration Server** | Spring Config Server                                                       | Centralized configuration management                                        |
 

## Navigation
- [Loan](#Loan)
- [Book](#Book)
- [Publisher](#Publisher)
- [Genre](#Genre)
- [Author](#Author)
- [Card](#Card)

<a name="Loan"></a>
## Loan
Loan management microservice with smart validation and automatic adjustment of return dates based on holidays.
### Technologies
- Java 17
- Spring Boot 3.x
- Spring Data JPA
- H2 Database 
### Functionalities
- Complete CRUD for loans
- Loan validation (limit of active loans per user)
- Multi-criteria loan filtering
- Automatic adjustment of return dates based on holidays
- Integration with the public holiday API
### API Reference
#### Get all loans

```http
  GET /loan
```
| Parameter   | Type      | Description                                                         |
| :---------- | :-------- | :------------------------------------------------------------------ |
| `loanId`    | `Integer` | **Required**. Identifiant unique du prêt.                           |
| `bookId`    | `Integer` | **Required**. Identifiant du livre concerné par le prêt.             |
| `cardNumber`| `String`  | **Required**. Numéro de carte de l'emprunteur.                       |
| `loanDate`  | `Date`    | **Required**. Date à laquelle le prêt a été initié.                  |
| `returnDate`| `Date`    | **Required**. Date prévue pour le retour du livre.                   |


#### Get loan by id

```http
GET /loan/{loanId}
```

| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `id`      | `integer` | **Required**. Id of loan to fetch |

#### Update loan by id

```http
  PUT /loan/{loanId}
```

| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `id`      | `integer` | **Required**. Id of loan to fetch |


#### Delete loan by id

```http
 DELETE /loan/{loanId}
```

| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `id`      | `integer` | **Required**. Id of loan to fetch |


#### Add a new loan

```http
  POST /loan
```

#### Get loans by filters

```http
  GET  /loan/filter (http://localhost:8086/loan/filter?bookId=4)
```


#### Get loan statistics

```http
 GET /loan/statistics
```


#### Get Adjust return date for holiday

```http
  GET /loan/{loanId}/adjust-return-date(http://localhost:8090/loan/11/adjust-return-date?countryCode=TN)
```
<a name="Book"></a>
## Book
### Technologies
- Java 17
- Spring Boot 3.x
- Spring Data JPA
- H2 Database 
### Functionalities
- Complete CRUD for books
- check book status
### API Reference
#### Get all books

```http
  GET /books
```

| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `title`      | `string` | **Not Required**. title of book to fetch |
| `author`      | `integer` | **Not Required**. authorId of book to fetch |
| `publisher`      | `integer` | **Not Required**. publisherId of book to fetch |
| `genre`      | `integer` | **Not Required**. genreId of book to fetch |

#### Get book by id

```http
  GET /books/${id}
```

| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `id`      | `string` | **Required**. Id of BOOK to fetch |

#### Update book by id

```http
  PUT /books/${id}
```

| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `id`      | `string` | **Required**. Id of BOOK to fetch |


#### Delete book by id

```http
  DELETE /books/${id}
```

| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `id`      | `string` | **Required**. Id of BOOK to fetch |


#### Add a new book

```http
  POST /books
```

#### Get books By authors

```http
  GET /books/getBooksByAuthors
```


#### Get books cout by  publisher

```http
  GET /books/getBooksCountByPublisher
```


#### Get books distribution by  status

```http
  GET /books/getBooksCountByStatus
```

<a name="Publisher"></a>
## Publisher
...

<a name="Genre"></a>
## Genre
...

<a name="Author"></a>
## Author
...

<a name="Card"></a>
## Card
...




















