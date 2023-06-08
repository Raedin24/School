To create an instance of a class
```Java
class Primitives{...}

Pirmitives <Circle> p = new Primitives<Circles>();
```
- With *infix*, the operator is in between the 2 operands
- With *postfix* expressions, the operator follows the 2 operands
$$
(3 * 4 - (2 + 5)) * 4 / 2
$$
$$
(3 * 4 - (7)) * 4 / 2
$$
$$
(12 - 7) * 4 / 2
$$
$$
5 * 4/2
$$
$$
20 / 2
$$
$$
10
$$
**Evaluating Postfix Expressions (Using Stacks)**
- Scan the expression from left to right
- When an operand is encountered, push it to the stack
- When an operator is encountered, pop the top 2 elements and perform the operation
- Push result on the stack

> Package name : Surname + last 4 digits of id

- An array is of a fixed size once defined
- To expand capacity, create a larger array and copy elements from first array

