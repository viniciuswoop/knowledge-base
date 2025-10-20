# Bad Smells in Code

Bad smells are **patterns that indicate potential design or structural problems** in code.  
They are not bugs — the program works — but they suggest that **something may need refactoring** to improve readability, maintainability, or extensibility.

Learning to recognize these smells is one of the most valuable skills in software development.  
Each smell points to a potential refactoring opportunity.

## Mysterious Name
Poorly named functions, variables, or classes make code harder to understand.  
Good names clearly communicate intention — *what* the code does and *why* it exists.

## Duplicated Code
Repetition forces careful examination to see if differences are intentional or accidental.  
Consolidate duplicated logic into a single place to improve maintainability.

## Long Function
Long, complex functions are difficult to understand, test, and reuse.  
Break them down into smaller, focused functions that do one thing well.

## Long Parameter List
Although better than using global variables, long parameter lists are often confusing.  
Consider grouping related parameters into a class or record to simplify method signatures.

## Global Data
Global and mutable data can be changed from anywhere, making tracking changes difficult.  
Restrict visibility and encapsulate state whenever possible.

## Mutable Data
Mutation increases the risk of bugs, especially when variables have wide scope.  
Favor immutability where practical to make code easier to reason about.

## Divergent Change
Occurs when a single module must be changed in many ways for different reasons.  
Each change affects unrelated behaviors, suggesting the module has too many responsibilities.

## Shotgun Surgery
When a single change requires small edits across many classes or modules, the system lacks proper encapsulation.  
Group related behavior together to localize future changes.

## Feature Envy
A method that interacts more with another class than with its own indicates misplaced behavior.  
Move the method to the class it seems most interested in.

## Data Clumps
Groups of data items that often appear together — as parameters or fields — suggest they should be encapsulated in their own class or record.

## Primitive Obsession
Overuse of primitive types (like strings or integers) instead of domain-specific abstractions.  
Examples include using `string` for phone numbers or `decimal` for money.  
Replace primitives with small, meaningful types that express intent.

## Repeated Switches
Repetitive conditional logic scattered across code is error-prone.  
Replace with polymorphism or strategy patterns for cleaner, extensible design.

## Loops
Modern languages offer expressive operations like `map`, `filter`, and `reduce` that make intent clearer than manual loops.  
Prefer declarative pipelines for better readability.

## Lazy Element
Code or structure added in anticipation of future needs but rarely used in practice.  
Remove unused or unnecessary abstractions to keep the codebase lean.

## Temporary Field
Instance variables that are only relevant in specific contexts confuse readers.  
Use local variables or smaller helper objects instead.

## Message Chains
Occurs when code calls a series of methods like `a.getB().getC().doSomething()`.  
This exposes internal structure and creates tight coupling.  
Introduce intermediary methods to hide the chain.

## Insider Trading
Modules that access another’s internals too often indicate poor encapsulation.  
Introduce clearer boundaries or a mediator module to separate concerns.

## Large Class
Classes that handle too many responsibilities should be split into smaller, focused ones.  
Use **Extract Class** or **Extract Module** refactorings to improve cohesion.

## Data Class
Classes that only hold data but have no behavior (anemic models) often indicate misplaced logic.  
Move relevant behavior into the data class or related domain types.

## Refused Bequest
A subclass inherits behavior it doesn’t use.  
This signals a flawed inheritance structure — consider composition or interface extraction instead.

## Comments
Comments that exist solely to explain confusing code indicate a deeper issue.  
Refactor to make the code self-explanatory — name things clearly and simplify logic instead of relying on comments.
