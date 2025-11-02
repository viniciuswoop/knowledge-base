# Combine Functions into Transforms

## What It Is

**Combine Functions into Transforms** is a refactoring technique where multiple functions that each perform a small transformation on data are **combined into a single transformation pipeline or class**.  
This improves readability, reduces repetitive code, and enforces a clear flow of data transformations.

## Motivation

- **Code Readability**  
  Combining transformations into a clear pipeline or class makes it easier to understand how data flows through each step.

- **Code Complexity**  
  Enforce separation of concerns by centralizing transformation logic, reducing scattered and redundant operations.

- **Maintainability and Extensibility**  
  Adding new transformations or modifying existing ones is easier when all related operations are centralized.

- **Code Duplication**  
  Avoids repeating similar transformation logic across different parts of the codebase.

## When to Apply

- Multiple functions perform **small, sequential transformations** on the same data.  
- Transformation logic is **repeated or scattered** across the codebase.  
- You want to **clarify the flow of data** and reduce duplication.

## When Not to Apply

- Transformations are **unrelated or independent**, so combining them would reduce clarity.  
- The logic is **trivial or rarely used**, so combining adds unnecessary complexity.  

## Example in C#

Before refactoring (scattered transformation functions):

```csharp
public string NormalizeName(string name)
{
    return name.Trim().ToLower();
}

public string MaskEmail(string email)
{
    var parts = email.Split('@');
    return parts[0].Substring(0, 2) + "****@" + parts[1];
}

public string FormatUserInfo(string name, string email)
{
    var normalizedName = NormalizeName(name);
    var maskedEmail = MaskEmail(email);
    return $"{normalizedName} <{maskedEmail}>";
}

// Client usage
string name = " Alice ";
string email = "alice@example.com";
string userInfo = FormatUserInfo(name, email);
Console.WriteLine(userInfo);
```
After refactoring:
```csharp
public class UserTransformer
{
    private readonly User _user;

    public UserTransformer(User user)
    {
        _user = user;
    }

    private string NormalizeName()
    {
        return _user.Name.Trim().ToLower();
    }

    private string MaskEmail()
    {
        var parts = _user.Email.Split('@');
        return parts[0].Substring(0, 2) + "****@" + parts[1];
    }

    public string Transform()
    {
        return $"{NormalizeName()} <{MaskEmail()}>";
    }
}

// Client usage
var user = new User { Name = " Alice ", Email = "alice@example.com" };
var transformer = new UserTransformer(user);
string userInfo = transformer.Transform();
Console.WriteLine(userInfo);

