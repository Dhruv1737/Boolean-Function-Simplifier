# Boolean Expression Simplifier — Quine–McCluskey Algorithm

**From minterms and maxterms to a simplified Boolean expression.**

A Boolean expression can get messy pretty quickly. This project makes it easier to simplify logical functions by implementing the **Quine–McCluskey algorithm**, a systematic method for Boolean minimization.

Enter the number of variables, choose whether you're working with minterms or maxterms, provide the corresponding indices, and let the algorithm do the rest.

## ✨ What Does It Do?

The project takes a Boolean function represented by minterms or maxterms and simplifies it into a more compact logical expression.

- **Variable-based input:** Specify the number of Boolean variables.
- **Minterm and maxterm support:** Choose the representation that matches your function.
- **Automatic minimization:** Apply the Quine–McCluskey algorithm to reduce the expression.
- **Step-by-step simplification:** Follow the grouping and combining process to understand how the result is obtained.
- **Readable output:** Display the simplified Boolean expression in standard notation.

## 🧠 How Does It Work?

Instead of relying on Karnaugh maps, which become difficult to manage as the number of variables grows, Quine–McCluskey uses a structured, tabular approach.

Here's the process behind the simplification.

### 1. Represent the Function in Binary

Each minterm or maxterm index is converted into a binary representation using the specified number of variables.

For example, with three variables \(A, B, C\):

| Decimal index | Binary representation |
|---:|:---:|
| 1 | 001 |
| 3 | 011 |
| 5 | 101 |
| 7 | 111 |

Each binary digit corresponds to a variable.

### 2. Group Terms by Number of 1s

Terms are placed into groups according to how many `1`s their binary representations contain.

This makes it easier to identify terms that can be combined. Two terms can be combined when their binary representations differ in **exactly one bit**.

For example:

```text
001
011
---
0-1
```

The middle bit differs, so it is replaced with a dash (`-`). This means that the corresponding variable no longer affects the expression.

### 3. Combine Repeatedly

The newly formed terms are compared again to see whether they can be combined further.

For example:

```text
001  +  011  →  0-1
101  +  111  →  1-1

0-1  +  1-1  →  --1
```

Each dash represents a variable eliminated during simplification.

The process continues until no further valid combinations can be made.

### 4. Identify Prime Implicants

Terms that cannot be combined any further are called **prime implicants**.

These terms represent the largest valid combinations found by the algorithm. However, not every prime implicant is necessarily required in the final answer.

### 5. Select the Required Terms

The algorithm determines which prime implicants are needed to cover the original function's minterms or maxterms.

It identifies essential prime implicants and then selects additional implicants, where necessary, to cover all remaining required indices.

The goal is to obtain a compact expression without changing the function's logical behavior.

### 6. Generate the Simplified Expression

Finally, the selected terms are converted into standard Boolean notation.

For minterms, the result is represented as a **Sum of Products (SOP)**. For maxterms, it is represented as a **Product of Sums (POS)**.

The result is a simplified Boolean expression derived directly from the input function.

## 🚀 Example

Suppose we have three variables and the following minterms:

```text
Number of variables: 3
Input type: Minterms
Minterms: 1, 3, 5, 7
```

The binary representations are:

```text
001
011
101
111
```

After repeated combinations, we obtain:

```text
--1
```

Both \(A\) and \(B\) have been eliminated. Only \(C\) remains.

**Simplified expression:**

\[
\boxed{F(A,B,C)=C}
\]

A function that initially required four minterms reduces to a single literal.

## 🔄 Minterms vs. Maxterms

The project supports both common canonical representations of a Boolean function.

| Input type | Represents | Simplified output |
|---|---|---|
| Minterms | Input combinations where \(F=1\) | SOP — Sum of Products |
| Maxterms | Input combinations where \(F=0\) | POS — Product of Sums |

This allows the same minimization approach to work with either the ON-set or the OFF-set of a function.

## ⚙️ Why Quine–McCluskey?

Karnaugh maps are excellent for learning and simplifying functions with a small number of variables. However, their visual layout becomes less convenient as the variable count increases.

Quine–McCluskey offers a systematic alternative:

- **Algorithmic:** Uses defined rules rather than visual pattern recognition.
- **Scalable in structure:** The same procedure applies as the number of variables grows, although the computational cost can increase rapidly.
- **Traceable:** Grouping, combining, and implicant selection can be followed step by step.
- **Useful for learning:** Connects binary representations with Boolean algebra and digital logic design.

Finding a minimum expression can involve multiple equivalent solutions, so the particular simplified expression may depend on the implicant-selection strategy.

## 🎯 What You'll Learn

This project brings together concepts from:

- Boolean algebra and logic minimization
- Binary number representation
- Prime implicants and essential prime implicants
- Combinatorial search and tabular algorithms
- Digital logic design

## 📌 Project Goal

The goal is to make Boolean minimization more accessible by turning a mathematical procedure into an interactive, easy-to-follow process.

Whether you're studying digital electronics, preparing for logic-design problems, or exploring classical algorithms, this tool provides a practical way to see how complex Boolean functions can be reduced to simpler expressions.

---

**Core algorithm:** Quine–McCluskey (tabulation method)  
**Input:** Number of variables and minterm/maxterm indices  
**Output:** Simplified Boolean expression in SOP or POS form
