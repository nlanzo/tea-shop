# Eerie Tea - Technical Architecture

## Overview

The Eerie Tea e-commerce platform follows a **separation of concerns** architecture with a clear split between frontend and backend:

- **Frontend**: Next.js 16.1.1 (React) - Client-side application
- **Backend**: .NET 10.0 + ASP.NET Core - RESTful Web API
- **Database**: SQL Server (Local for dev, Azure SQL Database for production)

## Architecture Diagram

```
┌─────────────────────────────────────────────────────────────────┐
│                         CLIENT LAYER                            │
│                                                                   │
│  ┌──────────────────────────────────────────────────────────┐  │
│  │              Next.js Frontend (Port 3000)                  │  │
│  │  ┌──────────┐  ┌──────────┐  ┌──────────┐              │  │
│  │  │  Pages   │  │Components│  │  Stores  │              │  │
│  │  │  (App    │  │  (React) │  │ (Zustand)│              │  │
│  │  │  Router) │  │          │  │          │              │  │
│  │  └──────────┘  └──────────┘  └──────────┘              │  │
│  │       │              │              │                    │  │
│  │       └──────────────┼──────────────┘                    │  │
│  │                      │                                    │  │
│  │              ┌──────▼──────┐                            │  │
│  │              │ API Client  │                            │  │
│  │              │  (lib/api)  │                            │  │
│  │              └──────┬──────┘                            │  │
│  └──────────────────────┼──────────────────────────────────┘  │
│                         │ HTTP/REST                            │
│                         │ (CORS enabled)                       │
└─────────────────────────┼───────────────────────────────────────┘
                          │
                          ▼
┌─────────────────────────────────────────────────────────────────┐
│                      API LAYER (Port 5000/5001)                 │
│                                                                   │
│  ┌──────────────────────────────────────────────────────────┐  │
│  │         ASP.NET Core Web API (EerieTea.Api)               │  │
│  │  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐   │  │
│  │  │ Controllers  │  │  Middleware  │  │   Filters    │   │  │
│  │  │              │  │              │  │              │   │  │
│  │  │ - Products   │  │ - Auth       │  │ - Validation│   │  │
│  │  │ - Orders     │  │ - CORS       │  │ - Error     │   │  │
│  │  │ - Cart       │  │ - Logging    │  │   Handling  │   │  │
│  │  │ - Auth       │  │              │  │              │   │  │
│  │  │ - Admin      │  │              │  │              │   │  │
│  │  └──────┬───────┘  └──────┬───────┘  └──────┬───────┘   │  │
│  │         │                  │                  │           │  │
│  │         └──────────────────┼──────────────────┘           │  │
│  │                            │                              │  │
│  │                    ┌───────▼───────┐                      │  │
│  │                    │  Dependency   │                      │  │
│  │                    │   Injection   │                      │  │
│  │                    └───────┬───────┘                      │  │
│  └────────────────────────────┼──────────────────────────────┘  │
│                               │                                   │
└───────────────────────────────┼───────────────────────────────────┘
                                │
                                ▼
┌─────────────────────────────────────────────────────────────────┐
│                    BUSINESS LOGIC LAYER                          │
│                                                                   │
│  ┌──────────────────────────────────────────────────────────┐  │
│  │              EerieTea.Core (Domain Layer)                │  │
│  │  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐   │  │
│  │  │  Entities    │  │    DTOs      │  │  Interfaces  │   │  │
│  │  │              │  │              │  │              │   │  │
│  │  │ - Product    │  │ - ProductDto │  │ - IProduct   │   │  │
│  │  │ - Order      │  │ - OrderDto   │  │   Service    │   │  │
│  │  │ - User       │  │ - CreateDto  │  │ - IOrder     │   │  │
│  │  │ - Cart       │  │              │  │   Service    │   │  │
│  │  └──────────────┘  └──────────────┘  └──────┬───────┘   │  │
│  └─────────────────────────────────────────────┼───────────┘  │
│                                                  │               │
└──────────────────────────────────────────────────┼───────────────┘
                                                   │
                                                   ▼
┌─────────────────────────────────────────────────────────────────┐
│                  INFRASTRUCTURE LAYER                           │
│                                                                   │
│  ┌──────────────────────────────────────────────────────────┐  │
│  │         EerieTea.Infrastructure                           │  │
│  │  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐   │  │
│  │  │   Services   │  │ Repositories │  │   External   │   │  │
│  │  │              │  │              │  │   Services   │   │  │
│  │  │ - Product    │  │ - Product    │  │ - Stripe     │   │  │
│  │  │   Service    │  │   Repository │  │ - Resend     │   │  │
│  │  │ - Order      │  │ - Order      │  │   (Email)    │   │  │
│  │  │   Service    │  │   Repository │  │              │   │  │
│  │  │ - Cart       │  │              │  │              │   │  │
│  │  │   Service    │  │              │  │              │   │  │
│  │  └──────┬───────┘  └──────┬───────┘  └──────────────┘   │  │
│  │         │                  │                              │  │
│  │         └──────────────────┼──────────────────┘          │  │
│  │                            │                               │  │
│  │                    ┌───────▼───────┐                      │  │
│  │                    │ EF Core       │                      │  │
│  │                    │ DbContext     │                      │  │
│  │                    └───────┬───────┘                      │  │
│  └────────────────────────────┼──────────────────────────────┘  │
│                               │                                   │
└───────────────────────────────┼───────────────────────────────────┘
                                │
                                ▼
┌─────────────────────────────────────────────────────────────────┐
│                        DATA LAYER                                │
│                                                                   │
│  ┌──────────────────────────────────────────────────────────┐  │
│  │                    SQL Server                            │  │
│  │                                                           │  │
│  │  ┌──────────┐  ┌──────────┐  ┌──────────┐             │  │
│  │  │ Products │  │  Orders  │  │  Users    │             │  │
│  │  │          │  │          │  │          │             │  │
│  │  │ - id     │  │ - id     │  │ - id     │             │  │
│  │  │ - name   │  │ - userId │  │ - email  │             │  │
│  │  │ - price │  │ - total  │  │ - role   │             │  │
│  │  │ - stock │  │ - status │  │          │             │  │
│  │  └──────────┘  └──────────┘  └──────────┘             │  │
│  │                                                           │  │
│  │  Development: Local SQL Server (Express/LocalDB)        │  │
│  │  Production: Azure SQL Database                          │  │
│  └───────────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────────┘
```

## Data Flow

### 1. User Request Flow
```
User → Next.js Frontend → API Client → .NET API → Controller → Service → Repository → EF Core → SQL Server
                                                                                              ↓
User ← Next.js Frontend ← API Client ← .NET API ← Controller ← Service ← Repository ← EF Core ← SQL Server
```

### 2. Authentication Flow
```
User → Login Form → API Client → AuthController → ASP.NET Core Identity → SQL Server (Users)
                                                                                    ↓
User ← JWT Token ← API Client ← AuthController ← ASP.NET Core Identity ← SQL Server
```

### 3. Order Processing Flow
```
User → Checkout → API Client → OrdersController → OrderService → PaymentService (Stripe)
                                                                              ↓
User ← Order Confirmation ← API Client ← OrdersController ← OrderService ← EmailService (Resend)
                                                                                    ↓
                                                                              SQL Server (Orders)
```

## Technology Stack

### Frontend
- **Framework**: Next.js 16.1.1 (App Router)
- **Language**: TypeScript 5.9+
- **State Management**: Zustand
- **Styling**: Tailwind CSS + shadcn/ui
- **API Communication**: Axios/Fetch API

### Backend
- **Framework**: .NET 10.0 + ASP.NET Core
- **Language**: C# 12.0
- **ORM**: Entity Framework Core 10.0
- **Authentication**: ASP.NET Core Identity + JWT
- **API Documentation**: Swagger/OpenAPI

### Database
- **Development**: SQL Server Express/LocalDB
- **Production**: Azure SQL Database
- **Migrations**: EF Core Migrations

### External Services
- **Payments**: Stripe (via Stripe.net SDK)
- **Email**: Resend (via .NET SDK)
- **Hosting**: 
  - Frontend: Vercel
  - Backend: Azure App Service

## Security

- **CORS**: Configured in .NET API to allow frontend origin
- **Authentication**: JWT Bearer tokens
- **Authorization**: Role-based (Admin, User)
- **Data Validation**: 
  - Frontend: Zod schemas
  - Backend: Data Annotations + FluentValidation
- **HTTPS**: Enforced in production

## Deployment Architecture

```
┌─────────────┐         ┌─────────────┐         ┌─────────────┐
│   Vercel    │────────▶│   Azure     │────────▶│   Azure     │
│  (Frontend) │  HTTPS  │ App Service │  HTTPS  │ SQL Database│
│             │         │  (Backend)   │         │             │
└─────────────┘         └─────────────┘         └─────────────┘
     │                        │                        │
     │                        │                        │
     └────────────────────────┼────────────────────────┘
                              │
                         ┌────▼────┐
                         │  Stripe │
                         │  Resend │
                         └─────────┘
```

## Key Design Decisions

1. **Separation of Frontend/Backend**: Allows independent scaling and deployment
2. **RESTful API**: Standard HTTP methods for clear API contracts
3. **Layered Architecture**: Separation of concerns (API → Core → Infrastructure)
4. **Dependency Injection**: Loose coupling, easy testing
5. **Repository Pattern**: Abstraction over data access
6. **DTO Pattern**: Separate domain entities from API contracts
7. **JWT Authentication**: Stateless, scalable authentication

## Future Considerations

- **Caching**: Redis for session/cart caching
- **Message Queue**: Azure Service Bus for async processing
- **CDN**: Azure CDN for static assets
- **Monitoring**: Application Insights
- **API Gateway**: Azure API Management (if needed)
