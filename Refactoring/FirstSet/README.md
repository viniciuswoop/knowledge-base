# First Set of Refactorings

Refactoring is most effective when approached systematically.  
The **first set of refactorings** are practical, widely applicable techniques that are used to address the most common code smells.  
They are **high-leverage tools** — simple to apply, but they significantly improve readability, maintainability, and overall code quality.

These foundational refactorings are the building blocks for more complex transformations.  
Mastering them ensures that future refactoring becomes faster, safer, and less risky.

> While these refactorings are powerful tools to **remove code duplication, improve maintainability, and enhance extensibility**, they are **not free**. Each change carries trade-offs, such as added complexity, consistency, modularity, and dependencies. Always weigh the benefits against potential costs before applying them.

## Why These Refactorings Are Important

1. **Address Common Smells**  
   Each of these refactorings directly targets frequent code issues such as long methods, unclear names, or convoluted logic.

2. **Improve Code Readability**  
   Refactorings clarify intent and structure, making it easier for developers to understand and work with the code.

3. **Remove Code Duplication**  
   Consolidating repeated code reduces maintenance overhead, prevents inconsistencies, and makes future changes safer.

4. **Improve Maintainability and Extensibility**  
   By clarifying structure, responsibilities, and dependencies, refactorings make the code easier to modify, extend, and integrate with new features.

## First Set of Refactorings

- [**Extract Function / Method**](./ExtractMethod/README.md)  
- [**Inline Function**](./InlineMethod/README.md)  
- [**Extract Variable**](./ExtractVariable/README.md)  
- [**Inline Variable**](./InlineVariable/README.md)
- [**Change Function Declaration**](./change-function-declaration.md)
- [**Encapsulate Variable**](./encapsulate-variable.md)
- [**Rename Variable**](./rename-variable.md)
- [**Introduce Parameter Object**](./introduce-parameter-object.md) 
- [**Combine Functions into Class**](./combine-functions-into-class.md)  
- [**Combine Functions into Transforms**](./combine-functions-into-transforms.md) 
- [**Split Phase**](./split-phase.md)
