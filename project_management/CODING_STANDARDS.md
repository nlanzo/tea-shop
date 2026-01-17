# Eerie Tea - Coding Standards and Conventions

This document defines the coding standards and conventions for the Eerie Tea e-commerce project, covering both the .NET backend and Next.js frontend.

---

## General Principles

1. **Consistency**: Follow consistent patterns throughout the codebase
2. **Readability**: Code should be self-documenting with clear naming
3. **Maintainability**: Write code that is easy to modify and extend
4. **Type Safety**: Leverage TypeScript and C# type systems fully
5. **SOLID Principles**: Apply SOLID principles in backend code

---

## Backend (.NET / C#) Standards

### Naming Conventions

- **Classes**: PascalCase (e.g., `ProductService`, `OrderController`)
- **Methods**: PascalCase (e.g., `GetProductById`, `CreateOrder`)
- **Properties**: PascalCase (e.g., `ProductName`, `OrderTotal`)
- **Private fields**: `_camelCase` with underscore prefix (e.g., `_productRepository`)
- **Local variables**: camelCase (e.g., `productId`, `orderTotal`)
- **Constants**: PascalCase (e.g., `MaxRetryAttempts`)
- **Interfaces**: Start with `I` (e.g., `IProductService`, `IEmailService`)
- **Async methods**: End with `Async` suffix (e.g., `GetProductByIdAsync`)

### File Organization

- One class per file
- File name matches class name
- Namespace matches folder structure
- Group related files in folders by feature/domain

### Code Style

```csharp
// ✅ Good: Clear, descriptive names
public async Task<ProductDto> GetProductByIdAsync(int productId)
{
    var product = await _productRepository.GetByIdAsync(productId);
    if (product == null)
    {
        throw new NotFoundException($"Product with ID {productId} not found.");
    }
    return _mapper.Map<ProductDto>(product);
}

// ❌ Bad: Unclear names, no error handling
public async Task<ProductDto> Get(int id)
{
    return await _repo.Get(id);
}
```

### Best Practices

1. **Use async/await** for all I/O operations
2. **Use dependency injection** for all dependencies
3. **Validate input** at controller/API boundary
4. **Use DTOs** for API contracts (never expose entities directly)
5. **Handle errors** gracefully with custom exceptions
6. **Use Entity Framework Core** efficiently (avoid N+1 queries)
7. **Use LINQ** for querying, but be aware of performance
8. **Log appropriately** (use structured logging)

### Entity Framework Core

```csharp
// ✅ Good: Explicit configuration, clear relationships
public class ProductConfiguration : IEntityTypeConfiguration<Product>
{
    public void Configure(EntityTypeBuilder<Product> builder)
    {
        builder.HasKey(p => p.Id);
        builder.Property(p => p.Name)
            .IsRequired()
            .HasMaxLength(200);
        builder.HasIndex(p => p.Slug)
            .IsUnique();
        builder.HasMany(p => p.OrderItems)
            .WithOne(oi => oi.Product)
            .HasForeignKey(oi => oi.ProductId);
    }
}
```

### API Controllers

```csharp
// ✅ Good: Clear route, proper HTTP methods, error handling
[ApiController]
[Route("api/[controller]")]
public class ProductsController : ControllerBase
{
    private readonly IProductService _productService;
    
    public ProductsController(IProductService productService)
    {
        _productService = productService;
    }
    
    [HttpGet("{id:int}")]
    [ProducesResponseType(typeof(ProductDto), StatusCodes.Status200OK)]
    [ProducesResponseType(StatusCodes.Status404NotFound)]
    public async Task<ActionResult<ProductDto>> GetProduct(int id)
    {
        var product = await _productService.GetProductByIdAsync(id);
        return Ok(product);
    }
}
```

### Comments and Documentation

- Use XML documentation comments for public APIs
- Explain **why**, not **what** (code should be self-explanatory)
- Keep comments up-to-date with code changes

```csharp
/// <summary>
/// Retrieves a product by its unique identifier.
/// </summary>
/// <param name="productId">The unique identifier of the product.</param>
/// <returns>The product DTO if found.</returns>
/// <exception cref="NotFoundException">Thrown when product is not found.</exception>
public async Task<ProductDto> GetProductByIdAsync(int productId)
{
    // Implementation
}
```

---

## Frontend (Next.js / TypeScript) Standards

### Naming Conventions

- **Components**: PascalCase (e.g., `ProductCard`, `CartItem`)
- **Files**: Match component name (e.g., `ProductCard.tsx`)
- **Functions**: camelCase (e.g., `getProductById`, `handleSubmit`)
- **Variables**: camelCase (e.g., `productId`, `cartItems`)
- **Constants**: UPPER_SNAKE_CASE (e.g., `API_BASE_URL`, `MAX_CART_ITEMS`)
- **Types/Interfaces**: PascalCase (e.g., `Product`, `OrderItem`)
- **Hooks**: Start with `use` (e.g., `useAuth`, `useCart`)
- **Custom hooks**: camelCase starting with `use` (e.g., `useProduct`, `useOrder`)

### File Organization

```
components/
  products/
    ProductCard.tsx
    ProductGrid.tsx
    ProductCard.test.tsx  # Tests co-located
lib/
  api/
    products.ts
    orders.ts
types/
  product.ts
  order.ts
```

### TypeScript Standards

```typescript
// ✅ Good: Explicit types, proper interfaces
interface Product {
  id: number;
  name: string;
  price: number;
  description: string;
  inStock: boolean;
}

async function getProductById(id: number): Promise<Product> {
  const response = await apiClient.get<Product>(`/api/products/${id}`);
  return response.data;
}

// ❌ Bad: Any types, no error handling
async function getProduct(id: any): Promise<any> {
  return await fetch(`/api/products/${id}`);
}
```

### React Component Standards

```typescript
// ✅ Good: TypeScript, proper props interface, clear structure
interface ProductCardProps {
  product: Product;
  onAddToCart: (productId: number) => void;
}

export function ProductCard({ product, onAddToCart }: ProductCardProps) {
  const handleClick = () => {
    onAddToCart(product.id);
  };

  return (
    <div className="product-card">
      <h3>{product.name}</h3>
      <p>${product.price.toFixed(2)}</p>
      <button onClick={handleClick}>Add to Cart</button>
    </div>
  );
}
```

### Best Practices

1. **Use TypeScript strictly** - avoid `any` types
2. **Use functional components** with hooks
3. **Extract custom hooks** for reusable logic
4. **Use proper error boundaries** for error handling
5. **Handle loading states** appropriately
6. **Validate forms** with Zod schemas
7. **Use React Hook Form** for form management
8. **Keep components small** and focused (single responsibility)

### API Client Standards

```typescript
// ✅ Good: Typed API client, error handling, proper structure
import { apiClient } from './client';
import type { Product, ProductListResponse } from '@/types/product';

export async function getProducts(params?: {
  page?: number;
  limit?: number;
  category?: string;
}): Promise<ProductListResponse> {
  const response = await apiClient.get<ProductListResponse>('/api/products', {
    params,
  });
  return response.data;
}

export async function getProductById(id: number): Promise<Product> {
  const response = await apiClient.get<Product>(`/api/products/${id}`);
  return response.data;
}
```

### State Management (Zustand)

```typescript
// ✅ Good: Clear store structure, typed actions
interface CartStore {
  items: CartItem[];
  addItem: (product: Product, quantity: number) => void;
  removeItem: (productId: number) => void;
  clearCart: () => void;
  total: number;
}

export const useCartStore = create<CartStore>((set, get) => ({
  items: [],
  addItem: (product, quantity) => {
    // Implementation
  },
  removeItem: (productId) => {
    // Implementation
  },
  clearCart: () => set({ items: [] }),
  get total() {
    return get().items.reduce((sum, item) => sum + item.total, 0);
  },
}));
```

### Form Validation (Zod)

```typescript
// ✅ Good: Schema validation, type inference
import { z } from 'zod';

const productSchema = z.object({
  name: z.string().min(1, 'Name is required').max(200),
  price: z.number().positive('Price must be positive'),
  description: z.string().min(10, 'Description must be at least 10 characters'),
  categoryId: z.number().int().positive(),
});

type ProductFormData = z.infer<typeof productSchema>;
```

### Comments and Documentation

- Use JSDoc comments for complex functions
- Explain business logic, not obvious code
- Document component props with TypeScript interfaces

```typescript
/**
 * Calculates the total price including tax and shipping.
 * @param subtotal - The subtotal before tax and shipping
 * @param taxRate - The tax rate as a decimal (e.g., 0.08 for 8%)
 * @param shippingCost - The shipping cost
 * @returns The total price
 */
function calculateTotal(
  subtotal: number,
  taxRate: number,
  shippingCost: number
): number {
  const tax = subtotal * taxRate;
  return subtotal + tax + shippingCost;
}
```

---

## Common Standards (Both Projects)

### Git Commit Messages

Follow conventional commits format:

```
feat: add product search functionality
fix: resolve cart sync issue on login
docs: update API documentation
refactor: simplify order processing logic
test: add unit tests for product service
chore: update dependencies
```

### Error Handling

- **Backend**: Use custom exceptions, return appropriate HTTP status codes
- **Frontend**: Handle errors gracefully, show user-friendly messages
- **Log errors** appropriately (don't log sensitive information)

### Testing

- Write tests for business logic
- Test edge cases and error scenarios
- Keep tests simple and focused
- Use descriptive test names

### Code Review Checklist

- [ ] Code follows naming conventions
- [ ] No hardcoded values (use constants/config)
- [ ] Error handling is appropriate
- [ ] No commented-out code
- [ ] No console.logs in production code
- [ ] Types are properly defined (no `any`)
- [ ] Performance considerations addressed
- [ ] Security considerations addressed
- [ ] Tests are included (if applicable)

---

## Tools and Configuration

### Backend

- **Formatter**: Built-in C# formatter (Visual Studio/Rider)
- **Linter**: EditorConfig for consistent formatting
- **Code Analysis**: Built-in .NET analyzers

### Frontend

- **Formatter**: Biome (configured in `biome.json`)
- **Linter**: ESLint (configured in `eslint.config.mjs`)
- **Type Checker**: TypeScript compiler

---

## Resources

- [.NET Coding Conventions](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/coding-conventions)
- [TypeScript Style Guide](https://typescript-eslint.io/rules/)
- [React Best Practices](https://react.dev/learn/describing-the-ui)
- [Next.js Best Practices](https://nextjs.org/docs)

---

**Last Updated:** 2026-01-XX
