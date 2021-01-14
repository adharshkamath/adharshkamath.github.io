---
title: Mathy Compiler
description: 'The Mathy Compiler project, supported syntax, and much more!'
date: 2020-12-09T06:43:38.000Z
tags: [OpenMP, Compiler, DSL, Programming Language, Project]
---

The code for this project can be found in [this](https://github.com/adharshkamath/Mathy-Compiler) GitHub repository. This project was done under the guidance of [Dr. Rupesh Nasre](https://www.cse.iitm.ac.in/~rupesh/).

Some features of the language:

- Every statement in this language is terminated with a newline.
- All the variables are typed and they have the same type which can be specified at compile time (while compiling to C).
- The bounds used in loop-y statements are all `int`s.
- A bound variable is valid only within the statement it is used.
- This small language is in turn compiled to C.


You can write four types of statements in this language.
- Assignment statement: This is the usual assignment supported in almost all general programming languages. 
    Example: <br><br>
    ```prolog
    a = 100
    ```

- Forall statement: This statement can be used to do an operation on a range of values. 
    Syntax: <br><br>
    ```prolog
    ∀(bound variable) | bound {
        statements
    }
    ```
    <br>

    One important detail to keep in mind is the newline after the opening bracket. 
    (I had originally planned to enforce indentation and neatness in the syntax which is not completely implemented yet)

    <br>
    Example: <br><br>

    ```prolog
    ∀(i) | 0<=i<=100 {
        a[i] = i
    }
    ```
    <br>

- Sigma statement: This statement can be used to compute and store the sum of an *expression* over range of values.
    Syntax: <br><br>
    ```prolog
    variable = Σ(expression involving the bound variable) | bound
    ```
    <br>
    Example: <br><br>

    ```prolog
    mean = Σ(a[i]/100) | 0<=i<=100
    ```
    <br>

- Product statement: This statement can be used to compute and store the product of an *expression* over range of values.
    Syntax: <br><br>
    ```prolog
    variable = Π(expression involving the bound variable) | bound
    ```
    <br>
    Example: <br><br>

    ```prolog
    product = Π(a[i]) | 0<=i<=100
    ``` 
    <br>
An  *expression* in the above two statements means a combination of any number of variables using `+`,`-`,`*` or `/`.

A bound is a term that encapsulates the upper and lower limits of the looping variable and only two comparison operators can be used to descibe a bound, `<` and `<=` . 

The language also supports square-root expressions. So  **` √(expression)`** is a valid expression.

In all the above statements/expressions, the unicode characters can be replaced with words - 

| Symbol |  Alternative |
| :---: | :----: |
| ∀ | forall |
| Π | product |
| Σ | sigma |
| √ | sqrt |
| \| | where|

<br>

Checkout the [webpage](posts/mathy-compiler-demo) where you can try the compiler from your browser.

