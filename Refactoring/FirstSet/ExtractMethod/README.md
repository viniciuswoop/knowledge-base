# Extract Method / Function

## What It Is

**Extract Method** (or Extract Function) is a refactoring technique where a portion of code within an existing method is moved into a **new, separate method**.  
The original method then calls this new method, preserving the original behavior while isolating a specific piece of logic.

## Motivation

- **Code Readability**
  Breaking long methods into smaller, well-named methods makes the code easier to understand at a glance.
  
- **Code Complexity**
  Isolating distinct logic reduces cognitive load and simplifies reasoning about the method.
  
- **Maintainability and Extensibility**
  Extracted methods can be modified, extended, or reused without affecting the rest of the code.
  
- **Testability**
  Smaller methods can be tested independently, improving reliability and confidence in code changes.
  
- **Code Duplication**
  Repeated code blocks can be extracted into a single method, reducing duplication and future maintenance overhead.

## When to Apply

- The method is **too long** or performs multiple distinct tasks.
- There are **repeated code patterns** within a method.
- A block of code can be **logically grouped** and given a descriptive name.
- You want to **isolate a piece of logic** for testing or reuse.

## When Not to Apply

- The code block is **trivial**, such as a single line that is already readable.
- The extraction **adds unnecessary indirection**, making the code harder to follow.
- The extracted logic is **tightly coupled** to local variables that are not easily passed as parameters.

## Example in C#

Before refactoring:

```csharp
public void ProcessOrder(Order order)
{
    Console.WriteLine($"Processing order {order.Id}");

    // Calculate total
    decimal total = 0;
    foreach (var item in order.Items)
    {
        total += item.Price * item.Quantity;
    }
    Console.WriteLine($"Total amount: {total}");

    // Send confirmation
    Console.WriteLine($"Sending confirmation email to {order.CustomerEmail}");
}

```
After refactoring
```csharp
public void ProcessOrder(Order order)
{
    Console.WriteLine($"Processing order {order.Id}");

    decimal total = CalculateTotal(order);
    Console.WriteLine($"Total amount: {total}");

    SendConfirmation(order);
}

private decimal CalculateTotal(Order order)
{
    decimal total = 0;
    foreach (var item in order.Items)
    {
        total += item.Price * item.Quantity;
    }
    return total;
}

private void SendConfirmation(Order order)
{
    Console.WriteLine($"Sending confirmation email to {order.CustomerEmail}");
}
