# Eerie Tea E-Commerce Project Task Breakdown

This document provides a comprehensive task breakdown organized for project management systems like Monday.com. Tasks are organized by phases with dependencies, priorities, and estimated effort.

**Technology Stack:** Next.js 16.1.1 (Frontend), .NET 10.0 + ASP.NET Core (Backend), TypeScript, C#, Entity Framework Core, Zustand, Tailwind CSS, shadcn/ui, ASP.NET Core Identity, Stripe, Resend, Vercel, Azure App Service, SQL Server (Local/Azure SQL Database)  
**See `TECH_STACK.md` for detailed technology information.**

---

## Phase 1: MVP (Minimum Viable Product) - 8-12 weeks

### Epic 1: Project Setup & Infrastructure

#### Task 1.1: Technical Architecture & Planning

- **Priority:** Critical
- **Estimated Time:** 1 week
- **Dependencies:** None
- **Subtasks:**
  - [x] Finalize technology stack decisions (.NET 10.0 backend, Next.js 16.1.1 frontend, Entity Framework Core, etc.)
  - [x] Create technical architecture diagram (frontend/backend separation)
  - [x] Set up version control repository (Git)
  - [x] Create project folder structure (separate frontend and backend folders)
  - [x] Set up development environment documentation
  - [x] Define coding standards and conventions (C# for backend, TypeScript for frontend)
  - [x] Set up code review process

#### Task 1.2: Development Environment Setup

- **Priority:** Critical
- **Estimated Time:** 1 week
- **Dependencies:** Task 1.1
- **Subtasks:**
  - [x] Install .NET SDK 10.0+ and verify version
  - [x] Install Node.js 20.9+ and verify version
  - [ ] Create .NET solution and projects (API, Core, Infrastructure, Tests)
  - [ ] Create Next.js 16.1.1 frontend project with TypeScript and App Router
  - [ ] Set up pnpm package manager for frontend
  - [ ] Configure C# project structure (layered architecture)
  - [ ] Configure TypeScript (tsconfig.json) - verify strict mode
  - [ ] Install and configure Entity Framework Core
  - [ ] Install SQL Server provider for EF Core (Microsoft.EntityFrameworkCore.SqlServer)
  - [ ] Set up local SQL Server database (SQL Server Express or LocalDB)
  - [ ] Configure SQL Server connection string in appsettings.json
  - [ ] Configure environment variables (appsettings.json for backend, .env.local for frontend)
  - [ ] Install and configure ESLint (Next.js config) for frontend
  - [ ] Install and configure Biome (or Prettier) for frontend formatting
  - [ ] Set up xUnit testing framework for backend
  - [ ] Set up Vitest testing framework for frontend
  - [ ] Set up Playwright for E2E testing
  - [ ] Initialize shadcn/ui component library (`npx shadcn@latest init`)
  - [ ] Configure Next.js Image domains (if using external images)
  - [ ] Set up Git repository and .gitignore (for both projects)
  - [ ] Configure Next.js app structure (app directory, layout, etc.)
  - [ ] Set up CORS configuration in .NET API for frontend access

#### Task 1.3: Database Schema Design & Setup

- **Priority:** Critical
- **Estimated Time:** 1 week
- **Dependencies:** Task 1.2
- **Subtasks:**
  - [ ] Design database schema (users, products, orders, cart, addresses, etc.)
  - [ ] Create Entity Framework Core DbContext
  - [ ] Configure DbContext to use SQL Server provider
  - [ ] Define all entity models (User, Product, Order, OrderItem, Cart, Address, etc.)
  - [ ] Set up Entity Framework relationships and foreign keys
  - [ ] Configure entity properties and constraints
  - [ ] Create initial EF Core migration
  - [ ] Run EF Core migrations to create database tables in local SQL Server
  - [ ] Set up database indexes using EF Core Fluent API
  - [ ] Create database seed data class for initial 30 tea products
  - [ ] Run seed data to populate local database
  - [ ] Verify database schema in SQL Server Management Studio (SSMS) or Azure Data Studio
  - [ ] Set up Swagger/OpenAPI for API documentation
  - [ ] Document database schema and relationships

#### Task 1.4: CI/CD Pipeline Setup

- **Priority:** High
- **Estimated Time:** 3-4 days
- **Dependencies:** Task 1.2
- **Subtasks:**
  - [ ] Set up GitHub Actions workflow
  - [ ] Configure automated testing for backend (xUnit tests)
  - [ ] Configure automated testing for frontend (Vitest unit tests)
  - [ ] Configure E2E testing in CI (Playwright)
  - [ ] Set up automated deployment to Vercel preview for frontend (on PR)
  - [ ] Set up automated deployment to Azure App Service for backend (on PR)
  - [ ] Configure Vercel project settings
  - [ ] Configure Azure App Service settings
  - [ ] Set up environment variables in Vercel dashboard (frontend)
  - [ ] Set up environment variables in Azure App Service (backend)
  - [ ] Configure build and deployment scripts for both projects
  - [ ] Test CI/CD pipeline with a test commit

#### Task 1.5: Hosting & Infrastructure Setup

- **Priority:** High
- **Estimated Time:** 3-4 days
- **Dependencies:** Task 1.2
- **Subtasks:**
  - [ ] Create Vercel account and connect GitHub repository (frontend)
  - [ ] Create Azure account and set up App Service (backend)
  - [ ] Set up Azure SQL Database for production
  - [ ] Create Azure SQL Database server and database
  - [ ] Configure firewall rules for Azure SQL Database
  - [ ] Get Azure SQL Database connection string
  - [ ] Configure database connection in Entity Framework Core (appsettings.json for local, Azure App Service settings for production)
  - [ ] Configure environment variables in Vercel (API_URL, etc.)
  - [ ] Configure environment variables in Azure App Service (ConnectionStrings:DefaultConnection, etc.)
  - [ ] Configure CORS in .NET API to allow Vercel frontend
  - [ ] Set up custom domain name (optional for MVP)
  - [ ] Configure DNS settings (if using custom domain)
  - [ ] Verify SSL certificates (automatic with Vercel and Azure)
  - [ ] Test database connection from Azure App Service to Azure SQL Database
  - [ ] Test API connection from frontend
  - [ ] Set up Vercel preview deployments for staging (frontend)
  - [ ] Set up Azure staging environment (backend)
  - [ ] Set up Azure SQL Database for staging (separate database or same server)

---

### Epic 2: Authentication & User Management

#### Task 2.1: User Registration & Login

- **Priority:** Critical
- **Estimated Time:** 1 week
- **Dependencies:** Task 1.3
- **Subtasks:**
  - [ ] Install and configure ASP.NET Core Identity
  - [ ] Set up Identity DbContext
  - [ ] Configure JWT Bearer Authentication in .NET API
  - [ ] Create User registration API endpoint (POST /api/auth/register)
  - [ ] Create User login API endpoint (POST /api/auth/login)
  - [ ] Implement password hashing (built into ASP.NET Core Identity)
  - [ ] Add email uniqueness validation (backend)
  - [ ] Design user registration form UI (using shadcn/ui components)
  - [ ] Implement registration form with React Hook Form + Zod validation
  - [ ] Create API client function for registration (frontend)
  - [ ] Design login form UI (using shadcn/ui components)
  - [ ] Implement login form with React Hook Form + Zod validation
  - [ ] Create API client function for login (frontend)
  - [ ] Implement JWT token storage (localStorage or httpOnly cookies)
  - [ ] Add form validation (Zod schemas for frontend, Data Annotations for backend)
  - [ ] Handle authentication errors gracefully (both frontend and backend)
  - [ ] Create protected route middleware (frontend)
  - [ ] Add [Authorize] attributes to protected API endpoints

#### Task 2.2: Password Reset Functionality

- **Priority:** High
- **Estimated Time:** 3-4 days
- **Dependencies:** Task 2.1, Task 8.1
- **Subtasks:**
  - [ ] Design "Forgot Password" UI (using shadcn/ui components)
  - [ ] Create password reset request API endpoint (POST /api/auth/forgot-password)
  - [ ] Set up Resend email service account
  - [ ] Install Resend .NET SDK
  - [ ] Create password reset email template (Razor email template)
  - [ ] Use ASP.NET Core Identity password reset token generation
  - [ ] Implement token expiration logic (24-hour expiry - built into Identity)
  - [ ] Design password reset form UI
  - [ ] Create password reset completion API endpoint (POST /api/auth/reset-password)
  - [ ] Add token validation and expiration handling (backend)
  - [ ] Create API client function for password reset (frontend)
  - [ ] Test email delivery in development

#### Task 2.3: User Profile Management

- **Priority:** High
- **Estimated Time:** 1 week
- **Dependencies:** Task 2.1
- **Subtasks:**
  - [ ] Design user profile page UI (using shadcn/ui components)
  - [ ] Create profile page route (Next.js App Router)
  - [ ] Create get user profile API endpoint (GET /api/users/me)
  - [ ] Create update user profile API endpoint (PUT /api/users/me)
  - [ ] Implement profile view (fetch from API - client component)
  - [ ] Implement profile update form with React Hook Form + Zod
  - [ ] Create API client functions for profile operations
  - [ ] Add email verification functionality (using Resend)
  - [ ] Create email verification API endpoint (POST /api/auth/verify-email)
  - [ ] Implement password change functionality
  - [ ] Create password change API endpoint (POST /api/auth/change-password)
  - [ ] Add password change form with validation
  - [ ] Add profile picture upload (optional - API endpoint for file upload)
  - [ ] Create account settings page
  - [ ] Add protected route middleware for profile pages (frontend)
  - [ ] Add [Authorize] attribute to profile endpoints (backend)

#### Task 2.4: Address Management

- **Priority:** High
- **Estimated Time:** 3-4 days
- **Dependencies:** Task 2.1
- **Subtasks:**
  - [ ] Design address management UI (using shadcn/ui components)
  - [ ] Create Address entity model in EF Core
  - [ ] Create EF Core migration for Address model
  - [ ] Create address management API endpoints (GET, POST, PUT, DELETE /api/addresses)
  - [ ] Create address management page route (frontend)
  - [ ] Implement add address API endpoint
  - [ ] Implement update address API endpoint
  - [ ] Implement delete address API endpoint
  - [ ] Implement set default address API endpoint
  - [ ] Create API client functions for address operations
  - [ ] Add address form with React Hook Form + Zod validation
  - [ ] Add address validation (required fields, US address format - both frontend and backend)
  - [ ] Display saved addresses list (fetch from API)

---

### Epic 2.5: API Client Setup (Frontend)

#### Task 2.5: API Client Configuration

- **Priority:** High
- **Estimated Time:** 2-3 days
- **Dependencies:** Task 1.2
- **Subtasks:**
  - [ ] Set up API client library (Axios or Fetch API wrapper)
  - [ ] Configure base API URL from environment variables
  - [ ] Create API client instance with interceptors
  - [ ] Add request interceptor for authentication tokens
  - [ ] Add response interceptor for error handling
  - [ ] Create API client types/interfaces (TypeScript)
  - [ ] Set up API response types matching backend DTOs
  - [ ] Create API client utility functions
  - [ ] Add retry logic for failed requests
  - [ ] Handle CORS errors gracefully
  - [ ] Test API client connectivity

---

### Epic 3: Product Catalog

#### Task 3.1: Product Database & Models

- **Priority:** Critical
- **Estimated Time:** 3-4 days
- **Dependencies:** Task 1.3
- **Subtasks:**
  - [ ] Create Product entity model in EF Core
  - [ ] Add product fields (name, description, price, images, origin, caffeine level, flavor notes, etc.)
  - [ ] Create Category entity model in EF Core
  - [ ] Create ProductImage entity model for multiple images
  - [ ] Set up EF Core relationships (Product-Category, Product-ProductImage)
  - [ ] Add inventory quantity field to Product entity
  - [ ] Create EF Core migration for Product models
  - [ ] Update database seed data class with 30 tea products
  - [ ] Add product seed data (names, descriptions, prices, images, categories)
  - [ ] Run seed data to populate products
  - [ ] Verify product data in database

#### Task 3.2: Product Listing Page

- **Priority:** Critical
- **Estimated Time:** 1 week
- **Dependencies:** Task 3.1, Task 2.5
- **Subtasks:**
  - [ ] Design product listing page layout (using Tailwind CSS)
  - [ ] Create products page route (Next.js App Router)
  - [ ] Create get products API endpoint (GET /api/products with pagination)
  - [ ] Implement client component to fetch products from API
  - [ ] Add pagination logic (API supports pagination)
  - [ ] Create product card component (using shadcn/ui Card)
  - [ ] Implement product grid layout (CSS Grid/Tailwind)
  - [ ] Add product grid/list view toggle (client component)
  - [ ] Implement pagination component (using shadcn/ui)
  - [ ] Add loading states (React loading states)
  - [ ] Add empty state handling
  - [ ] Optimize product images (Next.js Image component with lazy loading)
  - [ ] Make responsive for mobile devices (Tailwind responsive classes)
  - [ ] Add search params handling for filters (URL state)
  - [ ] Create API client function for products

#### Task 3.3: Product Filtering & Sorting

- **Priority:** High
- **Estimated Time:** 1 week
- **Dependencies:** Task 3.2
- **Subtasks:**
  - [ ] Design filter sidebar/panel UI (using shadcn/ui components)
  - [ ] Update products API endpoint to support filtering query parameters
  - [ ] Implement filter by category (EF Core query - backend)
  - [ ] Implement filter by price range (EF Core query - backend)
  - [ ] Implement filter by origin (EF Core query - backend)
  - [ ] Implement filter by caffeine level (EF Core query - backend)
  - [ ] Implement filter by flavor notes (EF Core query - backend)
  - [ ] Implement sort by price (low to high, high to low) - EF Core OrderBy
  - [ ] Implement sort by popularity (EF Core OrderBy)
  - [ ] Implement sort by newest (EF Core OrderBy CreatedAt)
  - [ ] Add filter reset functionality (frontend)
  - [ ] Update URL search params for filters (Next.js useSearchParams)
  - [ ] Combine multiple filters (EF Core where clauses - backend)
  - [ ] Update API client to pass filter parameters

#### Task 3.4: Product Search

- **Priority:** High
- **Estimated Time:** 3-4 days
- **Dependencies:** Task 3.2
- **Subtasks:**
  - [ ] Design search bar UI (header component)
  - [ ] Create search API endpoint (GET /api/products/search)
  - [ ] Implement search with EF Core (Contains/full-text search)
  - [ ] Add search by product name (EF Core Where Contains)
  - [ ] Add search by ingredients/description (EF Core Where Contains)
  - [ ] Create search suggestions API endpoint (GET /api/products/search/suggestions)
  - [ ] Implement search suggestions/autocomplete (debounced API call)
  - [ ] Create search results page route (frontend)
  - [ ] Handle empty search results
  - [ ] Add search history (for logged-in users - store in database)
  - [ ] Create search history API endpoints
  - [ ] Add search debouncing (client-side)
  - [ ] Create API client functions for search

#### Task 3.5: Product Detail Page

- **Priority:** Critical
- **Estimated Time:** 1.5 weeks
- **Dependencies:** Task 3.1, Task 2.5
- **Subtasks:**
  - [ ] Design product detail page layout (using Tailwind CSS)
  - [ ] Create dynamic product page route [slug] (Next.js App Router)
  - [ ] Create get product by slug API endpoint (GET /api/products/{slug})
  - [ ] Implement client component to fetch product from API
  - [ ] Create product image gallery component (using Next.js Image)
  - [ ] Display product name, price, description
  - [ ] Add tasting notes section
  - [ ] Add origin information section
  - [ ] Add brewing instructions section
  - [ ] Create quantity selector component (using shadcn/ui)
  - [ ] Add "Add to Cart" button (client component)
  - [ ] Display stock availability indicator
  - [ ] Create get related products API endpoint (GET /api/products/{id}/related)
  - [ ] Add related/recommended products section (fetch from API)
  - [ ] Make responsive for mobile devices
  - [ ] Add SEO meta tags (Next.js metadata API)
  - [ ] Create API client function for product detail

---

### Epic 4: Shopping Cart

#### Task 4.1: Cart State Management

- **Priority:** Critical
- **Estimated Time:** 3-4 days
- **Dependencies:** Task 3.5, Task 2.5
- **Subtasks:**
  - [ ] Install and set up Zustand for cart state management
  - [ ] Create cart store with Zustand (add, remove, update quantity)
  - [ ] Implement add to cart functionality (client-side)
  - [ ] Implement remove from cart functionality
  - [ ] Implement update cart item quantity
  - [ ] Persist cart to localStorage (guest users) using Zustand persist middleware
  - [ ] Create Cart entity model in EF Core (for logged-in users)
  - [ ] Create cart API endpoints (GET, POST, PUT, DELETE /api/cart)
  - [ ] Create add to cart API endpoint (POST /api/cart/items)
  - [ ] Create remove from cart API endpoint (DELETE /api/cart/items/{id})
  - [ ] Create update cart item API endpoint (PUT /api/cart/items/{id})
  - [ ] Sync cart with backend for logged-in users
  - [ ] Handle cart merge on login (merge localStorage cart with database cart)
  - [ ] Add cart item count to header (Zustand subscription)
  - [ ] Create API client functions for cart operations

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
- **Dependencies:** Task 5.1, Task 2.4, Task 2.5
- **Subtasks:**
  - [ ] Create shipping address form component (React Hook Form + Zod)
  - [ ] Add form validation (Zod schema - required fields, email format, US address format)
  - [ ] Implement guest checkout option (no account required)
  - [ ] Create account creation API endpoint for checkout (POST /api/auth/register)
  - [ ] Add saved addresses dropdown for logged-in users (fetch from API)
  - [ ] Create get user addresses API endpoint (GET /api/addresses)
  - [ ] Implement shipping method selection (Standard, Express, etc.)
  - [ ] Create shipping cost calculation API endpoint (POST /api/shipping/calculate)
  - [ ] Calculate and display shipping costs (fixed rates for MVP - backend)
  - [ ] Display estimated delivery dates (calculate based on shipping method)
  - [ ] Add address autocomplete (optional - Google Places API)
  - [ ] Store shipping info in checkout state (Zustand or form state)
  - [ ] Create API client functions for shipping

#### Task 5.3: Payment Integration

- **Priority:** Critical
- **Estimated Time:** 1.5 weeks
- **Dependencies:** Task 5.2, Task 2.5
- **Subtasks:**
  - [ ] Set up Stripe account and get API keys
  - [ ] Install Stripe.net package for backend (.NET)
  - [ ] Install Stripe packages for frontend (@stripe/stripe-js, @stripe/react-stripe-js)
  - [ ] Configure Stripe environment variables (backend appsettings.json)
  - [ ] Create Stripe payment intent API endpoint (POST /api/payments/create-intent)
  - [ ] Integrate Stripe Elements payment form (client component)
  - [ ] Implement credit card processing with Stripe
  - [ ] Add payment form validation (Stripe + Zod)
  - [ ] Create confirm payment API endpoint (POST /api/payments/confirm)
  - [ ] Handle payment errors gracefully (both frontend and backend)
  - [ ] Ensure PCI compliance (handled by Stripe)
  - [ ] Test payment processing in Stripe test mode
  - [ ] Add payment success/failure handling
  - [ ] Create webhook endpoint for Stripe events (POST /api/webhooks/stripe)
  - [ ] Create API client functions for payment operations

#### Task 5.4: Order Processing

- **Priority:** Critical
- **Estimated Time:** 1 week
- **Dependencies:** Task 5.3, Task 2.5
- **Subtasks:**
  - [ ] Create Order and OrderItem entity models in EF Core
  - [ ] Create EF Core migration for Order models
  - [ ] Create order creation API endpoint (POST /api/orders)
  - [ ] Link order to user (if logged in) via EF Core relation
  - [ ] Store order items with EF Core
  - [ ] Store shipping and payment information
  - [ ] Generate unique order number (format: ORDER-YYYYMMDD-XXXX)
  - [ ] Update inventory after order (EF Core transaction)
  - [ ] Handle out-of-stock items (check before order creation)
  - [ ] Create order confirmation page route (frontend)
  - [ ] Implement order confirmation email (using Resend + Razor templates)
  - [ ] Add order status tracking
  - [ ] Create API client function for order creation

#### Task 5.5: Discount Codes & Promotions

- **Priority:** Medium
- **Estimated Time:** 3-4 days
- **Dependencies:** Task 5.4
- **Subtasks:**
  - [ ] Create discount code entity model in EF Core
  - [ ] Create EF Core migration for discount codes
  - [ ] Design discount code input field (frontend)
  - [ ] Create discount code validation API endpoint (POST /api/discounts/validate)
  - [ ] Apply discount to order total (backend calculation)
  - [ ] Display discount in order summary (frontend)
  - [ ] Handle invalid/expired discount codes (backend validation)
  - [ ] Create API client function for discount validation

---

### Epic 6: Order Management

#### Task 6.1: Order History (User)

- **Priority:** High
- **Estimated Time:** 1 week
- **Dependencies:** Task 5.4, Task 2.1, Task 2.5
- **Subtasks:**
  - [ ] Design order history page (protected route)
  - [ ] Create order history page route (frontend)
  - [ ] Create get user orders API endpoint (GET /api/orders/me)
  - [ ] Fetch user orders from API (filter by userId - backend)
  - [ ] Display list of past orders
  - [ ] Show order details (items, total, date, status)
  - [ ] Add order filtering (by date, status) - EF Core queries (backend)
  - [ ] Add order search functionality (by order number)
  - [ ] Add pagination for order list (API supports pagination)
  - [ ] Make responsive for mobile devices
  - [ ] Add loading states
  - [ ] Create API client function for order history

#### Task 6.2: Order Tracking

- **Priority:** High
- **Estimated Time:** 3-4 days
- **Dependencies:** Task 6.1, Task 2.5
- **Subtasks:**
  - [ ] Design order tracking page (dynamic route [orderId])
  - [ ] Create order tracking page route (frontend)
  - [ ] Create get order by ID API endpoint (GET /api/orders/{id})
  - [ ] Fetch order details from API
  - [ ] Display order status (pending, processing, shipped, delivered)
  - [ ] Create OrderStatusHistory entity model if needed
  - [ ] Show order timeline/status updates (fetch from API)
  - [ ] Display tracking number (if available)
  - [ ] Add order details view (reuse from order history)
  - [ ] Implement order status update notifications (email via Resend)
  - [ ] Add protected route (verify user owns order - backend authorization)
  - [ ] Create API client function for order tracking

---

### Epic 7: Admin Panel

#### Task 7.1: Admin Authentication & Authorization

- **Priority:** Critical
- **Estimated Time:** 3-4 days
- **Dependencies:** Task 2.1
- **Subtasks:**
  - [ ] Configure ASP.NET Core Identity roles (admin, user)
  - [ ] Create EF Core migration for Identity roles
  - [ ] Create admin user seed data
  - [ ] Implement admin login (use same auth endpoints with role check)
  - [ ] Add role-based authorization attributes ([Authorize(Roles = "Admin")])
  - [ ] Create admin authorization policy in .NET API
  - [ ] Protect admin API endpoints with role checks
  - [ ] Create admin dashboard layout component (frontend)
  - [ ] Add admin navigation/sidebar (frontend)
  - [ ] Create admin route group (/admin) (frontend)
  - [ ] Add frontend role check for admin routes

#### Task 7.2: Product Management (Admin)

- **Priority:** Critical
- **Estimated Time:** 1.5 weeks
- **Dependencies:** Task 7.1, Task 3.1, Task 2.5
- **Subtasks:**
  - [ ] Design product management page (admin layout)
  - [ ] Create get products API endpoint for admin (GET /api/admin/products)
  - [ ] Implement product list view (admin) - fetch from API
  - [ ] Create add product form (React Hook Form + Zod)
  - [ ] Create create product API endpoint (POST /api/admin/products)
  - [ ] Create edit product form (pre-populated)
  - [ ] Create update product API endpoint (PUT /api/admin/products/{id})
  - [ ] Create delete product API endpoint (DELETE /api/admin/products/{id})
  - [ ] Add product image upload functionality (API endpoint for file upload)
  - [ ] Store images (cloud storage like Azure Blob Storage or Cloudinary)
  - [ ] Add bulk product operations (bulk delete, bulk update API endpoints)
  - [ ] Add product search/filter for admin (EF Core queries - backend)
  - [ ] Add pagination for admin product list (API supports pagination)
  - [ ] Create API client functions for admin product operations

#### Task 7.3: Order Management (Admin)

- **Priority:** Critical
- **Estimated Time:** 1 week
- **Dependencies:** Task 7.1, Task 5.4, Task 2.5
- **Subtasks:**
  - [ ] Design order management page (admin layout)
  - [ ] Create get orders API endpoint for admin (GET /api/admin/orders)
  - [ ] Implement order list view (admin) - fetch from API
  - [ ] Add order filtering (by status, date, customer) - EF Core where clauses (backend)
  - [ ] Create order detail view (fetch from API)
  - [ ] Create update order status API endpoint (PUT /api/admin/orders/{id}/status)
  - [ ] Create OrderNote entity model if needed
  - [ ] Add order notes/comments API endpoints
  - [ ] Export orders to CSV (optional - API endpoint)
  - [ ] Add order search functionality (EF Core search - backend)
  - [ ] Add pagination for order list (API supports pagination)
  - [ ] Display order totals and statistics (calculate in backend or frontend)
  - [ ] Create API client functions for admin order operations

#### Task 7.4: Inventory Management (Admin)

- **Priority:** High
- **Estimated Time:** 1 week
- **Dependencies:** Task 7.2, Task 2.5
- **Subtasks:**
  - [ ] Design inventory management page (admin layout)
  - [ ] Create get inventory API endpoint (GET /api/admin/inventory)
  - [ ] Display product inventory levels (fetch from API)
  - [ ] Create update inventory API endpoint (PUT /api/admin/inventory/{id})
  - [ ] Add low stock alerts/warnings (calculate threshold - backend or frontend)
  - [ ] Create InventoryHistory entity model if needed
  - [ ] Add inventory history tracking API endpoints
  - [ ] Create bulk inventory update API endpoint (POST /api/admin/inventory/bulk)
  - [ ] Add inventory filtering and search (EF Core queries - backend)
  - [ ] Display inventory statistics (calculate in backend or frontend)
  - [ ] Create API client functions for inventory management

#### Task 7.5: Customer Management (Admin)

- **Priority:** Medium
- **Estimated Time:** 3-4 days
- **Dependencies:** Task 7.1, Task 2.5
- **Subtasks:**
  - [ ] Design customer management page
  - [ ] Create get customers API endpoint (GET /api/admin/customers)
  - [ ] Implement customer list view (fetch from API)
  - [ ] Add customer search functionality (EF Core search - backend)
  - [ ] Create get customer details API endpoint (GET /api/admin/customers/{id})
  - [ ] Display customer details
  - [ ] Create get customer orders API endpoint (GET /api/admin/customers/{id}/orders)
  - [ ] View customer order history
  - [ ] Create customer notes API endpoints
  - [ ] Add customer notes
  - [ ] Create API client functions for customer management

---

### Epic 8: Email Notifications

#### Task 8.1: Email Service Setup

- **Priority:** High
- **Estimated Time:** 2-3 days
- **Dependencies:** Task 1.2
- **Subtasks:**
  - [ ] Set up Resend account and get API key
  - [ ] Install Resend .NET SDK
  - [ ] Configure Resend environment variables (appsettings.json)
  - [ ] Create email service class in .NET (IEmailService interface)
  - [ ] Implement email sending service (ResendEmailService)
  - [ ] Create email template structure (Razor views or HTML templates)
  - [ ] Configure dependency injection for email service
  - [ ] Test email delivery in development
  - [ ] Set up email domain verification (if using custom domain)

#### Task 8.2: Order Email Notifications

- **Priority:** High
- **Estimated Time:** 1 week
- **Dependencies:** Task 8.1, Task 5.4
- **Subtasks:**
  - [ ] Create order confirmation email template (Razor email template)
  - [ ] Create order shipped email template (Razor email template)
  - [ ] Create order delivered email template (Razor email template)
  - [ ] Implement email sending on order creation (in order creation endpoint)
  - [ ] Implement email sending on order status updates (in status update endpoint)
  - [ ] Add order details to emails (order number, items, total, etc.)
  - [ ] Style email templates (HTML/CSS in Razor templates)
  - [ ] Test all email templates in development
  - [ ] Test email delivery in production environment

#### Task 8.3: Account Email Notifications

- **Priority:** Medium
- **Estimated Time:** 2-3 days
- **Dependencies:** Task 8.1, Task 2.1
- **Subtasks:**
  - [ ] Create welcome email template (Razor email template)
  - [ ] Create password reset email template (Razor email template)
  - [ ] Create email verification email template (Razor email template)
  - [ ] Implement email sending on user registration (in registration endpoint)
  - [ ] Implement email sending on password reset request (in password reset endpoint)
  - [ ] Implement email sending on email verification request (in verification endpoint)
  - [ ] Style email templates (HTML/CSS)
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
  - [ ] Configure xUnit testing framework for backend
  - [ ] Configure Vitest testing framework for frontend
  - [ ] Set up xUnit config file
  - [ ] Set up Vitest config file
  - [ ] Install React Testing Library
  - [ ] Write unit tests for backend services (business logic)
  - [ ] Write unit tests for backend controllers (API endpoints)
  - [ ] Write unit tests for utility functions (lib/utils - frontend)
  - [ ] Write unit tests for API client functions (frontend)
  - [ ] Write unit tests for React components
  - [ ] Write unit tests for Zustand stores
  - [ ] Achieve minimum 70% code coverage (both projects)
  - [ ] Set up test coverage reporting (xUnit for backend, Vitest for frontend)
  - [ ] Add test scripts to package.json (frontend) and .csproj (backend)

#### Task 10.2: Integration Testing

- **Priority:** High
- **Estimated Time:** 1 week
- **Dependencies:** Task 10.1
- **Subtasks:**
  - [ ] Write integration tests for .NET API endpoints (using TestServer)
  - [ ] Test authentication flows (ASP.NET Core Identity)
  - [ ] Test database operations (EF Core queries with in-memory database or test SQL Server database)
  - [ ] Set up test SQL Server database (LocalDB or separate test database)
  - [ ] Test checkout flow end-to-end (API integration)
  - [ ] Test payment processing (Stripe test mode)
  - [ ] Test order creation and updates
  - [ ] Test cart synchronization (localStorage to database via API)
  - [ ] Mock external services (Stripe, Resend) in backend tests
  - [ ] Test API client functions (frontend integration tests)
  - [ ] Test CORS configuration

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
  - [ ] Implement caching strategy (React Query for frontend, response caching for backend)
  - [ ] Optimize database queries (EF Core query optimization, indexes)
  - [ ] Add database query logging to identify slow queries (EF Core logging)
  - [ ] Test API response times
  - [ ] Test with load testing tools (k6, Artillery, or Vercel Analytics)
  - [ ] Fix performance bottlenecks
  - [ ] Optimize bundle size (analyze with @next/bundle-analyzer)
  - [ ] Enable Next.js production optimizations
  - [ ] Optimize .NET API performance (response compression, async operations)

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
  - [ ] Configure Next.js App Router for optimal SEO (use Server Components for static content, client components for dynamic API calls)
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
  - [ ] Configure Vercel preview deployments for frontend (automatic on PR)
  - [ ] Set up Azure staging App Service for backend
  - [ ] Set up Azure SQL Database for staging (separate database or same server with different database name)
  - [ ] Configure staging database connection string in Azure App Service
  - [ ] Configure staging environment variables in Vercel (frontend)
  - [ ] Configure staging environment variables in Azure App Service (backend)
  - [ ] Run EF Core migrations on staging SQL Server database
  - [ ] Seed staging database with test data
  - [ ] Test staging deployment process (both frontend and backend)
  - [ ] Verify all features work in staging environment
  - [ ] Test API connectivity from staging frontend to staging backend
  - [ ] Test database connectivity from staging backend to staging SQL Server database

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
  - [ ] Configure Vercel production deployment (frontend)
  - [ ] Configure Azure App Service production deployment (backend)
  - [ ] Set up Azure SQL Database for production (if not already created)
  - [ ] Configure production database connection string in Azure App Service
  - [ ] Configure Azure SQL Database firewall rules for production access
  - [ ] Configure production environment variables in Vercel (frontend)
  - [ ] Configure production environment variables in Azure App Service (backend)
  - [ ] Run EF Core migrations on production SQL Server database
  - [ ] Seed production database with initial products
  - [ ] Deploy frontend application to Vercel production
  - [ ] Deploy backend application to Azure App Service production
  - [ ] Configure production Stripe keys (live mode)
  - [ ] Set up Vercel Analytics
  - [ ] Configure error tracking (optional - Sentry for both frontend and backend)
  - [ ] Test production deployment
  - [ ] Verify all features work in production
  - [ ] Test API connectivity from production frontend to production backend
  - [ ] Test database connectivity from production backend to production SQL Server database

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
  - [ ] Create Review entity model in EF Core
  - [ ] Create EF Core migration for Review model
  - [ ] Create review API endpoints (POST, GET, PUT, DELETE /api/reviews)
  - [ ] Implement create review endpoint (POST /api/reviews)
  - [ ] Implement get reviews endpoint (GET /api/products/{id}/reviews)
  - [ ] Implement update review endpoint (PUT /api/reviews/{id})
  - [ ] Implement delete review endpoint (DELETE /api/reviews/{id})
  - [ ] Add review moderation flag to Review entity
  - [ ] Add authorization (users can only edit/delete their own reviews)

#### Task 14.2: Review System Frontend

- **Priority:** Medium
- **Estimated Time:** 1 week
- **Dependencies:** Task 14.1
- **Subtasks:**
  - [ ] Design review section on product page
  - [ ] Create review form component
  - [ ] Create API client functions for reviews
  - [ ] Display reviews list (fetch from API)
  - [ ] Add review rating (stars)
  - [ ] Add review sorting (newest, highest rated, etc.) - API supports sorting
  - [ ] Add review pagination (API supports pagination)
  - [ ] Handle review submission (POST to API)

#### Task 14.3: Review Moderation (Admin)

- **Priority:** Medium
- **Estimated Time:** 3-4 days
- **Dependencies:** Task 14.1, Task 7.1
- **Subtasks:**
  - [ ] Create review moderation page (admin frontend)
  - [ ] Create get pending reviews API endpoint (GET /api/admin/reviews/pending)
  - [ ] Create approve/reject review API endpoints (PUT /api/admin/reviews/{id}/approve, PUT /api/admin/reviews/{id}/reject)
  - [ ] Implement approve/reject review (frontend calls API)
  - [ ] Add review flagging functionality (API endpoint)
  - [ ] Create review statistics API endpoint (GET /api/admin/reviews/statistics)
  - [ ] Display review statistics (fetch from API)
  - [ ] Create API client functions for review moderation

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
  - [ ] Create Subscription entity model in EF Core
  - [ ] Create EF Core migration for Subscription model
  - [ ] Create subscription API endpoints (POST, GET, PUT, DELETE /api/subscriptions)
  - [ ] Implement create subscription endpoint
  - [ ] Implement subscription management endpoints (pause, resume, cancel)
  - [ ] Add subscription scheduling logic (background service or scheduled job)
  - [ ] Implement subscription renewal process (automated)
  - [ ] Add subscription status tracking
  - [ ] Create subscription renewal background service (IHostedService)

#### Task 15.2: Subscription Frontend

- **Priority:** Medium
- **Estimated Time:** 1.5 weeks
- **Dependencies:** Task 15.1
- **Subtasks:**
  - [ ] Add subscription option to product pages
  - [ ] Design subscription selection UI
  - [ ] Create subscription management dashboard (fetch from API)
  - [ ] Create get user subscriptions API endpoint (GET /api/subscriptions/me)
  - [ ] Add frequency selection (weekly, monthly, etc.)
  - [ ] Create pause/resume subscription API endpoints
  - [ ] Add pause/resume subscription functionality (frontend calls API)
  - [ ] Create cancel subscription API endpoint
  - [ ] Add cancel subscription functionality (frontend calls API)
  - [ ] Display upcoming deliveries (fetch from API)
  - [ ] Create API client functions for subscription operations

#### Task 15.3: Subscription Admin

- **Priority:** Medium
- **Estimated Time:** 1 week
- **Dependencies:** Task 15.1, Task 7.1
- **Subtasks:**
  - [ ] Create subscription management page (admin frontend)
  - [ ] Create get all subscriptions API endpoint (GET /api/admin/subscriptions)
  - [ ] View all subscriptions (fetch from API)
  - [ ] Create update subscription status API endpoint (PUT /api/admin/subscriptions/{id}/status)
  - [ ] Manage subscription status (frontend calls API)
  - [ ] Create subscription analytics API endpoint (GET /api/admin/subscriptions/analytics)
  - [ ] View subscription analytics (fetch from API)
  - [ ] Create API client functions for admin subscription operations

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
  - [ ] Create newsletter signup form (frontend)
  - [ ] Create NewsletterSubscriber entity model in EF Core
  - [ ] Create newsletter subscription API endpoint (POST /api/newsletter/subscribe)
  - [ ] Store newsletter subscribers (EF Core)
  - [ ] Create welcome email for newsletter (Razor template)
  - [ ] Create unsubscribe API endpoint (POST /api/newsletter/unsubscribe)
  - [ ] Add unsubscribe functionality (frontend calls API)
  - [ ] Create API client function for newsletter

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
  - [ ] Create Points and PointsHistory entity models in EF Core
  - [ ] Create EF Core migration for points models
  - [ ] Implement points earning logic (service layer)
  - [ ] Implement points redemption logic (service layer)
  - [ ] Add points expiration rules (background service)
  - [ ] Create points API endpoints (GET, POST /api/points)
  - [ ] Create get points balance API endpoint (GET /api/points/balance)
  - [ ] Create points history API endpoint (GET /api/points/history)

#### Task 18.2: Points System Frontend

- **Priority:** Low
- **Estimated Time:** 1 week
- **Dependencies:** Task 18.1
- **Subtasks:**
  - [ ] Display points balance to users (fetch from API)
  - [ ] Show points earning opportunities
  - [ ] Create points redemption interface
  - [ ] Display points history (fetch from API)
  - [ ] Add points to checkout flow
  - [ ] Create API client functions for points operations

---

### Epic 19: Advanced Analytics

#### Task 19.1: Analytics Dashboard (Admin)

- **Priority:** Low
- **Estimated Time:** 1.5 weeks
- **Dependencies:** Task 7.1
- **Subtasks:**
  - [ ] Design analytics dashboard (admin frontend)
  - [ ] Create sales analytics API endpoint (GET /api/admin/analytics/sales)
  - [ ] Implement sales analytics (backend calculations)
  - [ ] Create customer analytics API endpoint (GET /api/admin/analytics/customers)
  - [ ] Implement customer analytics (backend calculations)
  - [ ] Create product analytics API endpoint (GET /api/admin/analytics/products)
  - [ ] Implement product analytics (backend calculations)
  - [ ] Add charts and graphs (frontend visualization)
  - [ ] Add date range filtering (API supports date filtering)
  - [ ] Create export analytics API endpoint (GET /api/admin/analytics/export)
  - [ ] Export analytics data (CSV/Excel)
  - [ ] Create API client functions for analytics

---

### Epic 20: Additional Integrations

#### Task 20.1: Shipping Integration

- **Priority:** Medium
- **Estimated Time:** 1.5 weeks
- **Dependencies:** Task 5.2
- **Subtasks:**
  - [ ] Integrate with shipping API (USPS, FedEx, UPS) - backend service
  - [ ] Create shipping rate calculation API endpoint (POST /api/shipping/rates)
  - [ ] Calculate real-time shipping rates (backend)
  - [ ] Create shipping label generation API endpoint (POST /api/shipping/labels)
  - [ ] Generate shipping labels (backend)
  - [ ] Create shipment tracking API endpoint (GET /api/shipping/track/{trackingNumber})
  - [ ] Track shipments (backend integration)
  - [ ] Create API client functions for shipping

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
- **Total Tasks:** ~121+ main tasks (includes new API client setup task)
- **Total Subtasks:** ~400+ subtasks
- **Phase 1 Duration:** 8-12 weeks
- **Phase 2 Duration:** 6-8 weeks
- **Phase 3 Duration:** 8-12 weeks
- **Total Project Duration:** 22-32 weeks (5.5-8 months)

---

**Last Updated:** 2026-01-XX
**Document Version:** 3.0 (Updated for .NET backend architecture)
