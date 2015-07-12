---
layout: post
title: Open - Closed Principle
---

##The Open - Closed Principle, the `O` in the `SOLID` principles.

These are my notes from the `OCP: The Open-Closed Principle` chapter in the book `Agile Software Development: Principles, Patterns, and Practices` By Robert C. Martin (Uncle Bob).

```
Software entities should be open for extension, but closed for modification.
```

Entities in this case can mean a `module`, `class` or even `method.

What does open for extension actually mean?
The Behaviour can be extended and the module can be changed.

What does closed for modification mean?
Extending the behaviour does not result in changes to the source of the module.

How do we change the behaviour without changing the module?
`Abstraction is the key`

Abstraions are fixed and yet represent an unbounded group of possible behaviours. Abstrations are abstract base classes, unbounded group of possible behaviours is represented by all the possible derivitive classes.

Prefer polymorphisism to switch statements.
This means you can add derivitive classes to add more behaviours and it makes your design not as fragile or rigid.
There is no need to make changes at all the places with the switch statements. The polymorphisim will handle this with new derivitive classes.

### Bad design with Switch statements

Rigid - an addition of a new shape requires all the classes that have switch statements for the different behaviours to be recomplied.

Fragile - there can be many places where the switch statements are used, this can make it harder to make sure you change all of them.

Immobile - anyone using the switch statement needs to require all the files, even if they are not all used.

### Better design with polymorphism

Not rigid - no existing files need to be modified, expect the module that creates the derivitive classes.

Not fragile - no need to hunt for different areas for switch statements.

Not immobile - The common method can be reused without needing all the the derivite classes. Only the ones needed are included.

```There is no model that is natural to all contexts!```

Decide what kinds of changes you want to close you design to.
Most likely kinds of change?
Construct abstractions to protect these areas.

Conforming to the OCP is expensive.
- Development time and effort to creat appropriate abstractions.
- Abstractions increase complexity of the system.

How do we know which changes are likely?
- do appropriate research.
- ask appropriate questions.
- experience and common sense.
- After all that, we wait till it happens.

We don't want to load design with lots of unecessary abstractions.
Wait until we actually need abstractions, then put it in.

#### Fool me once
```we take the first bullet```
When change occurs, we implement abstractions to protect us from future changes.

#### Stimulate changes
How can we stimulate changes to help build abstractions?

- Test first. We have to build abstractions that make the system testable.
- Develop in short cycles, days instead of weeks.
- Develop features before infrastructure.
- Develop most important features first.
- Release early and often.
