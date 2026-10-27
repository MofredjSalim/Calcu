# Calcu — Multi-base calculator in C

A calculator written in C that does arithmetic operations **directly in the chosen base** (2 to 16), working on the digits as strings and ASCII values. It never converts the operands to decimal to compute the result. It carries, borrows and digit products are handled by hand, the way you would on paper.

> Beginner project, built to practice string manipulation and low level logic in C.

## Features

| Option | What it does |
|--------|--------------|
| 1 | Convert a decimal number to any base (2–16) |
| 2 | Convert a number from any base (2–16) to decimal |
| 3 | Compare two numbers in a given base |
| 4 | Addition in any base |
| 5 | Subtraction in any base |
| 6 | Multiplication in any base |
| 7 | Euclidean division in any base (quotient and remainder) |

## How it works

- **Digit-by-digit arithmetic.** Each operation walks through the two strings from right to left, using ASCII offsets (`'0'`, `'A'`) to get each digit's value, and propagates the carry or borrow itself.
- **Alignment.** Operands are padded with leading zeros to the same length (`check_size`), and leading zeros are removed from results (`delete_zeros`).
- **Multiplication** is built from the other routines: one partial product per digit of the second number, shifted, then summed with the base N addition.
- **Division** repeats multiplication and comparison to find the quotient, then subtracts to get the remainder.

## Build and run

```bash
gcc binary_calculator.c -o calcu
```

## Limits

- Bases from 2 to 16 only.
- Numbers are entered without a sign and are limited to 255 characters.
- Decimal conversions (options 1 and 2) use a standard `int`, so they only work for values that fit in one.

## Project structure

```
binary_calculator.c   all the code (single file)
README.md             this file
```
