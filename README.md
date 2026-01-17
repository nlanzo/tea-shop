# Eerie Tea E-Commerce Platform

A modern, full-stack e-commerce platform for selling premium tea products online. Built with Next.js 16, TypeScript, and Prisma.

## Overview

Eerie Tea is an e-commerce platform designed specifically for tea enthusiasts, featuring detailed product information, brewing guides, and a seamless shopping experience. The platform enables customers to discover, browse, and purchase high-quality tea products with ease.

## Tech Stack

**Frontend:**

- **Framework:** Next.js 16.1.1 (App Router)
- **Language:** TypeScript 5.9+
- **Styling:** Tailwind CSS 4.1+ with shadcn/ui components
- **State Management:** Zustand
- **Forms:** React Hook Form + Zod validation
- **API Client:** Axios or Fetch API

**Backend:**

- **Framework:** .NET 10.0 with ASP.NET Core
- **Language:** C# 12.0
- **Database:** PostgreSQL with Entity Framework Core
- **Authentication:** ASP.NET Core Identity with JWT
- **Payments:** Stripe.net
- **Email:** Resend with Razor templates
- **API Documentation:** Swagger/OpenAPI

**Hosting:**

- **Frontend:** Vercel
- **Backend:** Azure App Service
- **Database:** Supabase

## Project Status

**Phase:** Planning & Setup  
**Current Status:** Project documentation and task planning complete

## Project Structure

```
eerie-tea/
├── project_management/     # Project documentation
│   ├── PRD.md              # Product Requirements Document
│   ├── TECH_STACK.md       # Detailed technology stack
│   └── PROJECT_TASKS.md   # Complete task breakdown
└── README.md               # This file
```

## Key Features (Planned)

### MVP (Phase 1)

- Product catalog with filtering and search
- Shopping cart and checkout
- User authentication and accounts
- Order management
- Admin panel for product/order management
- Email notifications

### Enhanced Features (Phase 2)

- Product reviews and ratings
- Subscription system
- Gift features (wrapping, messages, scheduled delivery)
- Advanced search and recommendations

### Advanced Features (Phase 3)

- Loyalty program
- Advanced analytics dashboard
- Shipping integrations

## Getting Started

### Prerequisites

- .NET SDK 10.0+
- Node.js 20.9+
- pnpm (recommended) or npm
- PostgreSQL database (or Supabase account)

### Installation

**Backend Setup:**

```bash
# Navigate to backend directory
cd backend

# Restore NuGet packages
dotnet restore

# Set up database connection in appsettings.json
# Run migrations
dotnet ef database update

# Seed database
dotnet run --project EerieTea.Api

# Run backend API
dotnet run --project EerieTea.Api
```

Backend API will run at [http://localhost:5000](http://localhost:5000) or [https://localhost:5001](https://localhost:5001)

**Frontend Setup:**

```bash
# Navigate to frontend directory
cd frontend

# Install dependencies
pnpm install

# Set up environment variables
cp .env.example .env.local
# Edit .env.local with API_URL pointing to backend

# Run development server
pnpm dev
```

Visit [http://localhost:3000](http://localhost:3000) to see the application.

## Documentation

- **[PRD.md](./project_management/PRD.md)** - Complete product requirements and specifications
- **[TECH_STACK.md](./project_management/TECH_STACK.md)** - Detailed technology stack and setup instructions
- **[PROJECT_TASKS.md](./project_management/PROJECT_TASKS.md)** - Comprehensive task breakdown for project management

## Development Phases

- **Phase 1 (MVP):** 8-12 weeks - Core e-commerce functionality
- **Phase 2 (Enhanced):** 6-8 weeks - Reviews, subscriptions, gift features
- **Phase 3 (Advanced):** 8-12 weeks - Loyalty program, analytics, integrations

## License

This is a portfolio project.

## Author

Built as a portfolio project to demonstrate full-stack e-commerce development.

---

**Note:** This project is currently in the planning phase. Development will begin following the task breakdown outlined in `PROJECT_TASKS.md`.
