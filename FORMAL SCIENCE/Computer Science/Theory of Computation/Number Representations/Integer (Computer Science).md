In [[Number Representations (Computer Science)|number representations of computer science]], integers are values that are defined as a set size of byte. The most common integers are 32 bits long without signs, or `unsigned int`/`uint32_t` in C; In the modern day, integers are 64 bits long. These data types can only represent the set of [[Integer|integers]].

Smaller objects exist - In C, `char` is an 8-bit unsigned integer; `short` is a 16-bit unsigned integer. There may even be 2-bit integers or 1-bit integers.

Integers are prone to overflow errors - Since numbers have to be stored in fixed sizings, when certain operations exceed that space, they overflow. For instance, with 2-bit integers, `01 + 10 = 11`, which corresponds to $1+2=3$. However, the addition of `11 + 01 = 00`, which corresponds to $3+1=0$. This causes obvious problems.

## Operations

The following basic operations occur for integers:

- Addition: Integers can be added together. Upon being summed, they may overflow.
- Subtraction: Integers can be subtracted from one another. This can cause underflow.
- Multiplication: Integers can be multiplied together. Usually, the output should be the sum of the space designated for the two operands: Multiplying two 4-bit numbers should require 8 bits of space.
- Division: Integers can be divided, but usually this is done with more complicated algorithms.
- Shifting: Integers can be rotated or shifted. For shifting an integer, this refers to removing the most significant bit, then rotating, and appending a `0`. So, `01101 << 1 = 11010`.

## Signed Integers

### One's Complement

The naïve implementation of representing negative numbers is to simply take the most significant bit and use it as a 'sign' bit. For instance, `10110` would go from $22$ to $-6$. However, this becomes problematic, as `$10000` corresponds to $-0$, which has no semantic meaning. Other problems with this system occur in mathematics: `001 + 011 = 100`, or $1 + 3 = -0$.

### Two's Complement

A better system is two's complement, a mathematical operation to reversibly convert a positive binary number into a negative binary number with equivalent value. The algorithm is as follows:

1. Start with the equivalent positive number's binary representation. For some value to represent $x$, start with $bin(|x|)$.
2. Flip all bits, inverting them. So, compute $\neg bin(|x|)$.
3. Add $bin(1)$ to the entire inverted number and ignore any overflow.

As such, converting a number to its negative counterpart in two's complement is simply computing:

$$-x = \neg bin(|x|) + bin(1)$$

Let's take a number: $-23$. Going through the procedure:

|#|Description|Value|
|-----|-------------|------|
|1.|Start with the value. |`0b010111`|
|2.|Flip all bits.|`0b101000`|
|3.|Add $bin(1)$, ignoring overflow.|`0b101001`|

Thus, the value $-23$ is `0b101001` in binary. We can return back to positive notation by following the same procedure!

|#|Description|Value|
|---|---|---|
|1.|Start with the value.|0b101001|
|2.|Flip all bits.|`0b010110`|
|3.|Add , ignoring overflow.|`0b010111`|

We've returned back to the same value.