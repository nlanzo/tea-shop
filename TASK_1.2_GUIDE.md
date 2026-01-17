# Task 1.2: Development Environment Setup - Step-by-Step Guide

This guide will walk you through setting up your development environment for both the frontend and backend.

---

## Prerequisites Check ✅

You already have:
- ✅ .NET SDK 10.0.102 installed
- ✅ Node.js v22.17.1 installed (meets 20.9+ requirement)
- ✅ pnpm 10.28.0 installed
- ✅ Next.js frontend project initialized

---

## Step 1: Create .NET Solution and Projects

### 1.1 Create the Solution

Navigate to the backend directory and create a new solution:

```bash
cd backend
dotnet new sln -n EerieTea
```

**What this does:** Creates a solution file (`EerieTea.sln`) that will contain all your .NET projects.

### 1.2 Create the Projects

Create each project in the `src/` directory:

```bash
# Create Web API project (main entry point)
dotnet new webapi -n EerieTea.Api -f net10.0 -o src/EerieTea.Api

# Create Core library (domain models, DTOs, interfaces)
dotnet new classlib -n EerieTea.Core -f net10.0 -o src/EerieTea.Core

# Create Infrastructure library (data access, external services)
dotnet new classlib -n EerieTea.Infrastructure -f net10.0 -o src/EerieTea.Infrastructure

# Create Tests project
dotnet new xunit -n EerieTea.Tests -f net10.0 -o src/EerieTea.Tests
```

**What this does:**
- `webapi`: Creates an ASP.NET Core Web API project template
- `classlib`: Creates a class library (reusable code)
- `xunit`: Creates a test project with xUnit framework
- `-f net10.0`: Targets .NET 10.0 framework
- `-o`: Specifies output directory

### 1.3 Add Projects to Solution

```bash
dotnet sln add src/EerieTea.Api/EerieTea.Api.csproj
dotnet sln add src/EerieTea.Core/EerieTea.Core.csproj
dotnet sln add src/EerieTea.Infrastructure/EerieTea.Infrastructure.csproj
dotnet sln add src/EerieTea.Tests/EerieTea.Tests.csproj
```

**What this does:** Adds all projects to the solution so they can reference each other.

### 1.4 Set Up Project References

The Infrastructure project needs to reference Core, and the API project needs both:

```bash
# Infrastructure references Core
dotnet add src/EerieTea.Infrastructure/EerieTea.Infrastructure.csproj reference src/EerieTea.Core/EerieTea.Core.csproj

# API references both Core and Infrastructure
dotnet add src/EerieTea.Api/EerieTea.Api.csproj reference src/EerieTea.Core/EerieTea.Core.csproj
dotnet add src/EerieTea.Api/EerieTea.Api.csproj reference src/EerieTea.Infrastructure/EerieTea.Infrastructure.csproj

# Tests reference all projects
dotnet add src/EerieTea.Tests/EerieTea.Tests.csproj reference src/EerieTea.Api/EerieTea.Api.csproj
dotnet add src/EerieTea.Tests/EerieTea.Tests.csproj reference src/EerieTea.Core/EerieTea.Core.csproj
dotnet add src/EerieTea.Tests/EerieTea.Tests.csproj reference src/EerieTea.Infrastructure/EerieTea.Infrastructure.csproj
```

**What this does:** Sets up the dependency chain:
- Infrastructure → Core
- API → Core + Infrastructure
- Tests → All projects (to test them)

### 1.5 Verify Build

```bash
dotnet build
```

**What this does:** Builds all projects to ensure everything is set up correctly. You should see "Build succeeded" if everything is working.

---

## Step 2: Configure TypeScript Strict Mode (Frontend)

### 2.1 Check Current TypeScript Config

```bash
cd ../frontend
cat tsconfig.json
```

### 2.2 Update tsconfig.json for Strict Mode

Open `frontend/tsconfig.json` and ensure these settings are present:

```json
{
  "compilerOptions": {
    "strict": true,
    "noUnusedLocals": true,
    "noUnusedParameters": true,
    "noImplicitReturns": true,
    "noFallthroughCasesInSwitch": true
  }
}
```

**What this does:**
- `strict`: Enables all strict type checking options
- `noUnusedLocals`: Error on unused local variables
- `noUnusedParameters`: Error on unused function parameters
- `noImplicitReturns`: Error when function doesn't return in all code paths
- `noFallthroughCasesInSwitch`: Error on fallthrough cases in switch statements

### 2.3 Verify TypeScript Compilation

```bash
pnpm run build
```

**What this does:** Checks if TypeScript compiles without errors in strict mode.

---

## Step 3: Install Entity Framework Core and SQL Server Provider

### 3.1 Install EF Core Packages

```bash
cd ../backend

# Install EF Core design tools (needed for migrations)
dotnet add src/EerieTea.Api/EerieTea.Api.csproj package Microsoft.EntityFrameworkCore.Design

# Install SQL Server provider
dotnet add src/EerieTea.Infrastructure/EerieTea.Infrastructure.csproj package Microsoft.EntityFrameworkCore.SqlServer

# Install EF Core in Infrastructure (where DbContext will live)
dotnet add src/EerieTea.Infrastructure/EerieTea.Infrastructure.csproj package Microsoft.EntityFrameworkCore
```

**What this does:**
- `Microsoft.EntityFrameworkCore.Design`: Tools for creating migrations
- `Microsoft.EntityFrameworkCore.SqlServer`: SQL Server database provider
- `Microsoft.EntityFrameworkCore`: Core EF Core library

### 3.2 Verify Installation

```bash
dotnet restore
dotnet build
```

**What this does:** Restores NuGet packages and builds to ensure everything installed correctly.

---

## Step 4: Set Up Local SQL Server Database

### 4.1 Check if SQL Server is Running

**For Windows (WSL):**
```bash
# Check if SQL Server service is running
# You may need to install SQL Server Express or use LocalDB
```

**For Linux:**
```bash
# Check if SQL Server is installed
sqlcmd -S localhost -U sa -Q "SELECT @@VERSION" 2>&1 || echo "SQL Server not running"
```

### 4.2 Install SQL Server (if needed)

**Option 1: SQL Server Express (Full SQL Server)**
- Download from: https://www.microsoft.com/en-us/sql-server/sql-server-downloads
- Install SQL Server Express

**Option 2: SQL Server LocalDB (Lightweight, Windows only)**
- Usually comes with Visual Studio
- Or install SQL Server Express with LocalDB option

**Option 3: Docker (Cross-platform)**
```bash
docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=YourStrong@Passw0rd" \
   -p 1433:1433 --name sql-server \
   -d mcr.microsoft.com/mssql/server:2022-latest
```

### 4.3 Create Database

Once SQL Server is running, create a database:

```bash
sqlcmd -S localhost -U sa -P YourPassword -Q "CREATE DATABASE EerieTeaDb"
```

Or use SQL Server Management Studio (SSMS) or Azure Data Studio to create it.

---

## Step 5: Configure Connection String (SECURE)

**⚠️ IMPORTANT:** Never commit connection strings with passwords to Git! We'll use .NET User Secrets for local development.

### 5.1 Update appsettings.json (Safe to Commit)

Edit `backend/src/EerieTea.Api/appsettings.json` with a **placeholder** connection string:

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.AspNetCore": "Warning"
    }
  },
  "AllowedHosts": "*",
  "ConnectionStrings": {
    "DefaultConnection": "Server=localhost;Database=EerieTeaDb;User Id=sa;Password=CHANGE_ME;TrustServerCertificate=True;"
  }
}
```

**Note:** This is just a placeholder. The actual connection string will come from User Secrets (see below).

**Connection String Format (for reference):**
- `Server=localhost`: SQL Server instance
- `Database=EerieTeaDb`: Database name
- `User Id=sa`: SQL Server username
- `Password=YourPassword`: SQL Server password (use User Secrets!)
- `TrustServerCertificate=True`: Required for local development

**For LocalDB (Windows):**
```
Server=(localdb)\\mssqllocaldb;Database=EerieTeaDb;Trusted_Connection=True;TrustServerCertificate=True;
```

### 5.2 Set Up .NET User Secrets (Local Development)

User Secrets stores sensitive data outside your project directory and is **never committed to Git**.

**Initialize User Secrets:**
```bash
cd backend/src/EerieTea.Api
dotnet user-secrets init
```

**Set your connection string:**
```bash
# For SQL Server with username/password
dotnet user-secrets set "ConnectionStrings:DefaultConnection" "Server=localhost;Database=EerieTeaDb;User Id=sa;Password=YourActualPassword;TrustServerCertificate=True;"

# OR for LocalDB (Windows)
dotnet user-secrets set "ConnectionStrings:DefaultConnection" "Server=(localdb)\\mssqllocaldb;Database=EerieTeaDb;Trusted_Connection=True;TrustServerCertificate=True;"
```

**What this does:**
- Stores the connection string in your user profile (not in the project)
- Automatically loads in Development environment
- Never gets committed to Git
- Overrides values in `appsettings.json`

**Verify it's set:**
```bash
dotnet user-secrets list
```

You should see your connection string listed.

### 5.3 Create appsettings.Development.json (Optional)

Create `backend/src/EerieTea.Api/appsettings.Development.json` for development-specific settings:

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.AspNetCore": "Warning",
      "Microsoft.EntityFrameworkCore": "Information"
    }
  }
}
```

**Note:** Don't put connection strings here either! Use User Secrets. This file can be gitignored or committed (it's safe without secrets).

### 5.4 Verify .gitignore

Make sure these are in `.gitignore`:

```
# User Secrets (stored in user profile, but good to be explicit)
**/Properties/launchSettings.json

# Development settings (optional - can commit if no secrets)
**/appsettings.Development.json
**/appsettings.Local.json
```

**What gets committed:**
- ✅ `appsettings.json` (with placeholder)
- ✅ `appsettings.Production.json` (if you create one, with placeholders)

**What NEVER gets committed:**
- ❌ User Secrets (stored outside project)
- ❌ `appsettings.Development.json` (if it contains secrets)
- ❌ Any file with real passwords

---

## Step 6: Configure Environment Variables

### 6.1 Frontend Environment Variables

Create `frontend/.env.local`:

```bash
cd ../frontend
touch .env.local
```

Add to `.env.local`:
```
NEXT_PUBLIC_API_URL=http://localhost:5000
```

**What this does:** Sets the API URL that the frontend will use to call the backend.

### 6.2 Backend Environment Variables

Backend uses `appsettings.json` (already configured above). For production, you'll use Azure App Service configuration.

---

## Step 7: Set Up Testing Frameworks

### 7.1 Backend Testing (xUnit)

xUnit is already included when you created the test project. Install additional packages:

```bash
cd ../backend

# Install Moq (mocking framework)
dotnet add src/EerieTea.Tests/EerieTea.Tests.csproj package Moq

# Install FluentAssertions (readable assertions)
dotnet add src/EerieTea.Tests/EerieTea.Tests.csproj package FluentAssertions

# Install test server for integration tests
dotnet add src/EerieTea.Tests/EerieTea.Tests.csproj package Microsoft.AspNetCore.Mvc.Testing
```

### 7.2 Frontend Testing (Vitest)

```bash
cd ../frontend

# Install Vitest and testing libraries
pnpm add -D vitest @vitejs/plugin-react @testing-library/react @testing-library/jest-dom @testing-library/user-event jsdom

# Install Playwright for E2E testing
pnpm add -D @playwright/test
```

**What these packages do:**
- `vitest`: Test runner
- `@vitejs/plugin-react`: Enables Vitest to work with React/JSX
- `@testing-library/react`: Utilities for testing React components
- `@testing-library/jest-dom`: Additional matchers for DOM testing
- `@testing-library/user-event`: Simulate user interactions
- `jsdom`: DOM environment for tests (needed for `environment: 'jsdom'`)

### 7.3 Configure Vitest

Create `frontend/vitest.config.ts`:

```typescript
import { defineConfig } from 'vitest/config';
import react from '@vitejs/plugin-react';
import path from 'path';

export default defineConfig({
  plugins: [react()],
  test: {
    environment: 'jsdom',
    globals: true,
    setupFiles: ['./tests/setup.ts'],
  },
  resolve: {
    alias: {
      '@': path.resolve(__dirname, './src'),
    },
  },
});
```

Create `frontend/tests/setup.ts`:

```typescript
import '@testing-library/jest-dom';
```

### 7.4 Configure Playwright

```bash
cd frontend
npx playwright install
```

This downloads the browser binaries (Chromium, Firefox, WebKit).

**Install System Dependencies (Linux/WSL):**

After installing browsers, you may see a warning about missing system dependencies. Install them:

```bash
# Option 1: Use Playwright's automatic installer (recommended)
sudo npx playwright install-deps

# Option 2: Manual install (if you prefer)
sudo apt-get update
sudo apt-get install libasound2t64 libatk-bridge2.0-0 libatk1.0-0 libatspi2.0-0 libcups2 libdbus-1-3 libdrm2 libgbm1 libgtk-3-0 libnspr4 libnss3 libwayland-client0 libxcomposite1 libxdamage1 libxfixes3 libxkbcommon0 libxrandr2 libxss1 libxtst6
```

**What this does:**
- Installs system libraries needed for browsers to run
- Required for E2E tests to execute
- Only needed once per system

**Verify installation:**
```bash
npx playwright test --version
```

This will create `playwright.config.ts` automatically when you run your first test.

---

## Step 8: Initialize shadcn/ui

```bash
cd frontend
npx shadcn@latest init
```

**When prompted:**
- Would you like to use TypeScript? → **Yes**
- Which style would you like to use? → **Default** (or your preference)
- Which color would you like to use as base color? → **Slate** (or your preference)
- Where is your global CSS file? → **src/app/globals.css**
- Would you like to use CSS variables for colors? → **Yes**
- Where is your tailwind.config.js located? → **./tailwind.config.ts**
- Configure the import alias for components? → **@/components**
- Configure the import alias for utils? → **@/lib/utils**

---

## Step 9: Configure ESLint and Biome

### 9.1 ESLint

ESLint should already be configured by Next.js. Verify:

```bash
cd frontend
cat eslint.config.mjs
```

### 9.2 Biome

```bash
cd frontend

# Install Biome
pnpm add -D @biomejs/biome

# Initialize Biome config
npx @biomejs/biome init
```

This creates `biome.json`. You can customize it if needed.

---

## Step 10: Configure CORS in .NET API

### 10.1 Update Program.cs

Edit `backend/src/EerieTea.Api/Program.cs`:

```csharp
var builder = WebApplication.CreateBuilder(args);

// Add services
builder.Services.AddControllers();
builder.Services.AddEndpointsApiExplorer();
builder.Services.AddSwaggerGen();

// Configure CORS
builder.Services.AddCors(options =>
{
    options.AddPolicy("AllowFrontend", policy =>
    {
        policy.WithOrigins("http://localhost:3000") // Next.js dev server
              .AllowAnyMethod()
              .AllowAnyHeader()
              .AllowCredentials();
    });
});

var app = builder.Build();

// Configure the HTTP request pipeline
if (app.Environment.IsDevelopment())
{
    app.UseSwagger();
    app.UseSwaggerUI();
}

app.UseHttpsRedirection();

// Use CORS (must be before UseAuthorization)
app.UseCors("AllowFrontend");

app.UseAuthorization();

app.MapControllers();

app.Run();
```

**What this does:**
- Allows requests from `http://localhost:3000` (Next.js dev server)
- Allows all HTTP methods (GET, POST, etc.)
- Allows all headers
- Allows credentials (cookies, auth headers)

---

## Step 11: Verify Everything Works

### 11.1 Build Backend

```bash
cd backend
dotnet build
```

Should see: **Build succeeded**

### 11.2 Run Backend API

```bash
cd backend/src/EerieTea.Api
dotnet run
```

Should see: **Now listening on: https://localhost:5001** (or similar)

Visit: `https://localhost:5001/swagger` to see Swagger UI

### 11.3 Run Frontend

```bash
cd frontend
pnpm dev
```

Should see: **Ready on http://localhost:3000**

---

## Checklist

- [ ] .NET solution and projects created
- [ ] Project references set up correctly
- [ ] TypeScript strict mode enabled
- [ ] Entity Framework Core installed
- [ ] SQL Server provider installed
- [ ] SQL Server database created
- [ ] Connection string configured
- [ ] Environment variables set up
- [ ] xUnit, Vitest, Playwright installed
- [ ] shadcn/ui initialized
- [ ] ESLint and Biome configured
- [ ] CORS configured in .NET API
- [ ] Both projects build and run successfully

---

## Next Steps

Once Task 1.2 is complete, you can move on to:
- **Task 1.3**: Database Schema Design & Setup
- Start creating your entity models
- Set up your DbContext

---

## Troubleshooting

### SQL Server Connection Issues
- Make sure SQL Server is running
- Check firewall settings
- Verify connection string format
- Try `TrustServerCertificate=True` for local development

### Build Errors
- Run `dotnet restore` to restore NuGet packages
- Run `pnpm install` to restore npm packages
- Check that all project references are correct

### CORS Errors
- Make sure CORS middleware is before `UseAuthorization`
- Verify frontend URL matches CORS policy
- Check browser console for specific CORS error messages

---

**Good luck! Take your time and learn as you go.** 🚀
