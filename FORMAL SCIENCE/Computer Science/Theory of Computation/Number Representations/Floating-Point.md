A floating-point number is a [[Number Representations (Computer Science)|numerical representation]] that can represent [[Real Number|real numbers]]. Unlike fixed-point decimal numbers (which have a certain number of bits for fractional portions), the floating point number does not have a fixed number of bits allocated for fractions (and thus, may 'float.')

## IEEE 754 Standard

The most common standard for floating-point is IEEE 754, which represents floating point numbers in scientific notation. It consists of two parts:

- The *sign* $s$ is the singular bit representation of positive or negative factor.
- The *mantissa* $M$, also known as the significand, is the binary representation of the fractional portion.
- The *exponent* $E$, also known as the characteristic or scale, modifies the magnitude of the number.

The numerical form can be represented as:

$$
F=(-1)^s \times M \times 2^E
$$

Usually, the encoding is reversed - The sign bit is most significant, followed by the exponent field, followed by the mantissa. The IEEE 754 standard for 32-bit floating point numbers `float32` contains 1 sign bit, then 8 exponent bits, and finally 23 fractional bits. For 'double-precision' `double` floating points, different sizings are specified.

The exponent is coded as a biased value:

$$
E = E' - B = E' - (2^{k-1} - 1)
$$

This is defined where $E'$ is the original exponent field's unsigned value, and $k$ is the number of exponent bits. For single precision, this means our bias $b$ (the parentheses portion) is 127.

## Normalization

Close to 0, the floating point numbers are considered 'denormalized' and are relatively dense. However, as magnitude is increased, precision is lost in the 'normalized' range.

This leads to the concept of $\infty$ and $-\infty$, as IEEE mathematics 'saturate.' We have special implementations for these values.

There are values of $+0$ and $-0$, which are equivalent in value. These are implemented simply. $\infty$ and $-\infty$ are encoded with all `1` values in exponents and all $0$ in fractional bits.

## Rounding

Generically, fractional points are rounded to the nearest even. However, rounding can easily be checked as follows:

`1.1010010`

If we need to round this to 3 binary points, we notice we can simply check the fourth position, and (by definition) that refers to 'half' of the third binary point.

```
1.1010010
     ^
     < 0.5 -> Round down
```

Similarly, `1.1011010` rounds upwards to `1.110`. If we have `1.1111100`, we can simply round `10.000`.

What about `1.0011000`? We notice that we can either round to `1.001` or `1.010`. In this case, we simply choose the rounded value with a `0` - So, `1.010`.

## Examples

### Encoding

Suppose we want to convert the number $84.125$ into IEEE 754 single-precision sizing.

Let's start with the whole number portion. Performing some whole number division, we can generate the following table:

|Division|Result|Remainder|
|---|----|----|
|84/2|42|0|
|42/2|21|0|
|21/2|10|1|
|10/2|5|0|
|5/2|2|1|
|2/2|1|0|
|1/2|0|1|

Now we can read the remainder from bottom to top: `0b1010100`. What about the decimal portion?

|Multiplication|Result|Whole-number portion|
|----|-----|----|
|$0.125\times 2$|0.25|0
|$0.25\times 2$|0.5|0|
|$0.5\times 2$|1|1|
|$0\times 2$|0|0|

Notice we subtract the whole-number portion each time, and stop at $0.0$. Now we can read `0b0010` from top to bottom.

Now we can simplify - Our number in binary is simply `1010100.001`. Now we can shift this over:

`1.010100001` $\times 2^6$

Since the number is positive, our sign bit is `0`. Since exponents are coded via bias, we need to add `127` to our exponent value `6` to get `133`. or `0b10000101`. Finally, our mantissa goes in easily as `010100001`. We remove our original `1` on the whole-number side as it's implicit, and we're left with:

`0 10000101 0101 0000 1000 0000 0000 000`

### Decoding: Normalized Value

Suppose we're given the following floating-point number:

`0xc0a0 0000`

Converting this to binary:

`0b1 10000001 010...`

This is a normalized value. So, we notice our value will be:

$$
1.010 \times 2^{128+1 - 127} = 1.010 \times 2^{2} = 101.0
$$

Converting this back to decimal: It's $5$, so with the signed bit, we have $-5.0$.