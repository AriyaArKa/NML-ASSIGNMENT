# Numerical Methods Console Application

This is a console-based application written in C++ that implements various numerical methods for solving linear equations, non-linear equations, differential equations, and performing matrix operations. The application provides an interactive menu-driven interface, allowing users to select the type of problem they wish to solve and choose from multiple algorithms available for that problem category.

## Table of Contents

- [Features](#features)
- [Algorithms Implemented](#algorithms-implemented)
  - [Linear Equations Solving Methods](#linear-equations-solving-methods)
    - [Jacobi Method](#jacobi-method)
    - [Gauss-Seidel Method](#gauss-seidel-method)
    - [Gauss Elimination](#gauss-elimination)
    - [Gauss-Jordan Elimination](#gauss-jordan-elimination)
    - [LU Factorization](#lu-factorization)
  - [Non-linear Equations Solving Methods](#non-linear-equations-solving-methods)
    - [Bisection Method](#bisection-method)
    - [False Position Method](#false-position-method)
    - [Secant Method](#secant-method)
    - [Newton-Raphson Method](#newton-raphson-method)
  - [Differential Equations Solving Methods](#differential-equations-solving-methods)
    - [Runge-Kutta Method (Fourth Order)](#runge-kutta-method-fourth-order)
  - [Matrix Operations](#matrix-operations)
    - [Matrix Inversion using Gauss-Jordan Elimination](#matrix-inversion-using-gauss-jordan-elimination)

## Features

- **Linear Equations Solving Methods**: Solve systems of linear equations using various iterative and direct methods.
- **Non-linear Equations Solving Methods**: Find roots of non-linear equations using bracketing and open methods.
- **Differential Equations Solving Methods**: Solve ordinary differential equations using the Runge-Kutta method.
- **Matrix Operations**: Perform matrix inversion using Gauss-Jordan elimination.
- **User-Friendly Interface**: Menu-driven console application with clear prompts and outputs.
- **Reusable Input**: Input data is entered once per session for linear and non-linear equations, allowing users to switch methods without re-entering data until they return to the main menu.

## Algorithms Implemented

### Linear Equations Solving Methods

#### Jacobi Method

The Jacobi method is an iterative algorithm for solving a system of linear equations. It is based on solving each equation for its own variable in terms of the other variables and iteratively updating the values until convergence.

**Algorithm Steps**:

1. Start with an initial guess for the solution vector.
2. For each iteration:
   - Compute the new value for each variable using the previous iteration's values.
   - Calculate the error between the new and old values.
3. Repeat until the maximum error exceeds the specified tolerance or the maximum number of iterations is reached.

**Convergence Criteria**:

- The method converges if the matrix is diagonally dominant or symmetric positive-definite.

#### Gauss-Seidel Method

The Gauss-Seidel method is an improvement over the Jacobi method. It uses the latest updated values within an iteration, which often results in faster convergence.

**Algorithm Steps**:

1. Start with an initial guess for the solution vector.
2. For each iteration:
   - Update each variable sequentially using the most recent values.
   - Compute the error between the new and old values.
3. Repeat until convergence criteria are met.

**Convergence Criteria**:

- Similar to the Jacobi method, convergence is guaranteed if the matrix is diagonally dominant or symmetric positive-definite.

#### Gauss Elimination

Gauss elimination is a direct method that transforms the system of linear equations into an upper triangular matrix, making it straightforward to solve via back substitution.

**Algorithm Steps**:

1. **Forward Elimination**:
   - For each pivot row, eliminate the variables below the pivot element.
   - Use partial pivoting to improve numerical stability.
2. **Back Substitution**:
   - Starting from the last equation, solve for each variable.
   - Substitute the known variables into the equations above to find the remaining variables.

#### Gauss-Jordan Elimination

Gauss-Jordan elimination extends Gauss elimination by transforming the matrix into a reduced row-echelon form (diagonal matrix), eliminating the need for back substitution.

**Algorithm Steps**:

1. **Forward Elimination**:
   - Convert the matrix into an upper triangular matrix.
2. **Backward Elimination**:
   - Convert the matrix into a diagonal matrix.
3. **Normalize Diagonal Elements**:
   - Scale rows to make the diagonal elements equal to one.
4. Extract the solution directly from the augmented matrix.

### Introduction To LU Factorization

An LU factorization of a matrix is a representation of the matrix as a product of a lower triangular matrix (the $L$ matrix) and an upper triangular matrix (the $U$ matrix) with the pyramid shape characteristic. This technique comes in handy when we would like to solve several systems of equations with the same coefficient matrix and varying right hand sides.

**Algorithm Steps**: 

1. **LU Decomposition**:
   - Factorize the matrix A as L times U where A=LU.
2. **Forward Substitution**:
   - Determine y in the equation Ly=b.
3. **Back Substitution**:
   - Determine x in the equation Ux=y.

**Advantages**:

- Solving multiple systems with an identical matrix is tremendously efficient.
- The LU decomposition approach can be applied again especially if the right hand side is modified.

### Non-linear Equations Solving Methods

#### Bisection Method

The bisection method is a bracketing method that repeatedly bisects an interval and selects a subinterval in which a root must lie.

**Algorithm Steps**:

1. Choose an initial interval $[a, b]$ where the function changes sign.
2. Compute the midpoint $c = \dfrac{a + b}{2}$.
3. Evaluate the function at $c$.
4. Decide the subinterval $[a, c]$ or $[c, b]$ where the root lies.
5. Repeat until the interval is sufficiently small or the function value at $c$ is within the tolerance.

**Convergence Criteria**:

- The function must be continuous on $[a, b]$ and $f(a)$ and $f(b)$ must have opposite signs.

### Method of False Position

This method, also known as the Regula Falsi method, is an enhancement of the bisection method which employs a secant line to approximate the position of the root.

**Overview of Steps in the Algorithm**:

1. Specify a start interval $[a, b]$ in which there is a change of sign of the function f.
2. Calculate c as:

   c = a - f(a)(b - a)/[f(b) - f(a)].

3. Consider f(c).
4. Choose the interval $[a,c]$ or the interval $[c,b]$ for the location of the root.
5. Continue while not completed.
#### Secant Method

The secant method is an open method that uses two initial approximations and approximates the derivative by a finite difference.

**Algorithm Steps**:

1. Choose two initial approximations $x_0$ and $x_1$.
2. Compute the next approximation using:

   $x_{n+1} = x_n - f(x_n) \dfrac{x_n - x_{n-1}}{f(x_n) - f(x_{n-1})}$

3. Repeat until the difference between successive approximations is within the tolerance.

**Advantages**:

- Faster convergence compared to bracketing methods.
- Does not require the computation of derivatives.

#### Newton-Raphson Method

The Newton-Raphson method is an open method that uses the function and its derivative to find successively better approximations to the roots.

**Algorithm Steps**:

1. Choose an initial approximation $x_0$.
2. Compute the next approximation using:

   $x_{n+1} = x_n - \dfrac{f(x_n)}{f'(x_n)}$

3. Repeat until convergence criteria are met.

**Advantages**:

- Quadratic convergence near the root.
- Very efficient if the derivative is easily computed.

**Convergence Criteria**:

- The function must be differentiable in the interval.
- The initial guess should be close to the actual root.

### Differential Equations Solving Methods

#### The Fourth Order Runsge-Kutta approach

The fourth order Runge-Kutta method provides an efficient technique for the numerical solution of ordinary differential equations.

**Steps of the algorithm**:

Let’s consider an initial value problem $y’ = f(x,y)$, $y(x_0) = y_0$ with step size h.

As a result of each step of

1. The slopes are computed as follows:

   k_1 = h f(x_n , y_n ) ; 
   k_2 = h f(x_n + h/2, y_n + k_1/2) ; 
   k_3 = h f(x_n + h/2, y_n + k_2/2) ; 
   k_4 = h f(x_n + h, y_n + k_3) .

2. Solution is advanced:

   $ y\_{n+1} = y\_n + \frac{1}{6}(k\_1 + 2k\_2 + 2k\_3 + k\_4) $

3. Increment:

   $ x\_{n+1} = x\_n + h $

**Advantages**:

- Offers improved accuracy for the method while maintaining fairly small step sizes.
- No need for any higher order derivatives.


### Matrix Operations

#### Matrix Inversion using Gauss-Jordan Elimination

This method computes the inverse of a matrix by augmenting it with the identity matrix and applying Gauss-Jordan elimination.

**Algorithm Steps**:

1. Form the augmented matrix $[A | I]$, where $I$ is the identity matrix.
2. Apply Gauss-Jordan elimination to transform $[A | I]$ into $[I | A^{-1}]$.
3. Extract the inverse $A^{-1}$ from the augmented matrix.

**Conditions**:

- The matrix $A$ must be square and non-singular (invertible).
- Zero pivot elements indicate a singular matrix that cannot be inverted.
