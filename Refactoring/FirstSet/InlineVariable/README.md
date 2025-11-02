# Inline Variable

## What It Is

**Inline Variable** is a refactoring technique where a **variable is replaced with its expression**.  
It is used when the variable adds no value to code clarity and can be safely removed without reducing readability.

## Motivation

- **Code Readability**  
  Simplifies the code by removing unnecessary indirection caused by trivial or redundant variables.

- **Code Complexity**  
  Reduces visual clutter when a variable is merely a placeholder for an obvious expression.

- **Maintainability and Extensibility**  
  Eliminates unneeded local state, reducing the number of moving parts to track during changes.

## When to Apply

- The variable **does not improve clarity** over the expression it stores.  
- The variable is **used only once**, and the expression is simple.  
- The variable was **introduced temporarily** during a refactoring and no longer serves a purpose.

## When Not to Apply

- The variable’s **name clarifies intent** better than the expression.  
- The expression is **complex** or **used multiple times**, in which case keeping a variable aids understanding and reduces duplication.  
- Inlining would **harm debugging or readability**, especially for multi-step calculations.

## Example in C#

Before refactoring:

```csharp
public bool IsCustomerEligible(Customer customer)
{
    var isAdult = customer.Age >= 18;
    return isAdult;
}
```
After refactoring:
```csharp
public bool IsCustomerEligible(Customer customer)
{
    return customer.Age >= 18;
}

