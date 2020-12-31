---
title: Mathy Compiler
description: 'The Mathy Compiler project, supported syntax, and much more!'
date: 2020-12-09T06:43:38.000Z
tags: [OpenMP, Compiler, DSL, Programming Language]
draft: true
---

The code for this project can be found in [this](https://github.com/adharshkamath/Mathy-Compiler) GitHub repository.

You can write four types of statements in this small language. 
- Assignment statements: This is the usual assignment operation supported in almost all programming languages. 
    Example: <br><br>
    ```prolog
    a = 100
    ```

- Forall statement: This statement can be used to do an operation on a range of values.
    Example: <br><br>
    ```prolog
    ∀(i) | 0<=i<=100 {
        a[i] = i
    }
    ```
    <br>

- Sigma statement: This statement can be used to do store the sum of an expression over range of values.
    Example: <br><br>
    ```prolog
    mean = Σ(a[i]/100) | 0<=i<=100
    ```
    <br>

- Product statement: This statement can be used to do store the product of an expression over range of values.
    Example: <br><br>
    ```prolog
    product = Π(a[i]) | 0<=i<=100
    ```
    <br>

This project was done under the guidance of [Dr. Rupesh Nasre](https://www.cse.iitm.ac.in/~rupesh/).