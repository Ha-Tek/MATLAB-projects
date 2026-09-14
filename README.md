# Incomplete Pairwise Comparison Matrix Completion Methods

This repository contains MATLAB implementations of several methods for completing **incomplete pairwise comparison matrices (iPCMs)** in the context of the **Analytic Hierarchy Process (AHP)**.

---

## 1. Nelder–Mead Algorithm for Incomplete Pairwise Comparison Matrices

**Author:** Hailemariam Abebe Tekile  
**Date:** June 17, 2021

### Description

This implementation uses the **Nelder–Mead algorithm** together with **coordinate transformation** for the optimal completion of incomplete pairwise comparison matrices.

The MATLAB function [`fminsearch`](https://www.mathworks.com/help/matlab/ref/fminsearch.html), which implements the Nelder–Mead optimization algorithm, is used together with coordinate transformation.

### Example

The implementation includes an example of a **constrained eigenvalue minimization problem** based on the following interval constraints:

- `5 <= x₁ <= 7`
- `1/9 <= x₂ <= 9`

### Reference

> Tekile, H. A., Fedrizzi, M., & Brunelli, M. (2021). Constrained eigenvalue minimization of incomplete pairwise comparison matrices by Nelder-Mead algorithm. *Algorithms, 14*(8), 222.

### MATLAB Implementation

To use the code, modify the following parameters:

- `A` — incomplete pairwise comparison matrix
- `numberOfMissingEntries` — number of missing entries in the matrix
- `lb` — lower bound
- `ub` — upper bound

Then run the MATLAB code.

---

## 2. Ergu et al.'s Least Squares Method (LSM) Using `fmincon`

### Description

This method estimates the optimal values of missing pairwise comparisons by minimizing the **sum of errors**, based on the **Geometric Mean Induced Bias Matrix (GMIBEM)**, subject to the interval constraint:

$$
\frac{1}{9} \leq x \leq 9
$$

The MATLAB [`fmincon`](https://www.mathworks.com/help/optim/ug/fmincon.html) function is used for constrained optimization.

### References

1. Tekile, H. A., Brunelli, M., & Fedrizzi, M. (2023). A numerical comparative study of completion methods for pairwise comparison matrices. *Operations Research Perspectives*, 100272.
2. Ergu, D., Kou, G., Peng, Y., & Zhang, M. (2016). Estimating the missing values for the incomplete decision matrix and consistency optimization in emergency management. *Applied Mathematical Modelling*, 40, 254–267.

---

## 3. Incomplete Logarithmic Least Squares Method (LLSM) Using `fmincon`

### Description

This implementation uses **incomplete Logarithmic Least Squares Method (LLSM)** with MATLAB's `fmincon` to estimate missing values under the interval constraint:

$$
\frac{1}{9} \leq \frac{w_i}{w_j} \leq 9
$$

for the relevant pairs of alternatives.

### Constraints

The optimization problem considers the following constraints:

1. **Pairwise ratio constraint**

   $$
   \frac{1}{9} \leq \frac{x_i}{x_j} \leq 9
   $$

   for `i, j = 1, 2, ..., n`, considering `i < j`.

2. **Normalization constraint**

   $$
   x_1 + x_2 + \cdots + x_n = 1
   $$

3. **Positivity constraint**

   $$
   x_i > 0, \qquad i = 1,2,\ldots,n
   $$

### Reference

> Tekile, H. A., Brunelli, M., & Fedrizzi, M. (2023). A numerical comparative study of completion methods for pairwise comparison matrices. *Operations Research Perspectives*, 100272.

---

## 4. Connecting Paths Method

### Description

The **Connecting Paths Method** estimates missing elements of an incomplete pairwise comparison matrix by taking the **geometric mean of the intensities of all connecting paths** between two alternatives `i` and `j`.

In other words, when the direct comparison between two alternatives is missing, the method uses the available connecting paths through other alternatives to estimate the missing comparison.

### Reference

> Tekile, H. A., Brunelli, M., & Fedrizzi, M. (2023). A numerical comparative study of completion methods for pairwise comparison matrices. *Operations Research Perspectives*, 100272.

---

## 5. DEMATEL-Based Completion Method for Incomplete PCMs in AHP

### Description

The **DEMATEL-based completion method** provides a different approach for estimating missing values in incomplete pairwise comparison matrices (iPCMs).

The method estimates the **indirect relationship** between two alternatives or criteria when their direct relative importance is unknown.

This provides an interpretation of missing comparisons based on the indirect relationships among the alternatives or criteria.

### References

1. Zhou, X., Hu, Y., Deng, Y., Chan, F. T., & Ishizaka, A. (2018). A DEMATEL-based completion method for incomplete pairwise comparison matrix in AHP. *Annals of Operations Research*, 271, 1045–1066.
2. Tekile, H. A., Brunelli, M., & Fedrizzi, M. (2023). A numerical comparative study of completion methods for pairwise comparison matrices. *Operations Research Perspectives*, 100272.

---

## References

### Main References

- Tekile, H. A., Fedrizzi, M., & Brunelli, M. (2021). Constrained eigenvalue minimization of incomplete pairwise comparison matrices by Nelder-Mead algorithm. *Algorithms, 14*(8), 222.

- Tekile, H. A., Brunelli, M., & Fedrizzi, M. (2023). A numerical comparative study of completion methods for pairwise comparison matrices. *Operations Research Perspectives*, 100272.

- Ergu, D., Kou, G., Peng, Y., & Zhang, M. (2016). Estimating the missing values for the incomplete decision matrix and consistency optimization in emergency management. *Applied Mathematical Modelling*, 40, 254–267.

- Zhou, X., Hu, Y., Deng, Y., Chan, F. T., & Ishizaka, A. (2018). A DEMATEL-based completion method for incomplete pairwise comparison matrix in AHP. *Annals of Operations Research*, 271, 1045–1066.
