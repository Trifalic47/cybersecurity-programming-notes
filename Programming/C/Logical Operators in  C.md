---
tags:
  - c
  - c-programming
  - operators
  - logical-operators
aliases:
  - C logical operators
created: 2025-01-28
---
# Logical Operators in C

Logical operators combine or negate conditions (usually from relational expressions).

## The Three Logical Operators

| Operator | Symbol | Name          | Type  | True when                                      | Short-circuit? |
|----------|--------|---------------|-------|------------------------------------------------|----------------|
| AND      | `&&`   | Logical AND   | binary| **both** operands true                         | Yes            |
| OR       | `||`   | Logical OR    | binary| **at least one** operand true                  | Yes            |
| NOT      | `!`    | Logical NOT   | unary | operand is **false**                           | No             |

## Truth Tables

### AND (`&&`)


## Most Important Feature: Short-circuit Evaluation

- `&&` → if left is **false** → right side is **not evaluated**
- `||`  → if left is **true**  → right side is **not evaluated**

```c
// Prevents division by zero
if (x != 0 && 100 / x > 10) { ... }

// Safe pointer check
if (ptr && *ptr > 0) { ... }
```

***
## Precedence Reminder
```
!     highest
&&    medium
||    lowest
```

## Quick Cheat Sheet

```
You want...                          → Operator(s)
───────────────────────────────────────────────
Both / all conditions true           → &&
At least one true                    → ||
None are true                        → !  or  == 0
Invert a condition                   → !
Prevent evaluating dangerous code    → &&   or   ||
```