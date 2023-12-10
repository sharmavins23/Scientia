An array is a [[Data Structures|data structure]] of contiguous and similar items. Each item has the same sizing and structure; As such, they can easily be concatenated together in a contiguous portion of [[Memory (Computing)|memory]].

Arrays may have indices for the number of elements they have, and these indices correspond to consistent offsets from the 'head' of the array. With these, accessing a value takes $O(1)$ time, but the array takes up $O(n)$ space.

## Pointers

Suppose we have the following code in C:

```c
int val[5] = {1, 8, 6, 1, 3};
// Assume (int*)val = 0xFF00
```

Let's look at a series of pointers:

|Thing|Type|Value|Notes|
|---|---|---|---|
|`val`|`int*`|`0xFF00`|Start of the array.|
|`val[2]`|`int`|`6`|Third element of a 0-indexed array.|
|`*(val + 2)`|`int`|`6`|The third element is 'dereferenced.'|
|`&val[2]`|`int*`|`0xFF08`|This does the same thing as above.|
|`(val + 2)`|`int*`|`0xFF08`|Again, the same computation.|
|`(val + i)`|`int*`|`0xFF00` + $4i$|We can access a value at an offset.|

This table brings up an interesting point - Pointers can be utilized as arrays (as they're fundamentally the same!). In C, pointers refer to addresses in [[Memory (Computing)|memory]], and the type of a pointer refers to its offset amount when incrementing the pointer.

## Multi-dimensional Arrays

Generally, arrays are packed in space-wise. Multi-dimensional arrays follow a similar structure - Let's look at the following code.

```c
int A[3][4] = {
	0, 1, 2, 3,
	4, 5, 6, 7,
	8, 9, 10, 11
};
```

Arrays are organized in memory in row-major order. Any dimensions will simply be concatenated. As such, the values in that array (above) follow the offsets in order to access it. Let's take a look at some examples:

|Value|Compiles?|Bad de-reference?|Size (bytes)|Notes|
|---|---|---|---|---|
|`int A1[3][5]`|Yes|No|$60$|A simple array.|
|`int *A2[3][5]*`|Yes|No|$120$|An array of pointers.|
|`int (*A3)[3][5]`|Yes|No|$8$|A single pointer. The bracket values are (potentially) ignored.|
|`int *(A4[3][5])`|Yes|No|$120$|Here, `A4` is a pointer pointing to a pointer array.|
|`int (*A5[3])[5]`|Yes|No|$24$|Here, `A5` is an array of 3 elements.|
