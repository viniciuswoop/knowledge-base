# Encapsulate Variable

## What It Is

**Encapsulate Variable** is a refactoring technique where a **variable’s access is controlled**, typically by making it private or providing limited modification methods, instead of allowing unrestricted direct changes.  
This allows controlled access to the variable, protecting it from unwanted modifications and enforcing invariants.

## Motivation

- **Code Readability**  
  Meaningful names make code easier to understand at a glance.

- **Code Complexity**  
  Clear names reduce cognitive load and prevent misinterpretation of a variable’s role.

- **Maintainability and Extensibility**  
  Well-named variables make it easier to update and extend code without introducing errors.

- **Code Duplication**  
  Using consistent and descriptive names helps prevent creating duplicate variables or concepts unnecessarily.

- **Testability**  
  Clear variable names make tests more understandable and reduce the chance of misinterpreting test behavior.


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
