# Information Hiding and Abstraction  

## What it is  
Information hiding is the principle of concealing the internal details of a module, class, or component, exposing only what is necessary through well-defined interfaces. Abstraction is the process of focusing on essential characteristics while ignoring irrelevant details.  

Together, these practices help reduce complexity, enforce modularity, and ensure that changes to internal implementation do not ripple across the system. Information hiding specifically **avoids external interference on internal behavior**, which is critical when approaching changes in the application: engineers can modify internal logic safely without breaking other modules that depend on it. Abstraction and information hiding also **play a key role in establishing clear interfaces with external clients**, allowing other modules or systems to interact with a component without knowing or depending on its internal implementation. Engineers can focus on what the component does, not how it does it.  

## Why it matters  
- Supports maintainability: internal changes can be made without affecting external code that relies on the module.  
- Enhances testability: tests can focus on observable behavior rather than implementation details.  
- Reduces coupling: other modules interact with the abstraction rather than the concrete implementation.  
- Improves readability: engineers can understand and use a module without needing to know its internal complexity.  
- Facilitates extensibility: new implementations can replace existing ones as long as they adhere to the same abstraction.  

## Key drivers  
- **Well-defined interfaces**: only expose what is necessary for other modules to interact with the component.  
- **Encapsulation**: keep internal data and logic private to the module.  
- **Use of abstract types or contracts**: define behavior without revealing implementation details.  
- **Consistent abstraction levels**: avoid mixing high-level and low-level details in the same module.  
- **Alignment with modularity and SoC**: abstractions enforce boundaries and clarify responsibilities.  
