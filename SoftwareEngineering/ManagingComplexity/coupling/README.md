# Managing Coupling  

Coupling is the degree of dependency between modules or components in a system. High coupling increases the cost of change, because modifications in one module can ripple across the system, causing unexpected side effects, bugs, and additional maintenance overhead. Low coupling reduces this cost, making the system more maintainable, testable, and adaptable.  

Completely removing coupling is impossible, because modules must communicate to deliver functionality. The goal is to **aim for loose coupling**, relying on well-defined contracts and interfaces to mediate interactions. This ensures that modules remain independent while still collaborating effectively, minimizing the impact of changes.  

Managing coupling complements modularity, cohesion, separation of concerns, and information hiding. By controlling dependencies, engineers can maintain flexibility, testability, and resilience in the system.  

## Why it matters  
- Supports maintainability: low-coupled modules can be modified independently.  
- Reduces risk: changes in one module are less likely to break other parts of the system.  
- Enhances testability: modules can be tested in isolation without complex setup.  
- Facilitates parallel development: teams can work on different modules without interfering with each other.  
- Improves readability: a well-decoupled system is easier to understand because interactions are explicit and limited.  

## Key drivers  
- **Explicit interfaces**: communicate between modules through well-defined contracts.  
- **Dependency Injection**: provide dependencies from the outside rather than having modules instantiate them internally.  
- **Information hiding**: hide internal details to reduce unnecessary dependencies.  
- **Single responsibility and cohesion**: tightly related responsibilities reduce the need for cross-module interactions.  
- **Modularity**: independent modules naturally reduce coupling when responsibilities are properly separated.  
- **APIs and Event Communication**: enable loose coupling at a higher level by allowing services or systems to interact through defined contracts.  
