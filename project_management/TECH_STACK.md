# Eerie Tea - Technology Stack

**Last Updated:** January 2026  
**Next.js Version:** 16.1.1

---

## Core Framework & Language

### Frontend Framework

- **Next.js:** `16.1.1` ✅ (Specified)
  - App Router (recommended for new projects)
  - Client-side rendering (consumes .NET API)
  - Server Components for SEO
  - Built-in image optimization
  - Turbopack (default bundler)

### Backend Framework

- **.NET:** `10.0` (LTS) or latest stable

  - Cross-platform runtime
  - High performance
  - Strong typing with C#
  - Excellent for API development

- **ASP.NET Core:** `10.0` (matches .NET version)
  - Web API framework
  - RESTful API endpoints
  - Built-in dependency injection
  - Middleware pipeline
  - Swagger/OpenAPI support

### Programming Languages

- **TypeScript:** `^5.9.2` (Frontend)

  - Static typing for better code quality
  - Required for Next.js 16 (TypeScript 5.1+)
  - Full type safety on frontend

- **C#:** `12.0` (Backend)
  - Strongly typed language
  - Excellent tooling and IDE support
  - Modern language features

### Runtime

- **Node.js:** `^20.9.0` or higher (Frontend)

  - Required by Next.js 16
  - LTS version recommended for stability

- **.NET Runtime:** `10.0` (Backend)
  - Cross-platform (.NET runtime)
  - Can run on Windows, Linux, macOS

---

## Styling & UI

### CSS Framework

- **Tailwind CSS:** `^4.1.13`
  - Utility-first CSS framework
  - Excellent Next.js integration
  - Responsive design utilities
  - Dark mode support

### UI Component Library

- **shadcn/ui:** `^3.3.1`
  - Copy-paste components (not a dependency)
  - Built on Radix UI primitives
  - Fully customizable
  - Works seamlessly with Tailwind CSS
  - TypeScript support
  - Accessible by default

### Icons

- **Lucide React:** `^0.468.0` (or latest)
  - Modern icon library
  - Tree-shakeable
  - Works well with shadcn/ui

---

## State Management

### Client State

- **Zustand:** `^5.0.0` (or latest stable)
  - Lightweight and performant
  - Simple API
  - No boilerplate
  - Perfect for cart, user preferences, UI state

### Server State (Optional)

- **React Query / TanStack Query:** `^5.0.0` (or latest stable)
  - For server state management
  - Caching and synchronization
  - Useful for product data, orders

---

## Forms & Validation

### Form Handling

- **React Hook Form:** `^7.54.0` (or latest stable)
  - Performant form library
  - Minimal re-renders
  - Great developer experience

### Schema Validation

- **Zod:** `^3.24.1` (or latest stable)
  - TypeScript-first schema validation
  - Works perfectly with React Hook Form
  - Type inference
  - Client and server-side validation

---

## Database & ORM

### Database

- **PostgreSQL:** Latest stable version
  - Robust relational database
  - ACID compliance
  - Excellent for e-commerce data
  - Works well with Entity Framework Core

### ORM

- **Entity Framework Core:** `10.0.x` (matches .NET version)
  - Official .NET ORM
  - Code-first migrations
  - LINQ support
  - Change tracking
  - Excellent C# integration
  - Database provider flexibility

**Alternative (if needed):**

- **Dapper:** Latest stable
  - Lightweight micro-ORM
  - Faster for simple queries
  - Can be used alongside EF Core

### Database Hosting Options

- **Supabase** (recommended for portfolio project)
  - Free tier available
  - Managed PostgreSQL
  - Built-in auth (optional)
  - Real-time subscriptions
- **Railway** (alternative)
  - Simple PostgreSQL hosting
  - Good free tier
- **Vercel Postgres** (if deploying on Vercel)
  - Seamless integration
  - Serverless Postgres

### Caching (Optional for MVP)

- **Redis:** Latest stable version
  - For session storage
  - Caching frequently accessed data
  - Can use Upstash Redis (serverless) if needed

---

## Authentication

### Backend Authentication

- **ASP.NET Core Identity:** Built into ASP.NET Core

  - User management and authentication
  - Password hashing
  - Role-based authorization
  - Token generation (JWT)
  - Email confirmation
  - Password reset functionality

- **JWT Bearer Authentication:** `Microsoft.AspNetCore.Authentication.JwtBearer`
  - JWT token validation
  - Stateless authentication
  - Works with frontend SPA
  - Secure token handling

### Frontend Authentication

- **Custom Auth Implementation:** Using React Context/Zustand
  - Store JWT tokens securely
  - Handle login/logout
  - Token refresh logic
  - Protected routes

**Alternative:**

- **Auth0** or **Clerk:** Latest stable version
  - Third-party authentication service
  - Pre-built UI components
  - User management dashboard
  - May have costs for production

---

## Payment Processing

### Payment Gateway

- **Stripe:** Latest stable
  - Industry standard
  - Comprehensive documentation
  - Test mode for development
  - PCI compliant

### Stripe Integration Libraries

**Backend (.NET):**

- **Stripe.net:** Latest stable
  - Official .NET SDK for Stripe
  - Server-side payment processing
  - Webhook handling

**Frontend (Next.js):**

- **@stripe/stripe-js:** Latest stable
- **@stripe/react-stripe-js:** Latest stable
  - Client-side Stripe Elements
  - Payment form components

**Note:** PayPal can be added later if needed (Phase 2)

---

## Email Service

### Email Provider

- **Resend:** Latest stable (Recommended)
  - Developer-friendly API
  - Great for transactional emails
  - Good free tier
  - .NET SDK available

**Alternatives:**

- **SendGrid:** Latest stable
  - More established
  - Higher free tier limits
  - Official .NET SDK
- **AWS SES:** Via AWS SDK for .NET
  - Cost-effective at scale
  - More setup required
- **MailKit:** Latest stable
  - Open-source .NET email library
  - Works with SMTP servers

### Email Templates

- **Razor Email Templates:** Built into ASP.NET Core
  - Server-side email rendering
  - C# templating engine
  - Can use Razor views for emails

**Alternative:**

- **React Email:** Latest stable
  - Build emails with React components
  - Can be rendered server-side
  - Works with Resend

---

## Testing

### Backend Testing (.NET)

- **xUnit:** Latest stable (Recommended)

  - .NET testing framework
  - Clean, simple API
  - Great tooling support

- **Moq:** Latest stable

  - Mocking framework for .NET
  - Easy to use
  - Type-safe mocks

- **FluentAssertions:** Latest stable
  - Fluent assertion library
  - Readable test assertions
  - Better error messages

### Frontend Testing

- **Vitest:** `^2.1.0` (or latest stable)

  - Fast test runner
  - Vite-powered
  - Jest-compatible API
  - Great TypeScript support

- **React Testing Library:** `^16.0.0` (or latest stable)
  - Test components from user perspective
  - Works with Vitest

### End-to-End Testing

- **Playwright:** `^1.48.0` (or latest stable)
  - Modern E2E testing
  - Cross-browser testing
  - Great debugging tools
  - Tests both frontend and backend integration

---

## Code Quality & Tooling

### Linting

- **ESLint:** `^9.0.0` (or latest stable)
  - Code quality and error detection
  - Next.js ESLint config included

### Formatting

- **Biome:** `^1.9.0` (or latest stable) ⭐ Recommended
  - Fast formatter and linter
  - Written in Rust
  - Can replace Prettier + ESLint
  - Better performance

**Alternative:**

- **Prettier:** `^3.3.0` (or latest stable)
  - If you prefer Prettier
  - Works well with ESLint

### Type Checking

- **TypeScript:** Built-in type checking
- **tsc --noEmit** in CI/CD

---

## Package Manager

### Package Manager

- **pnpm:** `^9.0.0` (or latest stable) ⭐ Recommended
  - Faster than npm/yarn
  - Efficient disk usage
  - Better for monorepos
  - Strict dependency resolution

**Alternatives:**

- **npm:** Comes with Node.js
- **yarn:** Classic or Yarn Berry

---

## Deployment & Hosting

### Frontend Hosting

- **Vercel:** Recommended
  - Created by Next.js team
  - Zero-config deployment
  - Automatic HTTPS
  - Great free tier for portfolio projects
  - Preview deployments for PRs

**Alternatives:**

- **Netlify:** Good alternative
- **AWS Amplify:** If you prefer AWS ecosystem

### Backend Hosting

- **Azure App Service:** Recommended for .NET
  - Native .NET support
  - Easy deployment
  - Auto-scaling
  - Good free tier

**Alternatives:**

- **AWS Elastic Beanstalk:** Good .NET support
- **Railway:** Simple deployment
- **DigitalOcean App Platform:** Good pricing
- **Docker Containers:** Deploy anywhere (Azure Container Apps, AWS ECS, etc.)

### Database Hosting

- **Supabase:** Recommended
  - Free tier available
  - Managed PostgreSQL
  - Good for portfolio projects
- **Azure Database for PostgreSQL:** If using Azure
- **Railway:** Simple PostgreSQL hosting
- **AWS RDS:** If using AWS

### CDN

- **Vercel Edge Network** (included with Vercel for frontend)
- **Azure CDN** (if using Azure)
- **Cloudflare** (if using custom domain)

---

## Analytics & Monitoring

### Analytics

- **Vercel Analytics:** Built-in with Vercel
  - Web Vitals tracking
  - Real-time analytics
- **Google Analytics 4:** `gtag` or `@next/third-parties`
  - For detailed user analytics

### Error Tracking (Optional for MVP)

- **Sentry:** Latest stable
  - Error tracking and monitoring
  - Good free tier

---

## Shipping Integration (Phase 2)

### Shipping APIs

- **EasyPost:** Latest stable
  - Multi-carrier shipping API
  - Rate calculation
  - Label generation
- **ShipStation API:** If preferred

---

## Development Tools

### Environment Variables

- **dotenv:** Built into Next.js
- Use `.env.local` for local development

### API Client

- **Native Fetch API:** Built into Next.js
- **axios:** `^1.7.0` (optional, if you prefer)

### Date Handling

- **date-fns:** `^4.0.0` (or latest stable)
  - Lightweight date utility library
  - Tree-shakeable

### Image Optimization

- **next/image:** Built into Next.js
- **Sharp:** Automatically installed by Next.js

---

## Security

### Security Libraries

- **bcryptjs:** `^2.4.3` (or latest stable)
  - Password hashing
- **jsonwebtoken:** `^9.0.2` (or latest stable)
  - JWT tokens (if not using NextAuth)
- **helmet:** `^8.0.0` (or latest stable)
  - Security headers (if needed)

---

## Recommended Project Structure

```
eerie-tea/
├── frontend/              # Next.js frontend application
│   ├── app/              # Next.js App Router
│   │   ├── (auth)/      # Auth routes
│   │   ├── (shop)/      # Shop routes
│   │   ├── admin/       # Admin routes
│   │   └── layout.tsx   # Root layout
│   ├── components/       # React components
│   │   ├── ui/          # shadcn/ui components
│   │   ├── cart/        # Cart components
│   │   └── products/    # Product components
│   ├── lib/             # Utility functions
│   │   ├── api/         # API client functions
│   │   ├── auth/        # Auth utilities
│   │   └── utils/       # Helper functions
│   ├── hooks/           # Custom React hooks
│   ├── types/           # TypeScript types
│   ├── public/          # Static assets
│   └── package.json
│
├── backend/             # .NET backend API
│   ├── EerieTea.Api/    # Web API project
│   │   ├── Controllers/ # API controllers
│   │   ├── Models/      # Data models/DTOs
│   │   ├── Services/    # Business logic services
│   │   ├── Data/        # DbContext and repositories
│   │   ├── Middleware/  # Custom middleware
│   │   └── Program.cs   # Application entry point
│   ├── EerieTea.Core/   # Core domain models
│   ├── EerieTea.Infrastructure/ # Infrastructure (EF Core, etc.)
│   └── EerieTea.Tests/  # Unit and integration tests
│
└── project_management/  # Project documentation
    ├── PRD.md
    ├── TECH_STACK.md
    └── PROJECT_TASKS.md
```

---

## Installation Commands

### Backend Setup (.NET)

```bash
# Create solution
dotnet new sln -n EerieTea

# Create Web API project
dotnet new webapi -n EerieTea.Api -f net10.0

# Create class library projects
dotnet new classlib -n EerieTea.Core -f net10.0
dotnet new classlib -n EerieTea.Infrastructure -f net10.0
dotnet new xunit -n EerieTea.Tests -f net10.0

# Add projects to solution
dotnet sln add EerieTea.Api/EerieTea.Api.csproj
dotnet sln add EerieTea.Core/EerieTea.Core.csproj
dotnet sln add EerieTea.Infrastructure/EerieTea.Infrastructure.csproj
dotnet sln add EerieTea.Tests/EerieTea.Tests.csproj

# Add NuGet packages
cd EerieTea.Api
dotnet add package Microsoft.EntityFrameworkCore.Design
dotnet add package Npgsql.EntityFrameworkCore.PostgreSQL
dotnet add package Microsoft.AspNetCore.Identity.EntityFrameworkCore
dotnet add package Microsoft.AspNetCore.Authentication.JwtBearer
dotnet add package Stripe.net
dotnet add package Swashbuckle.AspNetCore

cd ../EerieTea.Infrastructure
dotnet add package Microsoft.EntityFrameworkCore
dotnet add package Npgsql.EntityFrameworkCore.PostgreSQL
dotnet add package Microsoft.AspNetCore.Identity.EntityFrameworkCore

cd ../EerieTea.Tests
dotnet add package xunit
dotnet add package Moq
dotnet add package FluentAssertions
dotnet add package Microsoft.AspNetCore.Mvc.Testing
```

### Frontend Setup (Next.js)

```bash
# Create Next.js project with TypeScript
npx create-next-app@16.1.1 frontend --typescript --tailwind --app --use-pnpm

cd frontend

# Install core dependencies
pnpm add zustand react-hook-form zod @hookform/resolvers
pnpm add @stripe/stripe-js @stripe/react-stripe-js
pnpm add date-fns
pnpm add axios  # For API calls to .NET backend

# Install dev dependencies
pnpm add -D vitest @testing-library/react @testing-library/jest-dom
pnpm add -D @playwright/test
pnpm add -D @biomejs/biome

# Initialize shadcn/ui
npx shadcn@latest init
```

---

## Version Compatibility Notes

- **Next.js 16.1.1** requires:

  - Node.js 20.9+
  - TypeScript 5.1+
  - React 19+ (comes with Next.js)

- **.NET 10.0** requires:

  - .NET SDK 10.0+
  - Can run on Windows, Linux, macOS
  - Visual Studio 2022 or VS Code recommended

- **Entity Framework Core 10.0** works with:

  - PostgreSQL 12+
  - SQL Server 2012+
  - MySQL 5.7+

- **shadcn/ui** requires:
  - React 18+
  - Tailwind CSS 3.0+

---

## Decision Rationale

### Why Zustand over Redux?

- Simpler API, less boilerplate
- Better for smaller to medium applications
- Sufficient for e-commerce state needs

### Why Entity Framework Core over Prisma/Dapper?

- Native .NET integration
- Official Microsoft ORM
- Excellent LINQ support
- Code-first migrations
- Strong typing with C#
- Well-documented and widely used
- Great tooling support (Visual Studio, Rider)

### Why shadcn/ui over Material-UI/Chakra?

- More customizable
- Copy-paste approach (no dependency)
- Built on Radix UI (accessible)
- Works perfectly with Tailwind
- Modern design

### Why Resend over SendGrid?

- Better developer experience
- React Email support
- Simpler API
- Good for portfolio projects

### Why .NET Backend?

- High performance and scalability
- Strong typing with C#
- Excellent tooling and IDE support
- Built-in dependency injection
- Comprehensive framework (auth, validation, etc.)
- Cross-platform deployment
- Great for API development

### Why xUnit over NUnit/MSTest?

- Clean, simple API
- Better async/await support
- Great tooling integration
- Modern testing patterns

---

## Next Steps

1. ✅ Technology stack finalized
2. ⏭️ Set up project structure
3. ⏭️ Initialize database schema
4. ⏭️ Set up authentication
5. ⏭️ Begin development

---

**Note:** All version numbers should be verified at installation time. Use `@latest` tag or check npm registry for most current stable versions.
