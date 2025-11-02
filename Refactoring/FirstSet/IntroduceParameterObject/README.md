# Introduce Parameter Object

## What It Is

**Introduce Parameter Object** is a refactoring technique where a group of parameters that are frequently passed together to methods is **encapsulated into a single object**.  
This simplifies method signatures, improves readability, and centralizes related data.


## Motivation

- **Code Readability**  
  Long or repetitive parameter lists are simplified, making method calls easier to understand.

- **Code Complexity**  
  Encapsulating related parameters reduces cognitive load and simplifies method maintenance.

- **Maintainability and Extensibility**  
  Changes to the set of parameters require modifying only the parameter object instead of updating every method signature.



## When to Apply

- A method has **many parameters** (especially 5 or more).  
- The same group of parameters is **passed together to multiple methods**.  
- You want to **simplify method signatures** and centralize related data.  


## When Not to Apply

- Parameters are **independent or unrelated**, so encapsulating them adds unnecessary abstraction.  
- The method is **short-lived or trivial**, and creating a new object would overcomplicate the design.  
- The parameter object would be **used only once**, offering minimal value.


## Example in C#

Before refactoring:

```csharp
public class OrderService
{
    public void CreateOrder(string customerName, string customerEmail, string address, DateTime orderDate, decimal totalAmount)
    {
        // Order creation logic
    }
}
```
After refactoring:
```csharp
public class CustomerInfo
{
    public string Name { get; set; }
    public string Email { get; set; }
    public string Address { get; set; }
}

public class OrderDetails
{
    public CustomerInfo Customer { get; set; }
    public DateTime OrderDate { get; set; }
    public decimal TotalAmount { get; set; }
}

public class OrderService
{
    public void CreateOrder(OrderDetails orderDetails)
    {
        // Order creation logic
        // Access customer info via orderDetails.Customer
    }
}
