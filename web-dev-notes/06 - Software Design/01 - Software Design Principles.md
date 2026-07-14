# Software Design Principles

## Introduction to Software Design

**Software design** plans how application code fits and works together — using flowcharts, UML diagrams, interface descriptions, design patterns, and other tools.

**Software architecture** = design of the whole system. Key questions:

- How will we organize our software?
- How will the parts talk with each other?
- How will we move and store the data?

### Designing for Change

Factors that help a system adapt to change:

- Each part has a **clear purpose**
- Things most likely to change are **separated** from the rest
- Classes have a **clear way of interacting**
- System uses **standard design patterns and practices**

> Example: unsure which database you'll use? Keep database code interactions separate from the rest of the system.

### General Rules of Thumb

|Rule|Meaning|
|---|---|
|**YAGNI** — You Aren't Gonna Need It|Don't build features you don't need yet|
|**KISS** — Keep It Simple, Silly|Avoid unnecessary complexity|
|**DRY** — Don't Repeat Yourself|Single source of truth — no duplicated logic|

> DRY shouldn't be over-applied — only optimize/abstract where repetition actually causes problems.

---

## OOP & UML

### The 4 Pillars of OOP

|Pillar|Meaning|
|---|---|
|**Abstraction**|Hide low-level details, expose only the "big picture"|
|**Encapsulation**|Object manages its own internal state, exposes only behaviors|
|**Inheritance**|Child object inherits shared characteristics from parent|
|**Polymorphism**|Child class can override/redefine inherited behavior|

### UML Class Diagram

Describes an object at a high level — no implementation details.

```
Class Name
----------
Attributes
----------
Methods
```

### System Diagrams

Show how components relate at a bird's-eye view.

```
Website → Server → Database → Server → Website
```

Example: Website receives user request → forwards to Server → Server queries Database → Database returns data → Server packages response → Website displays it.

---

## SOLID Principles

5 OOP design guidelines for easy-to-change, understandable, reusable software.

|Letter|Principle|Meaning|
|---|---|---|
|**S**|Single Responsibility|A class should have only **one reason to change**|
|**O**|Open-Closed|Open for **extension**, closed for **modification**|
|**L**|Liskov Substitution|A subclass should be swappable for its parent without breaking anything|
|**I**|Interface Segregation|Interfaces should only have methods **all** subclasses actually use|
|**D**|Dependency Inversion|Classes should depend on **abstractions/interfaces**, not concrete classes|

### Single Responsibility Example

Instead of one bloated `Enemy` class handling everything:

```
EnemyBehavior  → attacking, taking damage
EnemyState     → health, type info
EnemyStorage   → database storage
EnemyDisplay   → rendering on screen
```

### Open-Closed Principle

Add functionality via **new classes**, not by editing existing ones.

### Liskov Substitution Example

```
Pet (parent)
├── Dog
├── Cat
└── Turtle
```

Any code using `Pet` should work seamlessly with `Dog`, `Cat`, or `Turtle` — no special-casing needed.

### Interface Segregation

Don't force subclasses to implement methods they don't use — split into smaller, more specific interfaces instead.

### Dependency Inversion

Classes should interact with **interfaces**, not concrete implementations — makes the system more flexible and supports Open-Closed + Interface Segregation.

> SOLID principles reinforce each other — they're not independent guidelines.

---

## Design Patterns

**Design patterns** = reusable solutions to common software organization problems.

### 3 Main Types

|Type|Purpose|Example Pattern|
|---|---|---|
|**Creational**|Hides object creation logic from clients|Singleton|
|**Structural**|Combines objects into larger structures|Bridge|
|**Behavioral**|Defines how objects interact with each other|Observer|

### Singleton (Creational)

Ensures only **one instance** of a class exists (e.g. a database connection) — no need to re-pass credentials/setup everywhere.

### Bridge (Structural)

Replaces exploding subclass hierarchies (`RedRectangle`, `BlueRectangle`, `RoundedBlueRectangle`...) with **object composition** instead of inheritance — turn the varying dimension into its own class, and use it as an attribute.

### Observer (Behavioral)

Lets objects "listen" for events (e.g. notify when a field changes) — add new listeners without modifying the source object.

### When to Use Design Patterns

✅ When solving a problem the pattern is specifically meant to solve ✅ When a part of the system is likely to change repeatedly

❌ Don't overuse them everywhere — that overcomplicates things ❌ Not chosen "before development begins" — chosen when the actual need/problem arises

---

## Model View Controller (MVC)

Architectural pattern for applications that move data, display UI, and let user actions change data.

|Component|Responsibility|
|---|---|
|**Model**|Data storage & representation objects|
|**View**|What the user sees (UI/presentation — React components, HTML, XML)|
|**Controller**|The "brain" — receives events, talks to Model, updates View|

### Example — Fun Fact Website

```
User clicks button (View)
        ↓
Controller receives event
        ↓
Controller requests new fact from Model
        ↓
Controller sends fact back to View
        ↓
View displays it
```

### Benefits

- Data, logic, and presentation are **separated** — modify independently
- Multiple Views (web + mobile) can share the **same Controller**

### Drawbacks

- Adds **unnecessary complexity** for simple apps
- Best for **larger, team-based, or complex** projects, not small ones

---

## Quick Reference

```
YAGNI → Don't build unneeded features
KISS  → Keep it simple
DRY   → Single source of truth

OOP Pillars:
Abstraction    → hide details
Encapsulation  → manage own state
Inheritance    → share parent behavior
Polymorphism   → override parent behavior

SOLID:
S → Single Responsibility (one reason to change)
O → Open-Closed (extend, don't modify)
L → Liskov Substitution (subclass swappable for parent)
I → Interface Segregation (no unused methods)
D → Dependency Inversion (depend on abstractions)

Design Pattern Types:
Creational  → object creation (Singleton)
Structural  → combining objects (Bridge)
Behavioral  → object interaction (Observer)

MVC:
Model      → data
View       → UI
Controller → logic/behavior
```

---

## Related

- [[../02 - JavaScript/08 - Classes & OOP]]
- [[../05 - Backend/04 - Express.js]]