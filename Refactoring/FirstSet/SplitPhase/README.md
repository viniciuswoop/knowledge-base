# Split Phase

## What It Is

**Split Phase** is a refactoring technique used when a function or process does **two distinct things in sequence**.  
The goal is to **split the function into separate phases**, each handling a single responsibility, improving clarity, testability, and maintainability.

## Motivation

- **Code Readability**  
  Separating distinct operations makes each step easier to understand and reason about.

- **Code Complexity**  
  Reduces cognitive load by isolating unrelated logic into distinct phases, enforcing separation of concerns.

- **Maintainability and Extensibility**  
  Each phase can be modified or extended independently without affecting the other.

- **Code Duplication**  
  Splitting phases helps identify repeated logic that can be reused or abstracted.

- **Testability**  
  Each phase can be tested independently, making it easier to write unit tests and ensure correctness.

## When to Apply

- A function **performs multiple independent operations** in sequence.  
- You want to **clarify intent** and make the logic easier to follow.  
- Some parts of the function may need **independent testing or reuse**.

## When Not to Apply

- The function is already **simple and focused** on a single responsibility.  
- Splitting would **add unnecessary abstraction** with no real benefit.

## Example in C#

Before refactoring (mixed responsibilities in one function):

```csharp
public class OrderProcessor
{
    public decimal ProcessOrder(List<OrderItem> items, decimal taxRate)
    {
        // Phase 1: calculate subtotal
        decimal subtotal = items.Sum(i => i.Price * i.Quantity);

        // Phase 2: apply tax
        decimal tax = subtotal * taxRate;

        // Phase 3: apply discount
        decimal discount = items.Sum(i => i.Price * i.Quantity) * 0.05m;

        // Return final total
        return subtotal + tax - discount;
    }
}

// Client usage
var items = new List<OrderItem>
{
    new OrderItem("Book", 10, 2),
    new OrderItem("Pen", 5, 5)
};

var processor = new OrderProcessor();
decimal total = processor.ProcessOrder(items, 0.1m);
Console.WriteLine($"Total: {total:C}");
```
After refactoring:
```csharp
public class OrderProcessor
{
    public decimal CalculateSubtotal(List<OrderItem> items)
    {
        return items.Sum(i => i.Price * i.Quantity);
    }

    public decimal ApplyTax(decimal subtotal, decimal taxRate)
    {
        return subtotal * taxRate;
    }

    public decimal ApplyDiscount(decimal subtotal, decimal discountRate)
    {
        return subtotal * discountRate;
    }

    public decimal CalculateTotal(List<OrderItem> items, decimal taxRate, decimal discountRate)
    {
        decimal subtotal = CalculateSubtotal(items);
        decimal tax = ApplyTax(subtotal, taxRate);
        decimal discount = ApplyDiscount(subtotal, discountRate);
        return subtotal + tax - discount;
    }
}

// Client usage
var items = new List<OrderItem>
{
    new OrderItem("Book", 10, 2),
    new OrderItem("Pen", 5, 5)
};

var processor = new OrderProcessor();
decimal total = processor.CalculateTotal(items, 0.1m, 0.05m);
Console.WriteLine($"Total: {total:C}");

