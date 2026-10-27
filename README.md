# Calcu — Multi-base calculator in C

A command-line calculator written in C that does arithmetic **directly in the chosen base** (2 to 16), working on the digits as strings and ASCII values. It never converts the operands to decimal to compute the result: carries, borrows and digit products are handled by hand, the way you would on paper.

> Beginner project, built to practise string manipulation and low-level logic in C.

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

Digits above 9 are written `A` to `F` (uppercase). Invalid digits for the chosen base are rejected.

## How it works

- **Digit-by-digit arithmetic.** Each operation walks through the two strings from right to left, using ASCII offsets (`'0'`, `'A'`) to get each digit's value, and propagates the carry or borrow itself.
- **Alignment.** Operands are padded with leading zeros to the same length (`check_size`), and leading zeros are removed from results (`delete_zeros`).
- **Multiplication** is built from the other routines: one partial product per digit of the second number, shifted, then summed with the base-N addition.
- **Division** repeats multiplication and comparison to find the quotient, then subtracts to get the remainder.

## Build and run

```bash
gcc binary_calculator.c -o calcu -lm
./calcu
```

## Examples

Addition in base 2 (`1011 + 110`):

```
Enter the base: 2
Enter the numbers: 1011 110
Result: 10001
```

Multiplication in base 16 (`1F × 3`):

```
Enter the base: 16
Enter the numbers: 1F 3
Result: 5D
```

Euclidean division in base 10 (`17 ÷ 5`):

```
Enter the base: 10
Enter the numbers: 17 5
Result: 3
Rest: 2
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

-----------------------------------------------------------

Calculatrice en ligne de commande, écrite en C, qui effectue les opérations **directement dans la base choisie** (de 2 à 16), en manipulant les chiffres comme des chaînes de caractères et des codes ASCII. Aucun opérande n'est converti en décimal pour calculer : retenues, emprunts et produits de chiffres sont gérés à la main, comme sur papier.

> Projet de débutant, réalisé pour s'exercer à la manipulation de chaînes et à la logique bas niveau en C.

## Fonctionnalités

1. Conversion du décimal vers une base quelconque (2 à 16)
2. Conversion d'une base quelconque (2 à 16) vers le décimal
3. Comparaison de deux nombres dans une base donnée
4. Addition dans n'importe quelle base
5. Soustraction dans n'importe quelle base
6. Multiplication dans n'importe quelle base
7. Division euclidienne dans n'importe quelle base (quotient et reste)

Les chiffres supérieurs à 9 s'écrivent de `A` à `F` (majuscules). Les chiffres invalides pour la base choisie sont refusés.

## Principe

- Chaque opération parcourt les deux chaînes de droite à gauche, utilise les décalages ASCII (`'0'`, `'A'`) pour obtenir la valeur de chaque chiffre, et propage elle-même la retenue ou l'emprunt.
- Les opérandes sont complétés par des zéros à gauche pour avoir la même longueur ; les zéros inutiles sont supprimés du résultat.
- La multiplication réutilise l'addition en base N (un produit partiel par chiffre, décalé, puis additionné).
- La division répète multiplication et comparaison pour trouver le quotient, puis soustrait pour obtenir le reste.

## Compilation et exécution

```bash
gcc binary_calculator.c -o calcu -lm
./calcu
```

## Limites

- Bases de 2 à 16 uniquement.
- Nombres saisis sans signe, 255 caractères maximum.
- Les conversions décimales (options 1 et 2) utilisent un `int` standard.
