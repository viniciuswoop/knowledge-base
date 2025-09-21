# Cohesion  


Cohesion is the degree to which the elements inside a module, class, or function belong together and contribute to a single, well-defined purpose. A highly cohesive component focuses on one responsibility, while low cohesion often indicates scattered, unrelated, or conflicting responsibilities grouped together.  

Cohesion drives good modularity: while modularity defines boundaries between components, cohesion ensures that what’s inside those boundaries makes sense as a unit. It also acts as a thermometer that warns when a modular unit is taking on too many responsibilities and drifting away from its original intent.  

## Why it matters  
- Improves readability: cohesive modules are easier to understand because their responsibilities are clear.  
- Supports maintainability: changes affect fewer parts of the system, reducing unintended side effects.  
- Enhances testability: cohesive components are simpler to test in isolation since their behavior is well-defined.  
- Reinforces extensibility: new features can often be added by extending cohesive modules without rewriting unrelated code.  

## Key drivers  
- **Single Responsibility Principle (SRP)**: each class or function should have only one reason to change.  
- **Focused design**: responsibilities are grouped logically, avoiding “God classes” or catch-all components.  
- **Clear purpose**: each module should have a name and interface that communicate its responsibility unambiguously.  
- **Separation of concerns**: responsibilities are not mixed across modules but isolated within the right boundaries.  
