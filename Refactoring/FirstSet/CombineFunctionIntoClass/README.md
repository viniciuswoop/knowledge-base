# Combine Functions into Class

## What It Is

**Combine Functions into Class** is a refactoring technique where related functions that operate on the same concept are **grouped into a single class**.  
This improves cohesion, enforces separation of concerns, and makes the code easier to understand and maintain.

## Motivation

- **Code Readability**  
  Grouping related functions clarifies their responsibility and relationship.

- **Code Complexity**  
  Enforce separation of concerns to tackle complexity by proposing a clear structure.

- **Maintainability and Extensibility**  
  Changes or extensions are easier to implement when related functions are centralized.

- **Code Duplication**  
  Helps prevent duplicating logic by providing a single class responsible for the behavior.

## When to Apply

- Multiple functions **operate on the same data or domain concept** but are scattered across the codebase.  
- You want to **improve cohesion** and encapsulate related behavior.


## When Not to Apply

- Functions are **unrelated**; combining them would create a class with no clear purpose.  
- Functions are **trivial or rarely used**, so combining them adds unnecessary complexity.

## Example in C#

Before refactoring:

```csharp
// Functions scattered across the codebase
public decimal CalculateSubtotal(List<OrderItem> items)
{
    return items.Sum(i => i.Price * i.Quantity);
}

public decimal CalculateTax(List<OrderItem> items, decimal taxRate)
{
    return items.Sum(i => i.Price * i.Quantity) * taxRate;
}

public decimal CalculateDiscount(List<OrderItem> items, decimal discountRate)
{
    return items.Sum(i => i.Price * i.Quantity) * discountRate;
}

// Client usage
var items = new List<OrderItem>
{
    new OrderItem("Book", 10, 2),
    new OrderItem("Pen", 5, 5)
};

decimal subtotal = CalculateSubtotal(items);
decimal tax = CalculateTax(items, 0.1m);
decimal discount = CalculateDiscount(items, 0.05m);
decimal total = subtotal + tax - discount;
Console.WriteLine($"Total: {total:C}");
```
After refactoring:
```csharp
public class OrderCalculator
{
    private readonly List<OrderItem> _items;
    private readonly decimal _taxRate;
    private readonly decimal _discountRate;

    public OrderCalculator(List<OrderItem> items, decimal taxRate, decimal discountRate)
    {
        _items = items;
        _taxRate = taxRate;
        _discountRate = discountRate;
    }

    public decimal Subtotal => _items.Sum(i => i.Price * i.Quantity);

    public decimal Tax => Subtotal * _taxRate;

    public decimal Discount => Subtotal * _discountRate;

    public decimal Total => Subtotal + Tax - Discount;
}

// Client usage
var items = new List<OrderItem>
{
    new OrderItem("Book", 10, 2),
    new OrderItem("Pen", 5, 5)
};

var calculator = new OrderCalculator(items, 0.1m, 0.05m);
Console.WriteLine($"Subtotal: {calculator.Subtotal:C}");
Console.WriteLine($"Tax: {calculator.Tax:C}");
Console.WriteLine($"Discount: {calculator.Discount:C}");
Console.WriteLine($"Total: {calculator.Total:C}");

