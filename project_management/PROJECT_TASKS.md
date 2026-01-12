# Eerie Tea E-Commerce Project Task Breakdown

This document provides a comprehensive task breakdown organized for project management systems like Monday.com. Tasks are organized by phases with dependencies, priorities, and estimated effort.

**Technology Stack:** Next.js 16.1.1 (App Router), TypeScript, Prisma, Zustand, Tailwind CSS, shadcn/ui, NextAuth.js, Stripe, Resend, Vercel, Supabase  
**See `TECH_STACK.md` for detailed technology information.**

---

## Phase 1: MVP (Minimum Viable Product) - 8-12 weeks

### Epic 1: Project Setup & Infrastructure

#### Task 1.1: Technical Architecture & Planning

- **Priority:** Critical
- **Estimated Time:** 1 week
- **Dependencies:** None
- **Subtasks:**
  - [x] Finalize technology stack decisions (Next.js 16.1.1, TypeScript, Prisma, Zustand, etc.)
  - [ ] Create technical architecture diagram
  - [ ] Set up version control repository (Git)
  - [ ] Create project folder structure (Next.js App Router structure)
  - [ ] Set up development environment documentation
  - [ ] Define coding standards and conventions (TypeScript, ESLint, Biome)
  - [ ] Set up code review process

#### Task 1.2: Development Environment Setup

- **Priority:** Critical
- **Estimated Time:** 3-5 days
- **Dependencies:** Task 1.1
- **Subtasks:**
  - [ ] Install Node.js 20.9+ and verify version
  - [ ] Create Next.js 16.1.1 project with TypeScript and App Router (`create-next-app`)
  - [ ] Set up pnpm package manager
  - [ ] Configure TypeScript (tsconfig.json) - verify strict mode
  - [ ] Install and configure Prisma ORM
  - [ ] Set up local PostgreSQL database (or connect to Supabase)
  - [ ] Configure environment variables (.env.local files)
  - [ ] Install and configure ESLint (Next.js config)
  - [ ] Install and configure Biome (or Prettier) for formatting
  - [ ] Set up Vitest testing framework
  - [ ] Set up Playwright for E2E testing
  - [ ] Initialize shadcn/ui component library (`npx shadcn@latest init`)
  - [ ] Configure Next.js Image domains (if using external images)
  - [ ] Set up Git repository and .gitignore
  - [ ] Configure Next.js app structure (app directory, layout, etc.)

#### Task 1.3: Database Schema Design & Setup

- **Priority:** Critical
- **Estimated Time:** 1 week
- **Dependencies:** Task 1.2
- **Subtasks:**
  - [ ] Design database schema (users, products, orders, cart, addresses, etc.)
  - [ ] Create Prisma schema file (schema.prisma)
  - [ ] Define all models (User, Product, Order, OrderItem, Cart, Address, etc.)
  - [ ] Set up Prisma relations and foreign keys
  - [ ] Create initial Prisma migration
  - [ ] Run Prisma migrations to create database tables
  - [ ] Set up database indexes in Prisma schema for performance
  - [ ] Create Prisma seed script for initial 30 tea products
  - [ ] Run seed script to populate database
  - [ ] Set up Prisma Studio for database management
  - [ ] Document database schema and relationships

#### Task 1.4: CI/CD Pipeline Setup

- **Priority:** High
- **Estimated Time:** 2-3 days
- **Dependencies:** Task 1.2
- **Subtasks:**
  - [ ] Set up GitHub Actions workflow
  - [ ] Configure automated testing (Vitest unit tests)
  - [ ] Configure E2E testing in CI (Playwright)
  - [ ] Set up automated deployment to Vercel preview (on PR)
  - [ ] Configure Vercel project settings
  - [ ] Set up environment variables in Vercel dashboard
  - [ ] Configure build and deployment scripts
  - [ ] Test CI/CD pipeline with a test commit

#### Task 1.5: Hosting & Infrastructure Setup

- **Priority:** High
- **Estimated Time:** 2-3 days
- **Dependencies:** Task 1.2
- **Subtasks:**
  - [ ] Create Vercel account and connect GitHub repository
  - [ ] Set up Supabase account for PostgreSQL database
  - [ ] Create Supabase project and get connection string
  - [ ] Configure database connection in Prisma
  - [ ] Configure environment variables in Vercel (DATABASE_URL, etc.)
  - [ ] Configure environment variables in Supabase (if needed)
  - [ ] Set up custom domain name (optional for MVP)
  - [ ] Configure DNS settings (if using custom domain)
  - [ ] Verify SSL certificates (automatic with Vercel)
  - [ ] Test database connection from Vercel environment
  - [ ] Set up Vercel preview deployments for staging

---

### Epic 2: Authentication & User Management

#### Task 2.1: User Registration & Login

- **Priority:** Critical
- **Estimated Time:** 1 week
- **Dependencies:** Task 1.3
- **Subtasks:**
  - [ ] Install and configure NextAuth.js (Auth.js)
  - [ ] Set up NextAuth.js configuration file
  - [ ] Configure Prisma adapter for NextAuth.js
  - [ ] Design user registration form UI (using shadcn/ui components)
  - [ ] Implement registration form with React Hook Form + Zod validation
  - [ ] Create Next.js API route for user registration
  - [ ] Implement password hashing (bcryptjs)
  - [ ] Add email uniqueness validation
  - [ ] Design login form UI (using shadcn/ui components)
  - [ ] Implement login form with React Hook Form + Zod validation
  - [ ] Configure NextAuth.js credentials provider
  - [ ] Set up session management (database sessions)
  - [ ] Add form validation (Zod schemas for frontend and backend)
  - [ ] Handle authentication errors gracefully
  - [ ] Create protected route middleware

#### Task 2.2: Password Reset Functionality

- **Priority:** High
- **Estimated Time:** 3-4 days
- **Dependencies:** Task 2.1, Task 8.1
- **Subtasks:**
  - [ ] Design "Forgot Password" UI (using shadcn/ui components)
  - [ ] Implement password reset request API route
  - [ ] Set up Resend email service account
  - [ ] Install React Email and configure
  - [ ] Create password reset email template (React Email)
  - [ ] Add password reset token field to User model in Prisma
  - [ ] Implement password reset token generation and storage
  - [ ] Implement token expiration logic (24-hour expiry)
  - [ ] Design password reset form UI
  - [ ] Implement password reset completion API route
  - [ ] Add token validation and expiration handling
  - [ ] Test email delivery in development

#### Task 2.3: User Profile Management

- **Priority:** High
- **Estimated Time:** 1 week
- **Dependencies:** Task 2.1
- **Subtasks:**
  - [ ] Design user profile page UI (using shadcn/ui components)
  - [ ] Create profile page route (Next.js App Router)
  - [ ] Implement Server Component for profile view
  - [ ] Create profile update Server Action
  - [ ] Implement profile update form with React Hook Form + Zod
  - [ ] Add email verification functionality (using Resend)
  - [ ] Create email verification API route
  - [ ] Implement password change functionality
  - [ ] Add password change form with validation
  - [ ] Add profile picture upload (optional - using Next.js Image API)
  - [ ] Create account settings page
  - [ ] Add protected route middleware for profile pages

#### Task 2.4: Address Management

- **Priority:** High
- **Estimated Time:** 3-4 days
- **Dependencies:** Task 2.1
- **Subtasks:**
  - [ ] Design address management UI (using shadcn/ui components)
  - [ ] Create Address model in Prisma schema
  - [ ] Create Prisma migration for Address model
  - [ ] Create address management page route
  - [ ] Implement add address Server Action
  - [ ] Implement update address Server Action
  - [ ] Implement delete address Server Action
  - [ ] Implement set default address Server Action
  - [ ] Add address form with React Hook Form + Zod validation
  - [ ] Add address validation (required fields, US address format)
  - [ ] Display saved addresses list

---

### Epic 3: Product Catalog

#### Task 3.1: Product Database & Models

- **Priority:** Critical
- **Estimated Time:** 3-4 days
- **Dependencies:** Task 1.3
- **Subtasks:**
  - [ ] Create Product model in Prisma schema
  - [ ] Add product fields (name, description, price, images, origin, caffeine level, flavor notes, etc.)
  - [ ] Create Category model in Prisma schema
  - [ ] Create ProductImage model for multiple images
  - [ ] Set up Prisma relations (Product-Category, Product-ProductImage)
  - [ ] Add inventory quantity field to Product model
  - [ ] Create Prisma migration for Product models
  - [ ] Update Prisma seed script with 30 tea products
  - [ ] Add product seed data (names, descriptions, prices, images, categories)
  - [ ] Run Prisma seed to populate products
  - [ ] Verify product data in Prisma Studio

#### Task 3.2: Product Listing Page

- **Priority:** Critical
- **Estimated Time:** 1 week
- **Dependencies:** Task 3.1
- **Subtasks:**
  - [ ] Design product listing page layout (using Tailwind CSS)
  - [ ] Create products page route (Next.js App Router)
  - [ ] Implement Server Component to fetch products with Prisma
  - [ ] Add pagination logic (server-side)
  - [ ] Create product card component (using shadcn/ui Card)
  - [ ] Implement product grid layout (CSS Grid/Tailwind)
  - [ ] Add product grid/list view toggle (client component)
  - [ ] Implement pagination component (using shadcn/ui)
  - [ ] Add loading states (Next.js loading.tsx)
  - [ ] Add empty state handling
  - [ ] Optimize product images (Next.js Image component with lazy loading)
  - [ ] Make responsive for mobile devices (Tailwind responsive classes)
  - [ ] Add search params handling for filters (URL state)

#### Task 3.3: Product Filtering & Sorting

- **Priority:** High
- **Estimated Time:** 1 week
- **Dependencies:** Task 3.2
- **Subtasks:**
  - [ ] Design filter sidebar/panel UI (using shadcn/ui components)
  - [ ] Implement filter by category (Prisma query)
  - [ ] Implement filter by price range (Prisma query)
  - [ ] Implement filter by origin (Prisma query)
  - [ ] Implement filter by caffeine level (Prisma query)
  - [ ] Implement filter by flavor notes (Prisma query)
  - [ ] Implement sort by price (low to high, high to low) - Prisma orderBy
  - [ ] Implement sort by popularity (Prisma orderBy)
  - [ ] Implement sort by newest (Prisma orderBy createdAt)
  - [ ] Add filter reset functionality
  - [ ] Update URL search params for filters (Next.js useSearchParams)
  - [ ] Combine multiple filters (Prisma where clause)

#### Task 3.4: Product Search

- **Priority:** High
- **Estimated Time:** 3-4 days
- **Dependencies:** Task 3.2
- **Subtasks:**
  - [ ] Design search bar UI (header component)
  - [ ] Create search API route (Next.js API route)
  - [ ] Implement search with Prisma (contains/full-text search)
  - [ ] Add search by product name (Prisma where contains)
  - [ ] Add search by ingredients/description (Prisma where contains)
  - [ ] Implement search suggestions/autocomplete (debounced API call)
  - [ ] Create search results page route
  - [ ] Handle empty search results
  - [ ] Add search history (for logged-in users - store in database)
  - [ ] Add search debouncing (client-side)

#### Task 3.5: Product Detail Page

- **Priority:** Critical
- **Estimated Time:** 1.5 weeks
- **Dependencies:** Task 3.1
- **Subtasks:**
  - [ ] Design product detail page layout (using Tailwind CSS)
  - [ ] Create dynamic product page route [slug] (Next.js App Router)
  - [ ] Implement Server Component to fetch product by slug with Prisma
  - [ ] Create product image gallery component (using Next.js Image)
  - [ ] Display product name, price, description
  - [ ] Add tasting notes section
  - [ ] Add origin information section
  - [ ] Add brewing instructions section
  - [ ] Create quantity selector component (using shadcn/ui)
  - [ ] Add "Add to Cart" button (client component)
  - [ ] Display stock availability indicator
  - [ ] Add related/recommended products section (fetch from Prisma)
  - [ ] Make responsive for mobile devices
  - [ ] Add SEO meta tags (Next.js metadata API)
  - [ ] Generate static params for product pages (if using SSG)

---

### Epic 4: Shopping Cart

#### Task 4.1: Cart State Management

- **Priority:** Critical
- **Estimated Time:** 3-4 days
- **Dependencies:** Task 3.5
- **Subtasks:**
  - [ ] Install and set up Zustand for cart state management
  - [ ] Create cart store with Zustand (add, remove, update quantity)
  - [ ] Implement add to cart functionality (client-side)
  - [ ] Implement remove from cart functionality
  - [ ] Implement update cart item quantity
  - [ ] Persist cart to localStorage (guest users) using Zustand persist middleware
  - [ ] Create Cart model in Prisma schema (for logged-in users)
  - [ ] Create API routes for cart sync (POST, GET, DELETE)
  - [ ] Sync cart with backend for logged-in users
  - [ ] Handle cart merge on login (merge localStorage cart with database cart)
  - [ ] Add cart item count to header (Zustand subscription)

#### Task 4.2: Cart Page UI

- **Priority:** Critical
- **Estimated Time:** 1 week
- **Dependencies:** Task 4.1
- **Subtasks:**
  - [ ] Design shopping cart page layout
  - [ ] Create cart item component
  - [ ] Display cart items with images and details
  - [ ] Add quantity update controls
  - [ ] Add remove item button
  - [ ] Display subtotal calculation
  - [ ] Add "Continue Shopping" button
  - [ ] Add "Proceed to Checkout" button
  - [ ] Handle empty cart state
  - [ ] Make responsive for mobile devices

#### Task 4.3: Cart Calculations

- **Priority:** Critical
- **Estimated Time:** 2-3 days
- **Dependencies:** Task 4.2
- **Subtasks:**
  - [ ] Implement subtotal calculation
  - [ ] Implement shipping cost calculation
  - [ ] Implement tax calculation
  - [ ] Implement total calculation
  - [ ] Display all calculations on cart page
  - [ ] Update calculations in real-time

---

### Epic 5: Checkout Process

#### Task 5.1: Checkout Flow Design

- **Priority:** Critical
- **Estimated Time:** 2-3 days
- **Dependencies:** Task 4.2
- **Subtasks:**
  - [ ] Design checkout flow (multi-step or single page)
  - [ ] Create checkout step indicator
  - [ ] Design shipping information form
  - [ ] Design payment form
  - [ ] Design order review section
  - [ ] Design order confirmation page

#### Task 5.2: Shipping Information Step

- **Priority:** Critical
- **Estimated Time:** 1 week
- **Dependencies:** Task 5.1, Task 2.4
- **Subtasks:**
  - [ ] Create shipping address form component (React Hook Form + Zod)
  - [ ] Add form validation (Zod schema - required fields, email format, US address format)
  - [ ] Implement guest checkout option (no account required)
  - [ ] Implement account creation option during checkout (NextAuth.js)
  - [ ] Add saved addresses dropdown for logged-in users (fetch from Prisma)
  - [ ] Implement shipping method selection (Standard, Express, etc.)
  - [ ] Calculate and display shipping costs (fixed rates for MVP)
  - [ ] Display estimated delivery dates (calculate based on shipping method)
  - [ ] Add address autocomplete (optional - Google Places API)
  - [ ] Store shipping info in checkout state (Zustand or form state)

#### Task 5.3: Payment Integration

- **Priority:** Critical
- **Estimated Time:** 1.5 weeks
- **Dependencies:** Task 5.2
- **Subtasks:**
  - [ ] Set up Stripe account and get API keys
  - [ ] Install Stripe packages (@stripe/stripe-js, @stripe/react-stripe-js, stripe)
  - [ ] Configure Stripe environment variables
  - [ ] Create Stripe payment intent API route
  - [ ] Integrate Stripe Elements payment form (client component)
  - [ ] Implement credit card processing with Stripe
  - [ ] Add payment form validation (Stripe + Zod)
  - [ ] Handle payment errors gracefully
  - [ ] Ensure PCI compliance (handled by Stripe)
  - [ ] Test payment processing in Stripe test mode
  - [ ] Add payment success/failure handling
  - [ ] Create webhook endpoint for Stripe events

#### Task 5.4: Order Processing

- **Priority:** Critical
- **Estimated Time:** 1 week
- **Dependencies:** Task 5.3
- **Subtasks:**
  - [ ] Create Order and OrderItem models in Prisma schema
  - [ ] Create Prisma migration for Order models
  - [ ] Implement order creation Server Action
  - [ ] Link order to user (if logged in) via Prisma relation
  - [ ] Store order items with Prisma
  - [ ] Store shipping and payment information
  - [ ] Generate unique order number (format: ORDER-YYYYMMDD-XXXX)
  - [ ] Update inventory after order (Prisma transaction)
  - [ ] Handle out-of-stock items (check before order creation)
  - [ ] Create order confirmation page route
  - [ ] Implement order confirmation email (using Resend + React Email)
  - [ ] Add order status tracking

#### Task 5.5: Discount Codes & Promotions

- **Priority:** Medium
- **Estimated Time:** 3-4 days
- **Dependencies:** Task 5.4
- **Subtasks:**
  - [ ] Create discount code database model
  - [ ] Design discount code input field
  - [ ] Implement discount code validation endpoint
  - [ ] Apply discount to order total
  - [ ] Display discount in order summary
  - [ ] Handle invalid/expired discount codes

---

### Epic 6: Order Management

#### Task 6.1: Order History (User)

- **Priority:** High
- **Estimated Time:** 1 week
- **Dependencies:** Task 5.4, Task 2.1
- **Subtasks:**
  - [ ] Design order history page (protected route)
  - [ ] Create order history page route (Server Component)
  - [ ] Fetch user orders with Prisma (filter by userId)
  - [ ] Display list of past orders
  - [ ] Show order details (items, total, date, status)
  - [ ] Add order filtering (by date, status) - Prisma queries
  - [ ] Add order search functionality (by order number)
  - [ ] Add pagination for order list
  - [ ] Make responsive for mobile devices
  - [ ] Add loading states

#### Task 6.2: Order Tracking

- **Priority:** High
- **Estimated Time:** 3-4 days
- **Dependencies:** Task 6.1
- **Subtasks:**
  - [ ] Design order tracking page (dynamic route [orderId])
  - [ ] Create order tracking page route (Server Component)
  - [ ] Fetch order details with Prisma
  - [ ] Display order status (pending, processing, shipped, delivered)
  - [ ] Show order timeline/status updates (OrderStatusHistory model if needed)
  - [ ] Display tracking number (if available)
  - [ ] Add order details view (reuse from order history)
  - [ ] Implement order status update notifications (email via Resend)
  - [ ] Add protected route (verify user owns order)

---

### Epic 7: Admin Panel

#### Task 7.1: Admin Authentication & Authorization

- **Priority:** Critical
- **Estimated Time:** 3-4 days
- **Dependencies:** Task 2.1
- **Subtasks:**
  - [ ] Add role field to User model in Prisma schema (admin, user)
  - [ ] Create Prisma migration for role field
  - [ ] Create admin user seed data
  - [ ] Implement admin login page (reuse NextAuth.js with role check)
  - [ ] Add role-based access control middleware (check user role)
  - [ ] Protect admin routes (middleware or Server Component check)
  - [ ] Create admin dashboard layout component
  - [ ] Add admin navigation/sidebar
  - [ ] Create admin route group (/admin)

#### Task 7.2: Product Management (Admin)

- **Priority:** Critical
- **Estimated Time:** 1.5 weeks
- **Dependencies:** Task 7.1, Task 3.1
- **Subtasks:**
  - [ ] Design product management page (admin layout)
  - [ ] Implement product list view (admin) - Server Component with Prisma
  - [ ] Create add product form (React Hook Form + Zod)
  - [ ] Implement create product Server Action
  - [ ] Create edit product form (pre-populated)
  - [ ] Implement update product Server Action
  - [ ] Implement delete product Server Action
  - [ ] Add product image upload functionality (Next.js API route + file upload)
  - [ ] Store images (local storage or cloud storage like Vercel Blob/Cloudinary)
  - [ ] Add bulk product operations (bulk delete, bulk update)
  - [ ] Add product search/filter for admin (Prisma queries)
  - [ ] Add pagination for admin product list

#### Task 7.3: Order Management (Admin)

- **Priority:** Critical
- **Estimated Time:** 1 week
- **Dependencies:** Task 7.1, Task 5.4
- **Subtasks:**
  - [ ] Design order management page (admin layout)
  - [ ] Implement order list view (admin) - Server Component with Prisma
  - [ ] Add order filtering (by status, date, customer) - Prisma where clauses
  - [ ] Create order detail view (Server Component)
  - [ ] Implement order status update Server Action
  - [ ] Add order notes/comments (create OrderNote model if needed)
  - [ ] Export orders to CSV (optional - API route)
  - [ ] Add order search functionality (Prisma search)
  - [ ] Add pagination for order list
  - [ ] Display order totals and statistics

#### Task 7.4: Inventory Management (Admin)

- **Priority:** High
- **Estimated Time:** 1 week
- **Dependencies:** Task 7.2
- **Subtasks:**
  - [ ] Design inventory management page (admin layout)
  - [ ] Display product inventory levels (Server Component with Prisma)
  - [ ] Implement update inventory Server Action
  - [ ] Add low stock alerts/warnings (calculate threshold)
  - [ ] Add inventory history tracking (create InventoryHistory model if needed)
  - [ ] Implement bulk inventory update (Server Action)
  - [ ] Add inventory filtering and search
  - [ ] Display inventory statistics

#### Task 7.5: Customer Management (Admin)

- **Priority:** Medium
- **Estimated Time:** 3-4 days
- **Dependencies:** Task 7.1
- **Subtasks:**
  - [ ] Design customer management page
  - [ ] Implement customer list view
  - [ ] Add customer search functionality
  - [ ] Display customer details
  - [ ] View customer order history
  - [ ] Add customer notes

---

### Epic 8: Email Notifications

#### Task 8.1: Email Service Setup

- **Priority:** High
- **Estimated Time:** 2-3 days
- **Dependencies:** Task 1.2
- **Subtasks:**
  - [ ] Set up Resend account and get API key
  - [ ] Install Resend and React Email packages
  - [ ] Configure Resend environment variables
  - [ ] Set up React Email development server
  - [ ] Create email template structure
  - [ ] Configure email sending utility function
  - [ ] Test email delivery in development
  - [ ] Set up email domain verification (if using custom domain)

#### Task 8.2: Order Email Notifications

- **Priority:** High
- **Estimated Time:** 1 week
- **Dependencies:** Task 8.1, Task 5.4
- **Subtasks:**
  - [ ] Create order confirmation email template (React Email)
  - [ ] Create order shipped email template (React Email)
  - [ ] Create order delivered email template (React Email)
  - [ ] Implement email sending on order creation (Server Action)
  - [ ] Implement email sending on order status updates
  - [ ] Add order details to emails (order number, items, total, etc.)
  - [ ] Style email templates (React Email styling)
  - [ ] Test all email templates in development
  - [ ] Test email delivery in production environment

#### Task 8.3: Account Email Notifications

- **Priority:** Medium
- **Estimated Time:** 2-3 days
- **Dependencies:** Task 8.1, Task 2.1
- **Subtasks:**
  - [ ] Create welcome email template (React Email)
  - [ ] Create password reset email template (React Email)
  - [ ] Create email verification email template (React Email)
  - [ ] Implement email sending on user registration
  - [ ] Implement email sending on password reset request
  - [ ] Implement email sending on email verification request
  - [ ] Style email templates
  - [ ] Test all account email templates

---

### Epic 9: UI/UX Design & Styling

#### Task 9.1: Design System & Branding

- **Priority:** High
- **Estimated Time:** 1 week
- **Dependencies:** None
- **Subtasks:**
  - [ ] Define brand colors (cozy tea theme) - update Tailwind config
  - [ ] Choose typography (fonts) - configure in Tailwind config
  - [ ] Create logo or placeholder logo
  - [ ] Initialize shadcn/ui component library
  - [ ] Configure shadcn/ui theme (colors, fonts)
  - [ ] Install initial shadcn/ui components (Button, Card, Input, etc.)
  - [ ] Customize shadcn/ui components to match brand
  - [ ] Create style guide/documentation
  - [ ] Set up Tailwind CSS configuration (tailwind.config.ts)
  - [ ] Configure CSS variables for theming

#### Task 9.2: Layout Components

- **Priority:** High
- **Estimated Time:** 1 week
- **Dependencies:** Task 9.1
- **Subtasks:**
  - [ ] Design and implement header/navigation
  - [ ] Design and implement footer
  - [ ] Create responsive navigation menu
  - [ ] Add mobile hamburger menu
  - [ ] Implement cart icon with item count
  - [ ] Add user account dropdown menu

#### Task 9.3: Common UI Components

- **Priority:** High
- **Estimated Time:** 1 week
- **Dependencies:** Task 9.1
- **Subtasks:**
  - [ ] Install shadcn/ui Button component
  - [ ] Install shadcn/ui Input component
  - [ ] Install shadcn/ui Form components (for React Hook Form)
  - [ ] Install shadcn/ui Loading spinner (Skeleton component)
  - [ ] Install shadcn/ui Dialog/Modal component
  - [ ] Install shadcn/ui Toast/Notification component (Sonner)
  - [ ] Install shadcn/ui Card component
  - [ ] Install shadcn/ui Badge component
  - [ ] Customize components to match brand theme
  - [ ] Create custom components if needed (quantity selector, etc.)
  - [ ] Document component usage

#### Task 9.4: Responsive Design

- **Priority:** Critical
- **Estimated Time:** Ongoing (throughout development)
- **Dependencies:** All UI tasks
- **Subtasks:**
  - [ ] Ensure mobile-first design approach
  - [ ] Test all pages on mobile devices
  - [ ] Test all pages on tablets
  - [ ] Test all pages on desktop
  - [ ] Fix responsive issues
  - [ ] Optimize touch interactions

---

### Epic 10: Testing & Quality Assurance

#### Task 10.1: Unit Testing

- **Priority:** High
- **Estimated Time:** 1.5 weeks
- **Dependencies:** All development tasks
- **Subtasks:**
  - [ ] Configure Vitest testing framework
  - [ ] Set up Vitest config file
  - [ ] Install React Testing Library
  - [ ] Write unit tests for utility functions (lib/utils)
  - [ ] Write unit tests for Server Actions
  - [ ] Write unit tests for API routes
  - [ ] Write unit tests for React components
  - [ ] Write unit tests for Zustand stores
  - [ ] Achieve minimum 70% code coverage
  - [ ] Set up test coverage reporting (Vitest coverage)
  - [ ] Add test scripts to package.json

#### Task 10.2: Integration Testing

- **Priority:** High
- **Estimated Time:** 1 week
- **Dependencies:** Task 10.1
- **Subtasks:**
  - [ ] Write integration tests for API routes (Next.js API routes)
  - [ ] Write integration tests for Server Actions
  - [ ] Test authentication flows (NextAuth.js)
  - [ ] Test database operations (Prisma queries)
  - [ ] Test checkout flow end-to-end
  - [ ] Test payment processing (Stripe test mode)
  - [ ] Test order creation and updates
  - [ ] Test cart synchronization (localStorage to database)
  - [ ] Mock external services (Stripe, Resend) in tests

#### Task 10.3: End-to-End Testing

- **Priority:** Medium
- **Estimated Time:** 1 week
- **Dependencies:** Task 10.2
- **Subtasks:**
  - [ ] Install and configure Playwright
  - [ ] Set up Playwright config file
  - [ ] Configure Playwright for Next.js
  - [ ] Write E2E tests for critical user flows
  - [ ] Test user registration and login flow
  - [ ] Test product browsing and filtering
  - [ ] Test add to cart functionality
  - [ ] Test checkout process (with Stripe test mode)
  - [ ] Test admin panel workflows
  - [ ] Set up Playwright CI configuration
  - [ ] Add E2E test scripts to package.json

#### Task 10.4: Security Testing

- **Priority:** Critical
- **Estimated Time:** 3-4 days
- **Dependencies:** All development tasks
- **Subtasks:**
  - [ ] Perform security audit
  - [ ] Test for SQL injection vulnerabilities
  - [ ] Test for XSS vulnerabilities
  - [ ] Test authentication and authorization
  - [ ] Test rate limiting
  - [ ] Review payment security (PCI compliance)
  - [ ] Fix identified security issues

#### Task 10.5: Performance Testing

- **Priority:** High
- **Estimated Time:** 3-4 days
- **Dependencies:** All development tasks
- **Subtasks:**
  - [ ] Test page load times (Lighthouse, Web Vitals)
  - [ ] Optimize images (Next.js Image component, compression)
  - [ ] Implement caching strategy (Next.js caching, React Query)
  - [ ] Optimize database queries (Prisma query optimization, indexes)
  - [ ] Add database query logging to identify slow queries
  - [ ] Test with load testing tools (k6, Artillery, or Vercel Analytics)
  - [ ] Fix performance bottlenecks
  - [ ] Optimize bundle size (analyze with @next/bundle-analyzer)
  - [ ] Enable Next.js production optimizations

---

### Epic 11: SEO & Accessibility

#### Task 11.1: SEO Implementation

- **Priority:** High
- **Estimated Time:** 1 week
- **Dependencies:** All page development
- **Subtasks:**
  - [ ] Add metadata to all pages (Next.js metadata API)
  - [ ] Implement Open Graph tags (Next.js metadata)
  - [ ] Add Twitter Card tags
  - [ ] Add structured data (Schema.org) - Product, Organization, BreadcrumbList
  - [ ] Create dynamic sitemap.xml (Next.js sitemap.ts)
  - [ ] Create robots.txt (Next.js robots.ts)
  - [ ] Optimize URL structure (slug-based routes)
  - [ ] Add alt text to all images (Next.js Image alt prop)
  - [ ] Configure Next.js App Router for optimal SEO (Server Components)
  - [ ] Add canonical URLs
  - [ ] Test SEO with Google Search Console (after deployment)

#### Task 11.2: Accessibility (WCAG)

- **Priority:** High
- **Estimated Time:** 1 week
- **Dependencies:** All UI development
- **Subtasks:**
  - [ ] Add ARIA labels where needed
  - [ ] Ensure keyboard navigation works
  - [ ] Test with screen readers
  - [ ] Ensure color contrast meets WCAG standards
  - [ ] Add focus indicators
  - [ ] Test accessibility with tools (axe, Lighthouse)

---

### Epic 12: Deployment & Launch

#### Task 12.1: Staging Environment Setup

- **Priority:** Critical
- **Estimated Time:** 2-3 days
- **Dependencies:** Task 1.5
- **Subtasks:**
  - [ ] Configure Vercel preview deployments (automatic on PR)
  - [ ] Set up staging Supabase project (or use separate database)
  - [ ] Configure staging environment variables in Vercel
  - [ ] Run Prisma migrations on staging database
  - [ ] Seed staging database with test data
  - [ ] Test staging deployment process
  - [ ] Verify all features work in staging environment

#### Task 12.2: Pre-Launch Testing

- **Priority:** Critical
- **Estimated Time:** 1 week
- **Dependencies:** Task 12.1, All testing tasks
- **Subtasks:**
  - [ ] Perform full regression testing on staging
  - [ ] Test all user flows
  - [ ] Test payment processing (test mode)
  - [ ] Test email notifications
  - [ ] Fix critical bugs
  - [ ] User acceptance testing (UAT)

#### Task 12.3: Production Deployment

- **Priority:** Critical
- **Estimated Time:** 2-3 days
- **Dependencies:** Task 12.2
- **Subtasks:**
  - [ ] Configure Vercel production deployment
  - [ ] Set up production Supabase database
  - [ ] Configure production environment variables in Vercel
  - [ ] Run Prisma migrations on production database
  - [ ] Seed production database with initial products
  - [ ] Deploy application to Vercel production
  - [ ] Configure production Stripe keys (live mode)
  - [ ] Set up Vercel Analytics
  - [ ] Configure error tracking (optional - Sentry)
  - [ ] Test production deployment
  - [ ] Verify all features work in production

#### Task 12.4: Launch Preparation

- **Priority:** Critical
- **Estimated Time:** 2-3 days
- **Dependencies:** Task 12.3
- **Subtasks:**
  - [ ] Create Terms of Service page
  - [ ] Create Privacy Policy page
  - [ ] Set up Google Analytics
  - [ ] Set up error tracking (Sentry, etc.)
  - [ ] Create launch checklist
  - [ ] Prepare launch announcement
  - [ ] Final production testing

#### Task 12.5: Soft Launch

- **Priority:** High
- **Estimated Time:** 1-2 weeks
- **Dependencies:** Task 12.4
- **Subtasks:**
  - [ ] Launch to beta users
  - [ ] Monitor application metrics
  - [ ] Monitor error logs
  - [ ] Gather user feedback
  - [ ] Fix critical issues
  - [ ] Iterate based on feedback

---

## Phase 2: Enhanced Features - 6-8 weeks

### Epic 13: Advanced Search & Discovery

#### Task 13.1: Enhanced Search

- **Priority:** Medium
- **Estimated Time:** 1 week
- **Dependencies:** Task 3.4
- **Subtasks:**
  - [ ] Implement advanced search filters
  - [ ] Add search result sorting
  - [ ] Improve search algorithm
  - [ ] Add search analytics

#### Task 13.2: Product Recommendations

- **Priority:** Medium
- **Estimated Time:** 1.5 weeks
- **Dependencies:** Task 3.5
- **Subtasks:**
  - [ ] Implement recommendation algorithm
  - [ ] Add "You may also like" section
  - [ ] Add recommendations based on browsing history
  - [ ] Add trending products section

#### Task 13.3: Recently Viewed Products

- **Priority:** Low
- **Estimated Time:** 2-3 days
- **Dependencies:** Task 3.5
- **Subtasks:**
  - [ ] Track recently viewed products
  - [ ] Display recently viewed section
  - [ ] Store in localStorage or backend

---

### Epic 14: Product Reviews & Ratings

#### Task 14.1: Review System Backend

- **Priority:** Medium
- **Estimated Time:** 1 week
- **Dependencies:** Task 3.1, Task 2.1
- **Subtasks:**
  - [ ] Create review database model
  - [ ] Implement create review endpoint
  - [ ] Implement get reviews endpoint
  - [ ] Implement update review endpoint
  - [ ] Implement delete review endpoint
  - [ ] Add review moderation flag

#### Task 14.2: Review System Frontend

- **Priority:** Medium
- **Estimated Time:** 1 week
- **Dependencies:** Task 14.1
- **Subtasks:**
  - [ ] Design review section on product page
  - [ ] Create review form component
  - [ ] Display reviews list
  - [ ] Add review rating (stars)
  - [ ] Add review sorting (newest, highest rated, etc.)
  - [ ] Add review pagination

#### Task 14.3: Review Moderation (Admin)

- **Priority:** Medium
- **Estimated Time:** 3-4 days
- **Dependencies:** Task 14.1, Task 7.1
- **Subtasks:**
  - [ ] Create review moderation page
  - [ ] Implement approve/reject review
  - [ ] Add review flagging functionality
  - [ ] Display review statistics

#### Task 14.4: Photo Reviews

- **Priority:** Low
- **Estimated Time:** 3-4 days
- **Dependencies:** Task 14.2
- **Subtasks:**
  - [ ] Add image upload to review form
  - [ ] Store review images
  - [ ] Display review images
  - [ ] Add image moderation

---

### Epic 15: Subscription System

#### Task 15.1: Subscription Backend

- **Priority:** Medium
- **Estimated Time:** 1.5 weeks
- **Dependencies:** Task 3.1, Task 2.1, Task 5.4
- **Subtasks:**
  - [ ] Create subscription database model
  - [ ] Implement create subscription endpoint
  - [ ] Implement subscription management endpoints
  - [ ] Add subscription scheduling logic
  - [ ] Implement subscription renewal process
  - [ ] Add subscription status tracking

#### Task 15.2: Subscription Frontend

- **Priority:** Medium
- **Estimated Time:** 1.5 weeks
- **Dependencies:** Task 15.1
- **Subtasks:**
  - [ ] Add subscription option to product pages
  - [ ] Design subscription selection UI
  - [ ] Create subscription management dashboard
  - [ ] Add frequency selection (weekly, monthly, etc.)
  - [ ] Add pause/resume subscription functionality
  - [ ] Add cancel subscription functionality
  - [ ] Display upcoming deliveries

#### Task 15.3: Subscription Admin

- **Priority:** Medium
- **Estimated Time:** 1 week
- **Dependencies:** Task 15.1, Task 7.1
- **Subtasks:**
  - [ ] Create subscription management page (admin)
  - [ ] View all subscriptions
  - [ ] Manage subscription status
  - [ ] View subscription analytics

---

### Epic 16: Gift Features

#### Task 16.1: Gift Message

- **Priority:** Medium
- **Estimated Time:** 2-3 days
- **Dependencies:** Task 5.2
- **Subtasks:**
  - [ ] Add gift message option to checkout
  - [ ] Create gift message input field
  - [ ] Store gift message with order
  - [ ] Display gift message in order details

#### Task 16.2: Gift Wrapping

- **Priority:** Medium
- **Estimated Time:** 2-3 days
- **Dependencies:** Task 5.2
- **Subtasks:**
  - [ ] Add gift wrapping option to checkout
  - [ ] Add gift wrapping fee calculation
  - [ ] Store gift wrapping preference with order
  - [ ] Display gift wrapping in order details

#### Task 16.3: Scheduled Delivery

- **Priority:** Medium
- **Estimated Time:** 1 week
- **Dependencies:** Task 5.2
- **Subtasks:**
  - [ ] Add delivery date selector to checkout
  - [ ] Validate delivery dates
  - [ ] Store scheduled delivery date
  - [ ] Display scheduled date in order details
  - [ ] Add admin notification for scheduled deliveries

#### Task 16.4: Gift Cards

- **Priority:** Low
- **Estimated Time:** 1.5 weeks
- **Dependencies:** Task 5.4
- **Subtasks:**
  - [ ] Create gift card product type
  - [ ] Implement gift card purchase flow
  - [ ] Generate unique gift card codes
  - [ ] Create gift card redemption system
  - [ ] Add gift card balance tracking
  - [ ] Create gift card management (admin)

#### Task 16.5: Gift Sets

- **Priority:** Low
- **Estimated Time:** 1 week
- **Dependencies:** Task 3.1
- **Subtasks:**
  - [ ] Create gift set product type
  - [ ] Design gift set product pages
  - [ ] Add gift set to catalog
  - [ ] Create gift set recommendations

---

### Epic 17: Marketing Features

#### Task 17.1: Promotional Banners

- **Priority:** Medium
- **Estimated Time:** 3-4 days
- **Dependencies:** Task 9.2
- **Subtasks:**
  - [ ] Create banner component
  - [ ] Design banner management (admin)
  - [ ] Implement banner display logic
  - [ ] Add banner scheduling

#### Task 17.2: Newsletter Signup

- **Priority:** Medium
- **Estimated Time:** 3-4 days
- **Dependencies:** Task 8.1
- **Subtasks:**
  - [ ] Create newsletter signup form
  - [ ] Implement newsletter subscription endpoint
  - [ ] Store newsletter subscribers
  - [ ] Create welcome email for newsletter
  - [ ] Add unsubscribe functionality

#### Task 17.3: Email Marketing Integration

- **Priority:** Low
- **Estimated Time:** 1 week
- **Dependencies:** Task 17.2
- **Subtasks:**
  - [ ] Integrate with email marketing platform (Mailchimp, etc.)
  - [ ] Set up automated email campaigns
  - [ ] Create abandoned cart emails
  - [ ] Create promotional emails

---

## Phase 3: Advanced Features - 8-12 weeks

### Epic 18: Loyalty Program

#### Task 18.1: Points System Backend

- **Priority:** Low
- **Estimated Time:** 1.5 weeks
- **Dependencies:** Task 5.4, Task 2.1
- **Subtasks:**
  - [ ] Create points/points history database model
  - [ ] Implement points earning logic
  - [ ] Implement points redemption logic
  - [ ] Add points expiration rules
  - [ ] Create points API endpoints

#### Task 18.2: Points System Frontend

- **Priority:** Low
- **Estimated Time:** 1 week
- **Dependencies:** Task 18.1
- **Subtasks:**
  - [ ] Display points balance to users
  - [ ] Show points earning opportunities
  - [ ] Create points redemption interface
  - [ ] Display points history
  - [ ] Add points to checkout flow

---

### Epic 19: Advanced Analytics

#### Task 19.1: Analytics Dashboard (Admin)

- **Priority:** Low
- **Estimated Time:** 1.5 weeks
- **Dependencies:** Task 7.1
- **Subtasks:**
  - [ ] Design analytics dashboard
  - [ ] Implement sales analytics
  - [ ] Implement customer analytics
  - [ ] Implement product analytics
  - [ ] Add charts and graphs
  - [ ] Add date range filtering
  - [ ] Export analytics data

---

### Epic 20: Additional Integrations

#### Task 20.1: Shipping Integration

- **Priority:** Medium
- **Estimated Time:** 1.5 weeks
- **Dependencies:** Task 5.2
- **Subtasks:**
  - [ ] Integrate with shipping API (USPS, FedEx, UPS)
  - [ ] Calculate real-time shipping rates
  - [ ] Generate shipping labels
  - [ ] Track shipments

#### Task 20.2: Customer Support Integration

- **Priority:** Low
- **Estimated Time:** 1 week
- **Dependencies:** None
- **Subtasks:**
  - [ ] Integrate live chat (Intercom, Zendesk)
  - [ ] Add support ticket system
  - [ ] Create FAQ page
  - [ ] Add contact form

---

## Task Import Guide for Monday.com

### How to Use This Document:

1. **Create Boards:** Create separate boards for Phase 1, Phase 2, and Phase 3
2. **Create Groups:** Use Epics as groups within each board
3. **Create Items:** Each task becomes an item in Monday.com
4. **Add Columns:**
   - Priority (Dropdown: Critical, High, Medium, Low)
   - Estimated Time (Text/Number)
   - Status (Status: Not Started, In Progress, Done)
   - Dependencies (Connect items)
   - Assignee (Person)
   - Subtasks (Checklist)
5. **Import Subtasks:** Add each subtask as a checklist item within the main task
6. **Set Dependencies:** Link tasks based on the dependencies listed
7. **Timeline View:** Use timeline view to visualize project schedule

### Recommended Monday.com Structure:

```
📊 Eerie Tea E-Commerce Project
├── 📋 Phase 1: MVP (8-12 weeks)
│   ├── 🎯 Epic 1: Project Setup & Infrastructure
│   ├── 🎯 Epic 2: Authentication & User Management
│   ├── 🎯 Epic 3: Product Catalog
│   ├── 🎯 Epic 4: Shopping Cart
│   ├── 🎯 Epic 5: Checkout Process
│   ├── 🎯 Epic 6: Order Management
│   ├── 🎯 Epic 7: Admin Panel
│   ├── 🎯 Epic 8: Email Notifications
│   ├── 🎯 Epic 9: UI/UX Design & Styling
│   ├── 🎯 Epic 10: Testing & Quality Assurance
│   ├── 🎯 Epic 11: SEO & Accessibility
│   └── 🎯 Epic 12: Deployment & Launch
├── 📋 Phase 2: Enhanced Features (6-8 weeks)
│   ├── 🎯 Epic 13: Advanced Search & Discovery
│   ├── 🎯 Epic 14: Product Reviews & Ratings
│   ├── 🎯 Epic 15: Subscription System
│   ├── 🎯 Epic 16: Gift Features
│   └── 🎯 Epic 17: Marketing Features
└── 📋 Phase 3: Advanced Features (8-12 weeks)
    ├── 🎯 Epic 18: Loyalty Program
    ├── 🎯 Epic 19: Advanced Analytics
    └── 🎯 Epic 20: Additional Integrations
```

### Tips for Project Management:

1. **Start with Phase 1:** Focus on MVP first, don't start Phase 2 until Phase 1 is complete
2. **Track Dependencies:** Use Monday.com's dependency feature to ensure tasks are done in order
3. **Update Regularly:** Update task status daily/weekly
4. **Break Down Large Tasks:** If a task seems too large, break it into smaller subtasks
5. **Use Labels/Tags:** Tag tasks by feature area (Frontend, Backend, Database, etc.)
6. **Set Milestones:** Mark completion of each Epic as a milestone
7. **Track Time:** Log actual time spent vs. estimated time to improve future estimates

---

## Summary Statistics

- **Total Epics:** 20
- **Total Tasks:** ~120+ main tasks
- **Total Subtasks:** ~400+ subtasks
- **Phase 1 Duration:** 8-12 weeks
- **Phase 2 Duration:** 6-8 weeks
- **Phase 3 Duration:** 8-12 weeks
- **Total Project Duration:** 22-32 weeks (5.5-8 months)

---

**Last Updated:** 2026-01-XX
**Document Version:** 2.0 (Updated with finalized technology stack)
