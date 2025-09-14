# Software Quality Aspects

The following software quality aspects directly impact the economic performance of companies, because software increasingly represents core business processes. Understanding these aspects and translating them into practical implementation drives engineering productivity, which in turn affects costs and enables faster adaptation to new requirements, fostering innovation.

## Maintainability & Extensibility

**What it is:**  
The degree to which a system can be efficiently modified to fix defects and add new features, without introducing unintended side effects or breaking existing functionality.

**Why it matters:**  
- **Software evolves**, requirements shift, bugs appear, and new features are requested. It’s the nature of software applications.  
- Maintainable code reduces the **cost and risk of change**, allowing teams to adapt quickly.  
- Extensible design enables **future growth**, so new functionalities can be integrated with minimal rework.  
- High maintainability **fosters engineers' productivity and team morale**, since the codebase is easier to understand and improve.  

**Key drivers:**  
- High **readability** - clear naming, consistent style (sometimes people get too attached and ignore good designs that matter the most), and straightforward logic.  
- **Low coupling** between components - minimizing interdependencies so changes in one module don't ripple across the system.  
- **Strong cohesion** within components - grouping related responsibilities together and avoiding "God classes".  
- Good **modular** boundaries - Defining clear interfaces and separation of concerns.  
- Adhere to **SOLID** principles - Principles that will guide implementation, aiming for maintainability and extensibility.  
- Comprehensive **automated tests** - ensuring safe refactoring and evolution.  

## Testability

**What it is:**  
The degree to which a software system or its components can be effectively and efficiently tested. In practice, it means how easily small units of the application can be tested in isolation, without requiring complex setup or dependencies.

**Why it matters:**  
- Enables **fast feedback** on code changes, allowing engineers to quickly run and debug small units of functionality.  
- Encourages writing **deterministic code**, where behavior is consistent and predictable under the same conditions.  
- Improves **confidence in changes**, since tests act as a safety net during refactoring or feature development.  
- Reduces the **cost of defects**, as issues are discovered earlier in the development cycle.  

**Key drivers:**  
- **Modularity** - designing software as independent, loosely coupled components.  
- Inversion of Control **(IoC)** & Dependency Injection **(DI)** - making dependencies explicit and replaceable, which facilitates mocking and stubbing.  
- Single Responsibility Principle **(SRP)** - ensuring each class or function has one well-defined purpose, reducing hidden behaviors that complicate tests.  

## Code Readability

**What it is:**  
The ease which someone - not just the original author - can read, understand, and reason about the code. Readability comes primarily **from good design decisions, not just formatting rules**.

**Why it matters**:
- Engineer's spend far more time **reading code than writing it**.
- Readable code lowers the learning curve, making onboarding and collaboration smoother.
- Clarity reduces mistakes, since intent is easier to follow and misunderstandings are minimized.
- Focusing on **design and structure first** ensures readability that lasts, whereas style alone only polishes the surface.

**Key drivers**:
- **Clear naming** - variables, functions and classes that reveal intent.
- **Small, focused functions and classes** - each doing one thing well, which makes behavior easy to follow.
- **Good modular design** - well defined boundaries and responsibilities, making navigation intuitive.
- **Minimal "surprise" behavior** - code should behave as its name and structure suggest
- **Consistent formatting and style** - helps, but always in service of the underlying design.
