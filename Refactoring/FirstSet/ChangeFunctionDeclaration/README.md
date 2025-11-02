# Change Function Declaration

## What It Is

**Change Function Declaration** is a refactoring technique where you **modify the signature of a function** — including its name, parameters, or return type — without changing its external behavior.  
This allows the function to better reflect its intent, improve usability, or align with the evolving design of the system.

## Motivation

- **Code Readability**  
  Updating names or parameter lists can make a function’s purpose clearer to developers.

- **Code Complexity**  
  Simplifying or clarifying the interface reduces cognitive load when using the function.

- **Code Duplication**  
  Consolidating or standardizing similar functions can reduce redundant variations.

## When to Apply

- The function name is **misleading** or unclear.  
- A parameter can be **derived from other inputs**.  
- You want to **align the signature** with related functions for consistency.  

## When Not to Apply

- Changing the function signature would **break many existing callers** without strong justification.  
- The function is **well-named and clear**, with appropriate parameters and return type.  
- The function is **stable and not evolving**, and changes provide minimal value.

## Example in C#

Before refactoring:

```csharp
public decimal ComputeTotal(Order order, bool applyDiscount)
{
    decimal subtotal = order.Items.Sum(i => i.Price * i.Quantity);
    if (applyDiscount)
    {
        subtotal *= 0.9m; // Apply discount if requested
    }
    return subtotal;
}
```
After refactoring:
```csharp
public decimal ComputeTotal(Order order)
{
    decimal subtotal = order.Items.Sum(i => i.Price * i.Quantity);

    if (order.HasDiscount) // Fetch the discount flag from Order
    {
        subtotal *= 0.9m; // Apply discount if requested
    }

    return subtotal;
}
```
