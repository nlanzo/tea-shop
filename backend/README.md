# Eerie Tea - Backend API

.NET 10.0 + ASP.NET Core Web API backend for the Eerie Tea e-commerce platform.

## Project Structure

This backend follows a **layered architecture**:

- **EerieTea.Api**: Web API layer with controllers, middleware, and configuration
- **EerieTea.Core**: Domain models, DTOs, and business logic interfaces
- **EerieTea.Infrastructure**: Data access (EF Core), external services, and implementations
- **EerieTea.Tests**: Unit and integration tests

## Prerequisites

- .NET SDK 10.0 or higher
- SQL Server (LocalDB/Express for development, Azure SQL Database for production)
- Visual Studio 2022, VS Code, or Rider

## Getting Started

See the main [README.md](../README.md) for setup instructions.

## Configuration

- `appsettings.json`: Base configuration
- `appsettings.Development.json`: Development settings (gitignored)
- `appsettings.Production.json`: Production settings (gitignored)

## Database

- Development: Local SQL Server (Express or LocalDB)
- Production: Azure SQL Database

## API Documentation

Swagger/OpenAPI documentation available at `/swagger` when running in development mode.
