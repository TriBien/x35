# Week 1: Bits, Bytes, Number Representation

## 1. Bit patterns and interpretation

The same bit pattern can have different meanings depending on how it is interpreted.

For example, the same 8 bits could represent an unsigned integer, a signed integer, a character, or part of a floating-point value. Bits themselves have no inherent meaning; their meaning comes from the representation and interpretation we assign to them.

## 2. Two's complement

Two's complement is a representation of signed integers that makes arithmetic hardware simpler.

One important advantage is that the same binary adder circuitry can be used for both addition and subtraction. Subtraction can be performed by adding the two's complement of the number being subtracted.

This allows hardware to avoid having completely separate circuits for signed addition and subtraction.

## 3. Integer overflow

Overflow occurs when the mathematical result of an operation cannot be represented within the range of the chosen data type.

For example, with an 8-bit unsigned integer:

Range: 0 to 255
255 + 1 = 256
256 cannot be represented using 8 bits

The resulting behavior depends on the representation and programming language. For example, fixed-width unsigned arithmetic commonly wraps around modulo 2^n

## 4. Floating-point representation

Floating-point numbers provide a way to represent a very large range of numerical values, but they involve a trade-off between precision, range, memory usage, and performance.

There are two important categories to distinguish:

+ Binary floating-point (float, double) usually provides an approximation of decimal values.

+ Decimal fixed-point/decimal arithmetic (decimal, numeric, etc.) can represent many decimal values exactly.

### Why does 0.1 + 0.2 != 0.3 happen?

In binary floating-point, many decimal fractions—including 0.1, 0.2, and 0.3—cannot be represented exactly with a finite number of binary digits.

Therefore, the stored values are approximations, and arithmetic on those approximations can produce:

0.1 + 0.2 ≠ 0.3

This is not because floating-point arithmetic is "wrong"; it is a consequence of representing numbers with finite precision.

### Decimal/numeric types

Decimal types are designed to represent decimal numbers exactly within their supported precision and scale.

A common conceptual model is scaled integers. For example:

$12.34 → 1234 cents

However, implementations of decimal/numeric types vary. They are not necessarily implemented simply as an integer multiplied by 100, nor do they necessarily use base 100 or 1000. The important idea is that decimal arithmetic uses a representation designed to preserve decimal precision.

## 5. Choosing a data representation

Choosing a data representation is a design trade-off.

Different representations optimize for different properties, such as:

human readability
storage size
network bandwidth
serialization/deserialization cost
processing speed
interoperability
precision

For example:

JSON is human-readable and widely interoperable, but generally requires more storage and bandwidth.
Binary formats can be more compact and efficient, but are generally less human-readable.

The right representation depends on the requirements and constraints of the system.

## 6. Big-endian vs. little-endian

Endianness defines the order in which the bytes of a multi-byte value are stored in memory or transmitted in a binary format.

Big-endian: the most significant byte (MSB) comes first, at the lowest address.

Little-endian: the least significant byte (LSB) comes first, at the lowest address.

For example, the 32-bit value:

0x12345678

is stored as:

Big-endian:    12 34 56 78

Little-endian: 78 56 34 12

### Why do systems choose one over the other?

There is no universally superior choice. The choice is usually driven by hardware design, historical compatibility, protocol conventions, and implementation trade-offs.

+ Big-endian

Big-endian puts the most significant part first, which matches the way humans normally write numbers:

12345678

12 34 56 78

This can make hexadecimal dumps, debugging, and protocol specifications easier to read because the byte order follows the conventional written order.

Big-endian is also commonly used in network protocols. The term network byte order traditionally means big-endian, providing a standard representation so that different machines can communicate regardless of their native CPU endianness.

+ Little-endian

Little-endian puts the least significant byte first:

12345678

78 56 34 12

One practical advantage is that the beginning of the representation contains the least significant part of the value. This works conveniently with operations that process low-order bits first and with certain variable-width integer operations.

More importantly, little-endian became dominant in several major CPU architectures and ecosystems. Once an architecture, operating system, compiler, ABI, and software ecosystem adopt an endian convention, backward compatibility becomes a powerful reason to keep it.

## 7. Bit flags

Bit flags allow multiple Boolean attributes to be represented within a single integer by assigning one bit to each attribute.

For example:

READ  = 0001

WRITE = 0010

EXEC  = 0100

A value of: 0110 
could represent: WRITE + EXEC

Bitwise operations can be used to:
+ set a flag
+ clear a flag
+ test a flag
+ toggle a flag

This can reduce storage and sometimes improve performance, especially when many Boolean attributes need to be packed together.

However, bit flags introduce a readability and maintainability trade-off. A collection of separate Boolean columns is often easier to understand, query, and evolve.

Therefore:

Bit flags trade representation compactness against readability and maintainability.

For database design, this trade-off should be evaluated carefully rather than assuming that fewer columns automatically means a better design.