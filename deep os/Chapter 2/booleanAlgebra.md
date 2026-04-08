---
id: booleanAlgebra
aliases: []
tags: []
---
---
# Meaning

*Boolean algebra is an branch of mathematics dealing with only two values 0 and 1.And as well all know binary also contains 0 and 1 which is
also called `base2`.*

        The Boolean operation ~ corresponds to the logical
        operation not, denoted by the symbol ¬. That is, we say that ¬P is true when
        P is not true, and vice versa. Correspondingly, ~p equals 1 when p equals 0, and
        vice versa. Boolean operation & corresponds to the logical operation and, denoted
        by the symbol ∧. We say that P ∧ Q holds when both P is true and Q is true.
        Correspondingly, p & q equals 1 only when p = 1 and q = 1. Boolean operation
        | corresponds to the logical operation or, denoted by the symbol ∨. We say that
        P ∨ Q holds when either P is true or Q is true. Correspondingly, p | q equals
        1 when either p = 1 or q = 1. Boolean operation ^ corresponds to the logical
        operation exclusive-or, denoted by the symbol ⊕. We say that P ⊕ Q holds when
        either P is true or Q is true, but not both. Correspondingly, p ^ q equals 1 when
        either p = 1 and q = 0, or p = 0 and q = 1

---

# Use in Coputer Programming

`We could extend this boolean operations to also operate on bit vectors(a string of 0 and 1 with a fixed length).`

We could use the bitwise operators in the programming languages like C and many other but we will focus on the C and assembly mainly on this
learning course.We use the operators like the `&`,`|`,`~` and `^`.These compares the variables on the bases of their binary value not on the
basis of their printing value which means that they compares on their `base2` values not the `ASCII`.

![[booleanArith1.png]]

---

# Next Topic

Now lets move to the next topic which is [[shiftOperators]]
