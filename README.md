# Compiler Design Lab

A comprehensive collection of compiler design programs covering various aspects of compiler construction including lexical analysis, syntax analysis, parsing, and code generation.

## 📋 Table of Contents

- [Overview](#overview)
- [Prerequisites](#prerequisites)
- [Programs](#programs)
  - [Lexical Analysis](#lexical-analysis)
  - [Syntax Analysis](#syntax-analysis)
  - [Parsing](#parsing)
  - [Code Generation](#code-generation)
- [Compilation and Execution](#compilation-and-execution)
- [Grammar Used](#grammar-used)
- [License](#license)

## 🎯 Overview

This repository contains implementations of fundamental compiler design concepts and algorithms. Each program demonstrates a specific phase or technique used in compiler construction.

## 🛠 Prerequisites

To compile and run these programs, you need:

- **C Compiler**: GCC or any C99-compatible compiler
- **C++ Compiler**: G++ (for C++ programs)
- **Java Development Kit (JDK)**: Version 8 or higher
- **Flex**: Fast lexical analyzer generator
- **Bison** (optional): For yacc/bison programs

## 📂 Programs

### Lexical Analysis

#### 1. CapitalLetters.lex

**Description**: A Lex program that identifies and counts capital letters in the input.

**Compilation & Execution**:

```bash
flex CapitalLetters.lex
gcc lex.yy.c -o capital_letters
./capital_letters
```

**Sample Input**:

```
Hello World
```

**Sample Output**:

```
H capital letter
ello World not a capital letter

Number of Capital letters in the given input - 1
```

---

#### 2. Operators&Identifiers.lex

**Description**: A Lex program that recognizes and counts operators and identifiers in arithmetic expressions.

**Compilation & Execution**:

```bash
flex Operators&Identifiers.lex
gcc lex.yy.c -o operators_identifiers
./operators_identifiers
```

**Sample Input**:

```
x + y * 2
```

**Sample Output**:

```
x is an identifier
+ is an operator
y is an identifier
* is an operator

Number of operators: 2
Number of identifiers: 2
```

---

#### 3. ScannerByRegularExpression

**Description**: A combined Lex and Yacc program demonstrating scanner implementation using regular expressions.

**Files**: Contains both `test.l` (Lex file) and `test.y` (Yacc file)

**Compilation & Execution** (Windows):

```bash
win_flex test.l
win_bison -d test.y
gcc lex.yy.c test.tab.c -o scanner
./scanner
```

**Compilation & Execution** (Linux/Mac):

```bash
flex test.l
bison -d test.y
gcc lex.yy.c test.tab.c -o scanner
./scanner
```

---

### Syntax Analysis

#### 4. ComputationOfFirst.c

**Description**: Computes the FIRST sets for a given context-free grammar.

**Grammar Used**:

```
E -> TA
A -> +TA | #
T -> FB
B -> *FB | #
F -> (E) | i
```

(where `#` represents epsilon)

**Compilation & Execution**:

```bash
gcc ComputationOfFirst.c -o first
./first
```

**Sample Output**:

```
First(E) = { (, i, }
First(A) = { +, #, }
First(T) = { (, i, }
First(B) = { *, #, }
First(F) = { (, i, }
```

---

#### 5. First&Follow.c

**Description**: Computes both FIRST and FOLLOW sets for a given context-free grammar.

**Grammar Used**: Same as ComputationOfFirst.c

**Compilation & Execution**:

```bash
gcc First&Follow.c -o first_follow
./first_follow
```

**Sample Output**:

```
First(E) = { (, i, }
First(A) = { +, #, }
First(T) = { (, i, }
First(B) = { *, #, }
First(F) = { (, i, }
-----------------------------------------------

Follow(E) = { $, ), }
Follow(A) = { $, ), }
Follow(T) = { +, $, ), }
Follow(B) = { +, $, ), }
Follow(F) = { *, +, $, ), }
```

---

#### 6. LeftRecursion.c

**Description**: Eliminates left recursion from a given grammar production.

**Compilation & Execution**:

```bash
gcc LeftRecursion.c -o left_recursion
./left_recursion
```

**Sample Input**:

```
E->E+A|A
```

**Sample Output**:

```
Grammar Without Left Recursion:

E->AE'
E'->+AE'|#
```

---

#### 7. LeftFactoring.c

**Description**: Performs left factoring on grammar productions with common prefixes.

**Compilation & Execution**:

```bash
gcc LeftFactoring.c -o left_factoring
./left_factoring
```

**Sample Input**:

```
abcd|abef
```

**Sample Output**:

```
A->abX
X->cd|ef
```

---

### Parsing

#### 8. PredictiveParser.cpp

**Description**: Implementation of a predictive (LL(1)) parser that constructs a parsing table and parses input strings.

**Compilation & Execution**:

```bash
g++ PredictiveParser.cpp -o predictive_parser
./predictive_parser
```

**Sample Input**:

```
Number of productions: 5
Enter productions:
E->TA
A->+TA
A->#
T->FB
B->#
F->i

Number of Terminals: 3
Enter Terminals: + ( i
Number of Non-Terminals: 5
Enter Non-Terminals and their FOLLOW sets...
```

**Features**:

- Builds predictive parsing table
- Parses input strings using stack-based algorithm
- Handles epsilon productions

---

#### 9. SLRParser.cpp

**Description**: Implementation of an SLR(1) parser that constructs canonical collection of LR(0) items.

**Compilation & Execution**:

```bash
g++ SLRParser.cpp -o slr_parser
./slr_parser
```

**Sample Input**:

```
ENTER THE PRODUCTIONS OF THE GRAMMAR(ENTER PROD WITH ARROW, 0 TO END):
E->E+T
E->T
T->T*F
T->F
F->(E)
F->i
0
```

**Sample Output**:

```
Augmented grammar
S->E
E->E+T
E->T
T->T*F
T->F
F->(E)
F->i

THE SET OF ITEMS ARE

I0
S->.E
E->.E+T
E->.T
T->.T*F
T->.F
F->.(E)
F->.i
...
```

---

### Code Generation

#### 10. ICG.java

**Description**: Demonstrates simple intermediate code generation for if statements.

**Compilation & Execution**:

```bash
javac ICG.java
java ICG
```

**Sample Output**:

```
Generated code:
if (x > 5) {
    y = x * 2;
}
```

---

#### 11. SyntaxTreeArithmetic.java

**Description**: Constructs and evaluates syntax trees for arithmetic expressions.

**Compilation & Execution**:

```bash
javac SyntaxTreeArithmetic.java
java SyntaxTreeArithmetic
```

**Sample Output**:

```
Result: 13
```

(for expression: 3 + (5 \* 2))

**Features**:

- Binary tree representation of expressions
- Recursive evaluation
- Supports +, -, \*, / operators
- Division by zero handling

---

#### 12. BasicJavaProgram.java

**Description**: A basic Java program that checks if a number is positive, negative, or zero.

**Compilation & Execution**:

```bash
javac BasicJavaProgram.java
java BasicJavaProgram
```

**Sample Input**:

```
Enter a number: 5
```

**Sample Output**:

```
The number is positive.
```

---

## 📖 Grammar Used

Most programs use the following expression grammar:

```
E  -> TA
A  -> +TA | ε
T  -> FB
B  -> *FB | ε
F  -> (E) | i
```

Where:

- `E` = Expression
- `T` = Term
- `F` = Factor
- `A` = Expression tail
- `B` = Term tail
- `i` = identifier/number
- `ε` or `#` = epsilon (empty string)

## 🔧 Compilation Tips

### C Programs

```bash
gcc filename.c -o outputname
./outputname
```

### C++ Programs

```bash
g++ filename.cpp -o outputname
./outputname
```

### Java Programs

```bash
javac filename.java
java classname
```

### Lex Programs

```bash
flex filename.lex
gcc lex.yy.c -o outputname
./outputname
```

### Lex + Yacc Programs

```bash
flex lexfile.l
bison -d yaccfile.y
gcc lex.yy.c yaccfile.tab.c -o outputname
./outputname
```

## 📝 Notes

- All C programs use standard input/output for user interaction
- Lex programs require Flex to be installed
- Some programs have hardcoded grammars for demonstration purposes
- The `#` symbol represents epsilon (ε) in grammar productions

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
