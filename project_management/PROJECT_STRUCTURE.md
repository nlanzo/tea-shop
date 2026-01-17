# Eerie Tea - Project Folder Structure

This document outlines the complete folder structure for the Eerie Tea e-commerce project, separating the Next.js frontend and .NET backend.

## Root Structure

```
eerie-tea/
├── frontend/                    # Next.js 16.1.1 Frontend Application
├── backend/                     # .NET 10.0 Backend API
├── project_management/          # Project documentation and planning
├── .gitignore                  # Git ignore rules for both projects
├── README.md                   # Project overview
└── PROJECT_STRUCTURE.md        # This file
```

---

## Frontend Structure (`frontend/`)

```
frontend/
├── .next/                      # Next.js build output (gitignored)
├── .env.local                  # Local environment variables (gitignored)
├── .env.example                # Example environment variables
├── public/                     # Static assets
│   ├── images/
│   ├── icons/
│   └── favicon.ico
├── app/                        # Next.js App Router
│   ├── (auth)/                 # Auth route group
│   │   ├── login/
│   │   │   └── page.tsx
│   │   ├── register/
│   │   │   └── page.tsx
│   │   └── forgot-password/
│   │       └── page.tsx
│   ├── (shop)/                 # Shop route group
│   │   ├── products/
│   │   │   ├── [slug]/
│   │   │   │   └── page.tsx
│   │   │   └── page.tsx
│   │   ├── cart/
│   │   │   └── page.tsx
│   │   └── checkout/
│   │       └── page.tsx
│   ├── admin/                  # Admin routes (protected)
│   │   ├── products/
│   │   ├── orders/
│   │   ├── customers/
│   │   └── layout.tsx
│   ├── account/                # User account routes (protected)
│   │   ├── profile/
│   │   ├── orders/
│   │   └── addresses/
│   ├── api/                    # API client utilities (not Next.js API routes)
│   │   └── client.ts           # API client configuration
│   ├── layout.tsx              # Root layout
│   ├── page.tsx                # Home page
│   ├── loading.tsx             # Global loading UI
│   ├── error.tsx               # Global error UI
│   └── not-found.tsx           # 404 page
├── components/                 # React components
│   ├── ui/                     # shadcn/ui components
│   │   ├── button.tsx
│   │   ├── card.tsx
│   │   ├── input.tsx
│   │   └── ...
│   ├── layout/                 # Layout components
│   │   ├── Header.tsx
│   │   ├── Footer.tsx
│   │   └── Navigation.tsx
│   ├── products/               # Product-related components
│   │   ├── ProductCard.tsx
│   │   ├── ProductGrid.tsx
│   │   ├── ProductDetail.tsx
│   │   └── ProductFilters.tsx
│   ├── cart/                   # Cart components
│   │   ├── CartItem.tsx
│   │   ├── CartSummary.tsx
│   │   └── CartIcon.tsx
│   ├── checkout/               # Checkout components
│   │   ├── ShippingForm.tsx
│   │   ├── PaymentForm.tsx
│   │   └── OrderSummary.tsx
│   └── auth/                   # Auth components
│       ├── LoginForm.tsx
│       └── RegisterForm.tsx
├── lib/                        # Utility functions and helpers
│   ├── api/                    # API client functions
│   │   ├── products.ts
│   │   ├── auth.ts
│   │   ├── cart.ts
│   │   ├── orders.ts
│   │   └── index.ts
│   ├── utils/                  # General utilities
│   │   ├── cn.ts               # className utility (for shadcn/ui)
│   │   ├── format.ts           # Formatting utilities
│   │   └── validation.ts
│   ├── hooks/                  # Custom React hooks
│   │   ├── useAuth.ts
│   │   ├── useCart.ts
│   │   └── useApi.ts
│   └── stores/                 # Zustand stores
│       ├── cartStore.ts
│       └── authStore.ts
├── types/                      # TypeScript type definitions
│   ├── api.ts                  # API response types
│   ├── product.ts
│   ├── order.ts
│   └── user.ts
├── styles/                     # Global styles
│   └── globals.css             # Tailwind CSS imports
├── tests/                      # Frontend tests
│   ├── components/
│   ├── utils/
│   └── setup.ts
├── .eslintrc.json              # ESLint configuration
├── .prettierrc                 # Prettier configuration (if using)
├── biome.json                  # Biome configuration (if using)
├── next.config.ts              # Next.js configuration
├── tailwind.config.ts          # Tailwind CSS configuration
├── tsconfig.json               # TypeScript configuration
├── package.json                # npm/pnpm dependencies
└── pnpm-lock.yaml              # Lock file (or package-lock.json)
```

---

## Backend Structure (`backend/`)

```
backend/
├── src/
│   ├── EerieTea.Api/           # Web API Project (Main Entry Point)
│   │   ├── Controllers/        # API Controllers
│   │   │   ├── ProductsController.cs
│   │   │   ├── AuthController.cs
│   │   │   ├── CartController.cs
│   │   │   ├── OrdersController.cs
│   │   │   ├── UsersController.cs
│   │   │   └── Admin/
│   │   │       ├── AdminProductsController.cs
│   │   │       ├── AdminOrdersController.cs
│   │   │       └── AdminCustomersController.cs
│   │   ├── Middleware/         # Custom middleware
│   │   │   ├── ErrorHandlingMiddleware.cs
│   │   │   └── RequestLoggingMiddleware.cs
│   │   ├── Filters/            # Action filters
│   │   │   └── ValidateModelAttribute.cs
│   │   ├── Extensions/         # Extension methods
│   │   │   ├── ServiceCollectionExtensions.cs
│   │   │   └── ApplicationBuilderExtensions.cs
│   │   ├── Program.cs          # Application entry point
│   │   ├── appsettings.json   # Configuration
│   │   ├── appsettings.Development.json
│   │   ├── appsettings.Production.json
│   │   └── EerieTea.Api.csproj
│   │
│   ├── EerieTea.Core/          # Domain Models & Business Logic
│   │   ├── Entities/           # Domain entities
│   │   │   ├── Product.cs
│   │   │   ├── Category.cs
│   │   │   ├── Order.cs
│   │   │   ├── OrderItem.cs
│   │   │   ├── Cart.cs
│   │   │   ├── CartItem.cs
│   │   │   ├── User.cs
│   │   │   ├── Address.cs
│   │   │   └── Review.cs
│   │   ├── DTOs/               # Data Transfer Objects
│   │   │   ├── Products/
│   │   │   │   ├── ProductDto.cs
│   │   │   │   └── CreateProductDto.cs
│   │   │   ├── Orders/
│   │   │   │   ├── OrderDto.cs
│   │   │   │   └── CreateOrderDto.cs
│   │   │   └── Auth/
│   │   │       ├── LoginDto.cs
│   │   │       └── RegisterDto.cs
│   │   ├── Interfaces/        # Service interfaces
│   │   │   ├── IProductService.cs
│   │   │   ├── IOrderService.cs
│   │   │   ├── ICartService.cs
│   │   │   └── IEmailService.cs
│   │   ├── Enums/             # Enumerations
│   │   │   ├── OrderStatus.cs
│   │   │   ├── PaymentStatus.cs
│   │   │   └── UserRole.cs
│   │   ├── Exceptions/         # Custom exceptions
│   │   │   ├── NotFoundException.cs
│   │   │   └── ValidationException.cs
│   │   └── EerieTea.Core.csproj
│   │
│   ├── EerieTea.Infrastructure/  # Data Access & External Services
│   │   ├── Data/               # EF Core DbContext & Configurations
│   │   │   ├── ApplicationDbContext.cs
│   │   │   ├── Configurations/ # Entity configurations
│   │   │   │   ├── ProductConfiguration.cs
│   │   │   │   ├── OrderConfiguration.cs
│   │   │   │   └── UserConfiguration.cs
│   │   │   └── Migrations/    # EF Core migrations (gitignored, generated)
│   │   ├── Repositories/      # Repository implementations
│   │   │   ├── ProductRepository.cs
│   │   │   ├── OrderRepository.cs
│   │   │   └── IRepository.cs (base interface)
│   │   ├── Services/           # Service implementations
│   │   │   ├── ProductService.cs
│   │   │   ├── OrderService.cs
│   │   │   ├── CartService.cs
│   │   │   ├── EmailService.cs
│   │   │   └── PaymentService.cs
│   │   ├── External/           # External service integrations
│   │   │   ├── Stripe/
│   │   │   │   └── StripeService.cs
│   │   │   └── Resend/
│   │   │       └── ResendEmailService.cs
│   │   ├── Identity/          # ASP.NET Core Identity setup
│   │   │   └── IdentityServiceExtensions.cs
│   │   └── EerieTea.Infrastructure.csproj
│   │
│   └── EerieTea.Tests/        # Unit & Integration Tests
│       ├── UnitTests/
│       │   ├── Services/
│       │   │   ├── ProductServiceTests.cs
│       │   │   └── OrderServiceTests.cs
│       │   └── Controllers/
│       │       └── ProductsControllerTests.cs
│       ├── IntegrationTests/
│       │   ├── ApiTests/
│       │   │   └── ProductsApiTests.cs
│       │   └── DatabaseTests/
│       │       └── ProductRepositoryTests.cs
│       ├── TestHelpers/       # Test utilities
│       │   ├── TestDbContextFactory.cs
│       │   └── TestDataBuilder.cs
│       └── EerieTea.Tests.csproj
│
├── EerieTea.sln               # Solution file
├── .gitignore                 # Backend-specific gitignore
└── README.md                  # Backend README
```

---

## Key Points

### Frontend (Next.js)
- Uses **App Router** structure (`app/` directory)
- Route groups `(auth)` and `(shop)` for organization
- Components organized by feature/domain
- API client functions in `lib/api/` (calls backend API)
- Zustand stores for client-side state management
- TypeScript types matching backend DTOs

### Backend (.NET)
- **Layered Architecture**:
  - **Api**: Controllers, middleware, entry point
  - **Core**: Domain entities, DTOs, business logic interfaces
  - **Infrastructure**: Data access, external services, implementations
  - **Tests**: Unit and integration tests
- **Clean Architecture** principles
- Entity Framework Core for data access
- ASP.NET Core Identity for authentication
- Dependency Injection throughout

### Shared
- Both projects have their own `.gitignore`
- Root `.gitignore` covers common patterns
- Environment-specific configuration files
- Separate README files for each project

---

## Next Steps

1. Create the folder structure
2. Initialize Git repository (if not already done)
3. Set up frontend project (`npx create-next-app@16.1.1`)
4. Set up backend solution and projects (`dotnet new`)
5. Configure each project according to Task 1.2
