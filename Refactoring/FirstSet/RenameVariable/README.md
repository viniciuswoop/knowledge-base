# Rename Variable

## What It Is

**Rename Variable** is a refactoring technique where a variable’s name is changed to better reflect its purpose or meaning.  
The behavior of the code remains unchanged, but the new name improves clarity, reduces confusion, and helps enforce consistent usage.

## Motivation

- **Code Readability**  
  Meaningful names communicate intent at a glance, making code easier for developers to understand and maintain.



## When to Apply

- Variable names are **ambiguous, misleading, or too generic** (e.g., `temp`, `val`, `data`).  
- Variable names do **not match their purpose or context**.  
- You want to **improve consistency** across related variables or classes.

## When Not to Apply

- Variable names are **already clear and descriptive**.  
- Renaming would **confuse existing team members** without adding value.  
- Variable is **short-lived and trivial**, where a longer name might reduce readability.


## Example in C#

Before refactoring:

```csharp
public class Order
{
    public decimal val;
    
    public void PrintTotal()
    {
        Console.WriteLine($"Total: {val}");
    }
}
```
After refactoring:
```csharp
public class Order
{
    public decimal TotalAmount;
    
    public void PrintTotal()
    {
        Console.WriteLine($"Total: {TotalAmount}");
    }
}

```
