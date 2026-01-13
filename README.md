# 🛒 E-Commerce REST API

A RESTful e-commerce backend application built with **Spring Boot 3.5.9** for managing products with image support.

## 🚀 Tech Stack

| Technology | Description |
|------------|-------------|
| **Java 17** | Programming Language |
| **Spring Boot 3.5.9** | Application Framework |
| **Spring Data JPA** | Data Access Layer |
| **H2 Database** | In-memory Database |
| **Lombok** | Boilerplate Code Reduction |
| **Maven** | Build & Dependency Management |

## 📋 Prerequisites

- Java 17 or higher
- Maven 3.6+

## ⚙️ Getting Started

### Clone the repository

```bash
git clone <repository-url>
cd ecom-proj
```

### Build the project

```bash
./mvnw clean install
```

Or on Windows:

```bash
mvnw.cmd clean install
```

### Run the application

```bash
./mvnw spring-boot:run
```

Or on Windows:

```bash
mvnw.cmd spring-boot:run
```

The application will start on `http://localhost:8080`

## 🗄️ Database Configuration

This project uses an **H2 in-memory database** for development:

| Property | Value |
|----------|-------|
| Console URL | http://localhost:8080/h2-console |
| JDBC URL | `jdbc:h2:mem:telusko` |
| Username | `sa` |
| Password | *(empty)* |

## 📁 Project Structure

```
src/main/java/com/telusko/ecom_proj/
├── EcomProjApplication.java    # Main Application Entry Point
├── controller/
│   └── ProductController.java  # REST API Endpoints
├── model/
│   └── Product.java            # Product Entity
├── repo/
│   └── ProductRepo.java        # Data Repository
└── service/
    └── ProductService.java     # Business Logic Layer
```

## 🔗 API Endpoints

### Base URL: `/api`

| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/products` | Get all products |
| `GET` | `/product/{id}` | Get product by ID |
| `POST` | `/product` | Add a new product |
| `PUT` | `/product/{id}` | Update a product |
| `DELETE` | `/product/{id}` | Delete a product |
| `GET` | `/product/{id}/image` | Get product image |
| `GET` | `/products/search?keyword={keyword}` | Search products |

### Product Model

```json
{
  "id": 1,
  "name": "Product Name",
  "description": "Product Description",
  "brand": "Brand Name",
  "price": 99.99,
  "category": "Category",
  "releseDate": "2026-01-13",
  "productAvailable": true,
  "stockQuantity": 100,
  "imageName": "image.jpg",
  "imageType": "image/jpeg"
}
```

### Example Requests

#### Get All Products
```bash
curl -X GET http://localhost:8080/api/products
```

#### Get Product by ID
```bash
curl -X GET http://localhost:8080/api/product/1
```

#### Add New Product (with image)
```bash
curl -X POST http://localhost:8080/api/product \
  -F "product={\"name\":\"iPhone\",\"brand\":\"Apple\",\"price\":999.99,\"category\":\"Electronics\",\"productAvailable\":true,\"stockQuantity\":50};type=application/json" \
  -F "imageFile=@/path/to/image.jpg"
```

#### Update Product
```bash
curl -X PUT http://localhost:8080/api/product/1 \
  -F "product={\"id\":1,\"name\":\"iPhone 15\",\"brand\":\"Apple\",\"price\":1099.99};type=application/json" \
  -F "imageFile=@/path/to/new-image.jpg"
```

#### Delete Product
```bash
curl -X DELETE http://localhost:8080/api/product/1
```

#### Search Products
```bash
curl -X GET "http://localhost:8080/api/products/search?keyword=phone"
```

## 🔧 Configuration

Application properties can be modified in `src/main/resources/application.properties`:

```properties
spring.application.name=ecom-proj
spring.datasource.url=jdbc:h2:mem:telusko
spring.jpa.show-sql=true
spring.jpa.hibernate.ddl-auto=update
spring.h2.console.enabled=true
```

## ✨ Features

- ✅ Full CRUD operations for products
- ✅ Image upload and retrieval support
- ✅ Product search functionality
- ✅ RESTful API design
- ✅ CORS enabled for cross-origin requests
- ✅ H2 Console for database inspection

## 📝 License

This project is open source and available under the [MIT License](LICENSE).

---

Made with ❤️ using Spring Boot

