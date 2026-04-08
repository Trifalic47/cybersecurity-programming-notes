---
id: shiftOperators
aliases: []
tags: []
---

---

# About Shift Operators

    C also provides a set of shift operations for shifting bit patterns to the left and to
    the right. For an operand x having bit representation [xw−1, xw−2, . . . , x0], the C
    expression x << k yields a value with bit representation [xw−k−1, xw−k−2, . . . , x0,
    0, . . . , 0]. That is, x is shifted k bits to the left, dropping off the k most significant
    bits and filling the right end with k zeros. The shift amount should be a value
    between 0 and w − 1. Shift operations associate from left to right, so x << j << k
    is equivalent to (x << j) << k.
    There is a corresponding right shift operation, written in C as x >> k, but it has
    a slightly subtle behavior. Generally, machines support two forms of right shift:
    Logical. A logical right shift fills the left end with k zeros, giving a result
    [0, . . . , 0, xw−1, xw−2, . . . xk].
    Arithmetic. An arithmetic right shift fills the left end with k repetitions of the
    most significant bit, giving a result [xw−1, . . . , xw−1, xw−1, xw−2, . . . xk].
    This convention might seem peculiar, but as we will see, it is useful for
    operating on signed integer data.

> [!note] Read more about the shift operators in the CS:APP book on page 93 and 94.

---

# Next Topic

Now lets move on to the next topic which is [[integerRepresentation]]
