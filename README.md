# 🛒 E-Commerce Web API

A production-style RESTful API for an e-commerce platform built with **ASP.NET Core** and **Onion Architecture**, featuring Redis caching, Stripe payment integration, and JWT authentication.

---

## ✨ Features

- 🏗️ **Onion Architecture** — strict separation of concerns across Core, Application, Infrastructure, and API layers
- 🔐 **JWT Authentication** — secure token-based auth with ASP.NET Core Identity
- 💳 **Stripe Integration** — full payment processing workflow
- ⚡ **Redis Caching** — reduces redundant DB queries on high-traffic endpoints
- 📦 **Generic Repository + Unit of Work + Specification Pattern** — flexible and scalable data access layer
- 🗺️ **AutoMapper** — clean DTO mapping across layers
- 📄 **Swagger/OpenAPI** — fully documented and testable API endpoints

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Language | C# / .NET |
| Framework | ASP.NET Core Web API |
| ORM | Entity Framework Core |
| Database | SQL Server |
| Caching | Redis |
| Auth | JWT · ASP.NET Core Identity |
| Payments | Stripe API |
| Mapping | AutoMapper |
| Architecture | Onion Architecture |
| Patterns | Generic Repository · Unit of Work · Specification |

---

## 🏛️ Architecture Overview

```
├── Core
│   ├── Entities
│   └── Interfaces (IGenericRepository, IUnitOfWork, ISpecification)
├── Application
│   ├── Services
│   ├── DTOs
│   └── Mapping Profiles
├── Infrastructure
│   ├── Data (EF Core DbContext, Migrations)
│   ├── Repositories (Generic + Specification implementations)
│   ├── Redis Cache Service
│   └── Stripe Payment Service
└── API
    ├── Controllers
    ├── Middleware (Error Handling)
    └── Extensions (DI, Swagger)
```

---

## 🚀 Getting Started

### Prerequisites
- .NET 8 SDK
- SQL Server
- Redis (local or Docker)
- Stripe account (for payment testing)

### Setup

```bash
# 1. Clone the repository
git clone https://github.com/karimsalahabdelghany/E-Commerce-Web-API.git
cd E-Commerce-Web-API

# 2. Update appsettings.json with your config
# - SQL Server connection string
# - Redis connection string
# - JWT Secret
# - Stripe Secret Key

# 3. Apply EF Core migrations
dotnet ef database update

# 4. Run the application
dotnet run
```

### 📡 API Endpoints (Key Examples)

| Method | Endpoint | Description |
|---|---|---|
| POST | `/api/account/login` | User login, returns JWT |
| POST | `/api/account/register` | New user registration |
| GET | `/api/products` | Get all products (cached) |
| GET | `/api/products/{id}` | Get product by ID |
| POST | `/api/basket` | Add items to basket |
| POST | `/api/orders` | Place a new order |
| POST | `/api/payments` | Create Stripe payment intent |

---

## 📸 Swagger UI

After running the project, navigate to:
```
https://localhost:{port}/swagger
```

---

## 🌟 Key Design Decisions

- **Specification Pattern** — avoids query bloat in repositories, each query is encapsulated in its own spec class
- **Redis for basket** — shopping basket is stored in Redis (not SQL) for fast ephemeral access
- **Stripe webhook-ready** — payment service is structured to support Stripe webhooks for order confirmation

---

## 👤 Author

**Karim Salah** — Junior .NET Backend Developer
- 📧 karimabdelghany753@gmail.com
- 💼 [LinkedIn](https://linkedin.com/in/karim-salah22)
- 🐙 [GitHub](https://github.com/karimsalahabdelghany)
