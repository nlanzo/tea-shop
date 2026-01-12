# Eerie Tea - Technology Stack

**Last Updated:** January 2026  
**Next.js Version:** 16.1.1

---

## Core Framework & Language

### Frontend Framework

- **Next.js:** `16.1.1` ✅ (Specified)
  - App Router (recommended for new projects)
  - Built-in API Routes for backend functionality
  - Server Components and Server Actions
  - Built-in image optimization
  - Turbopack (default bundler)

### Programming Language

- **TypeScript:** `^5.9.2`
  - Static typing for better code quality
  - Required for Next.js 16 (TypeScript 5.1+)
  - Full type safety across the stack

### Runtime

- **Node.js:** `^20.9.0` or higher
  - Required by Next.js 16
  - LTS version recommended for stability

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

### ORM

- **Prisma:** `^6.0.0` (or latest stable)
  - Type-safe database client
  - Excellent TypeScript support
  - Migration system
  - Great developer experience
  - Prisma Studio for database management

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

### Authentication Library

- **NextAuth.js (Auth.js):** `^5.0.0` (or latest stable)
  - Built for Next.js
  - Supports multiple providers
  - Session management
  - JWT and database sessions
  - TypeScript support

**Alternative (if you want more features):**

- **Clerk:** Latest stable version
  - More features out of the box
  - Pre-built UI components
  - User management dashboard
  - May have costs for production

---

## Payment Processing

### Payment Gateway

- **Stripe:** `^17.0.0` (or latest stable)
  - Industry standard
  - Excellent Next.js integration
  - Comprehensive documentation
  - Test mode for development
  - PCI compliant

### Stripe Integration Libraries

- **@stripe/stripe-js:** Latest stable
- **@stripe/react-stripe-js:** Latest stable
- **stripe:** Latest stable (server-side)

**Note:** PayPal can be added later if needed (Phase 2)

---

## Email Service

### Email Provider

- **Resend:** `^4.0.0` (or latest stable) ⭐ Recommended
  - Developer-friendly API
  - Great for transactional emails
  - React Email support
  - Good free tier

**Alternatives:**

- **SendGrid:** Latest stable
  - More established
  - Higher free tier limits
- **AWS SES:** Via AWS SDK
  - Cost-effective at scale
  - More setup required

### Email Templates

- **React Email:** `^0.0.25` (or latest stable)
  - Build emails with React components
  - Works great with Resend
  - TypeScript support

---

## Testing

### Unit & Integration Testing

- **Vitest:** `^2.1.0` (or latest stable)
  - Fast test runner
  - Vite-powered
  - Jest-compatible API
  - Great TypeScript support

### Component Testing

- **React Testing Library:** `^16.0.0` (or latest stable)
  - Test components from user perspective
  - Works with Vitest

### End-to-End Testing

- **Playwright:** `^1.48.0` (or latest stable)
  - Modern E2E testing
  - Cross-browser testing
  - Great debugging tools
  - Better than Cypress for Next.js

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

### Frontend & Backend Hosting

- **Vercel:** ⭐ Recommended
  - Created by Next.js team
  - Zero-config deployment
  - Automatic HTTPS
  - Edge functions
  - Great free tier for portfolio projects
  - Preview deployments for PRs

**Alternatives:**

- **Netlify:** Good alternative
- **AWS Amplify:** If you prefer AWS ecosystem

### Database Hosting

- **Supabase** (recommended)
- **Railway**
- **Vercel Postgres** (if using Vercel)

### CDN

- **Vercel Edge Network** (included with Vercel)
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
├── app/                    # Next.js App Router
│   ├── (auth)/            # Auth routes
│   ├── (shop)/            # Shop routes
│   ├── admin/             # Admin routes
│   ├── api/               # API routes
│   └── layout.tsx         # Root layout
├── components/            # React components
│   ├── ui/                # shadcn/ui components
│   ├── cart/              # Cart components
│   ├── products/          # Product components
│   └── ...
├── lib/                   # Utility functions
│   ├── db/                # Database client (Prisma)
│   ├── auth/              # Auth configuration
│   ├── stripe/            # Stripe utilities
│   └── utils/             # Helper functions
├── hooks/                 # Custom React hooks
├── types/                 # TypeScript types
├── public/                # Static assets
├── prisma/                # Prisma schema and migrations
├── .env.local             # Environment variables (gitignored)
└── package.json
```

---

## Installation Commands

### Initial Setup

```bash
# Create Next.js project with TypeScript
npx create-next-app@16.1.1 eerie-tea --typescript --tailwind --app --use-pnpm

# Install core dependencies
pnpm add zustand react-hook-form zod @hookform/resolvers
pnpm add @prisma/client
pnpm add next-auth@beta  # or latest stable
pnpm add stripe @stripe/stripe-js @stripe/react-stripe-js
pnpm add resend react-email
pnpm add date-fns

# Install dev dependencies
pnpm add -D prisma
pnpm add -D vitest @testing-library/react @testing-library/jest-dom
pnpm add -D @playwright/test
pnpm add -D @biomejs/biome  # or prettier eslint-config-prettier

# Initialize Prisma
npx prisma init

# Initialize shadcn/ui (after project setup)
npx shadcn@latest init
```

---

## Version Compatibility Notes

- **Next.js 16.1.1** requires:

  - Node.js 20.9+
  - TypeScript 5.1+
  - React 19+ (comes with Next.js)

- **Prisma** works with:

  - PostgreSQL 12+
  - Node.js 18+

- **shadcn/ui** requires:
  - React 18+
  - Tailwind CSS 3.0+

---

## Decision Rationale

### Why Zustand over Redux?

- Simpler API, less boilerplate
- Better for smaller to medium applications
- Sufficient for e-commerce state needs

### Why Prisma over TypeORM/Drizzle?

- Best TypeScript support
- Excellent developer experience
- Great migration system
- Prisma Studio for database management
- Well-documented

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

### Why Vitest over Jest?

- Faster (Vite-powered)
- Better ESM support
- Jest-compatible API
- Great TypeScript support

---

## Next Steps

1. ✅ Technology stack finalized
2. ⏭️ Set up project structure
3. ⏭️ Initialize database schema
4. ⏭️ Set up authentication
5. ⏭️ Begin development

---

**Note:** All version numbers should be verified at installation time. Use `@latest` tag or check npm registry for most current stable versions.
