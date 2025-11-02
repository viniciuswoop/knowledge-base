# Encapsulate Variable

## What It Is

**Encapsulate Variable** is a refactoring technique where a **variable’s access is controlled**, typically by making it private or providing limited modification methods, instead of allowing unrestricted direct changes.  
This allows controlled access to the variable, protecting it from unwanted modifications and enforcing invariants.

## Motivation

- **Maintainability and Extensibility**  
  Centralizing the data manipulation logic helps to enforce business rules when modifying it and prevent undesirable data manipulation from clients.

- **Code Readability**  
  Client interaction is clear and communicates intention.

- **Testability**  
  Object becomes more testable as object enforces business rules by its own.


## When to Apply

- The variable is **public or widely accessed** directly.  
- You need to **control or validate modifications** to the variable.  
- You want to **hide implementation details** and provide a stable interface for clients.

## When Not to Apply

- The variable is **already private** and used only internally.  
- Introducing getters/setters adds **unnecessary boilerplate** without improving clarity or control.  
- The variable is **trivial and unlikely to change**, so encapsulation provides minimal benefit.

## Example in C#

Before refactoring:

```csharp
public class BankAccount
{
    public decimal Balance;
}

public class Program
{
    public static void Main()
    {
        var account = new BankAccount();
        account.Balance = 1000;
        account.Balance += 200;
        Console.WriteLine(account.Balance);
    }
}
```
After refactoring:
```csharp
public class BankAccount
{
    public decimal Balance { get; private set; }

    public void Deposit(decimal amount)
    {
        if (amount <= 0)
            throw new ArgumentException("Deposit must be positive.", nameof(amount));

        Balance += amount;
    }

    public void Withdraw(decimal amount)
    {
        if (amount <= 0)
            throw new ArgumentException("Withdrawal must be positive.", nameof(amount));

        if (amount > Balance)
            throw new InvalidOperationException("Insufficient funds.");

        Balance -= amount;
    }
}

public class Program
{
    public static void Main()
    {
        var account = new BankAccount();
        account.Deposit(1000);
        account.Deposit(200);
        Console.WriteLine(account.Balance);
    }
}

```
