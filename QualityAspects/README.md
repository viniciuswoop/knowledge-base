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

## Complexity

**What it is**:  
The measure of how difficult code is to understand, reason about, and change. Complexity comes in two main flavors:
- **Accidental complexity**: Complexity introduced by poor design, unnecessary abstractions, duplication, or unclear naming.
- **Essential complexity**: Complexity inherent in the problem domain that cannot be avoided. (tax rules, distributed systems)

**Why it matters**:
- Directly affects **readability** (harder to parse and follow)
- Increases the cost of maintenance (small changes risk unintended consequences)
- Reduces **reusability** (complex code is harder to lift into other contexts)
- Makes achieving **consistency** and **modularity** harder, since complex components tend to sprawl accross responsibilities.

**Key drivers**
- Too many nested conditionals or loops.
- Overuse of inheritance or deep hierarchies.
- Large classes or functions with multiple responsibilities.
- Hidden dependencies between modules.

## Code Duplication

**What it is**:  
The extent to which the same logic or structure is repeated across the codebase. Duplication can be exact (copy-paste code) or conceptual (slightly different implementations of the same idea and purpose.)

**Why it matters**: 
- **Increases maintenance cost** - a change in one place often requires updates in multiple places.
- **Invites inconsistency** - when similar pieces of code evolve differently, subtle bugs and contradictions appear and are hard to find.
- **Slows down development** - developers spend more time hunting for all the spots that need to change.
- **Reduces clarity** - duplicated code hides intent, making it harder to understand where the "real" logic lives.

**Key drivers**
- **Copy-paste culture** - quick fixes under pressure instead of proper design.
- **Lack of shared libraries** - engineers reimplement the same logic because no common solution exists.
- **Poor modular design** - tightly coupled code that makes reuse difficult, encouraging repetition.
- **Lack of application structure** - unclear boundaries and inconsistent layering lead developers to duplicate logic rather than navigate existing code.
- **Knowledge silos** - different teams or individuals solving the same problem without awareness of existing solutions.
- **Lack of accountability** - unclear ownership of modules or components allows duplication to go unnoticed or unchallenged.
- **Short-term optimization mindset** - prioritizing speed of delivery over long-term maintainability.
- **Fear of breaking changes** - developers duplicate instead of reusing existing code to avoid unintended side effects.
