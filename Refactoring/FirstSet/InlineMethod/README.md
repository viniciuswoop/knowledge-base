# Inline Function

## What It Is

**Inline Function** is a refactoring technique where the body of a function is **moved directly into its callers**, and the original function is removed.  
This is done when the function adds no meaningful abstraction or indirection.

## Motivation

- **Code Readability**: Eliminates unnecessary layers of indirection, making the code easier to follow.
- **Code Complexity**: Simplifies the structure by removing trivial functions that do not convey additional intent.
- **Maintainability and Extensibility**: Reduces the overhead of maintaining a function that provides no benefit, making the codebase simpler to modify.
- **Testability**: In some cases, inlining can make testing more straightforward by consolidating logic in one place.

## When to Apply
- The function is **short and trivial**, providing little or no semantic value.
- The function **delegates directly** to another function without adding clarity.
- Inlining improves **readability** and reduces unnecessary abstraction.

## When Not to Apply
- The function **adds meaningful abstraction** or clarifies intent.
- The function is **used in multiple places** and inlining would create duplication.
- Removing the function would **reduce testability or modularity**.

## Example in C#

Before refactoring:

```csharp
public int GetTotalItems(Order order)
{
    return CalculateItemCount(order);
}

private int CalculateItemCount(Order order)
{
    int count = 0;
    foreach (var item in order.Items)
    {
        count += item.Quantity;
    }
    return count;
}

```
After refactoring

```csharp
public int GetTotalItems(Order order)
{
    int count = 0;
    foreach (var item in order.Items)
    {
        count += item.Quantity;
    }
    return count;
}
