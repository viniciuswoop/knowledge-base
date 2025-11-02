# Extract Variable

## What It Is

**Extract Variable** is a refactoring technique where an **expression is replaced by a variable** that holds its result.  
The variable is introduced with a clear and meaningful name, making complex expressions easier to read and understand.

## Motivation

- **Code Readability**  
  Simplifies complex expressions by introducing intermediate variables with descriptive names, clarifying the code’s intent.

- **Code Complexity**  
  Reduces mental effort by breaking down long or nested expressions into smaller, understandable parts.

- **Maintainability and Extensibility**  
  Named variables make it easier to locate and modify specific logic in the future.

- **Testability**  
  Although minor, explicit variables can help when debugging, stepping through, or inspecting values during testing.

## When to Apply

- You have **complex expressions** that are difficult to understand at a glance.  
- The same expression is **used multiple times** within a method.  
- A **descriptive variable name** can convey the intent more clearly than the raw expression.

## When Not to Apply

- The expression is **simple and self-explanatory**, and introducing a variable would add noise.  
- The variable name does not improve understanding compared to the expression itself.  
- The code becomes **cluttered** with unnecessary temporary variables.

## Example in C#

Before refactoring:

```csharp
public void PrintOrderSummary(Order order)
{
    Console.WriteLine($"Order {order.Id}: {order.Items.Count} items, total price {order.Items.Sum(i => i.Price * i.Quantity) * (1 - order.Discount)}");
}
```
After refactoring:
```csharp
public void PrintOrderSummary(Order order)
{
    var itemCount = order.Items.Count;
    var subtotal = order.Items.Sum(i => i.Price * i.Quantity);
    var totalPrice = subtotal * (1 - order.Discount);

    Console.WriteLine($"Order {order.Id}: {itemCount} items, total price {totalPrice}");
}

