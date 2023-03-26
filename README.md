# Nelder-Mead algorithm Implementation for Incomplete Pairwise Comparison Matrices

Author: Hailemariam Abebe Tekile, June 17, 2021

Nelde-Mead algorithm using the techniques of coordinate transformation for the optimal completion of incomplete pairwise comparison matrices.
I used simply MATLAB's fminsearch (equivalent to the standard Nelder-Mead algorithm) along with the coordinate transformation.
 
An example of a constrained eigenvalue problem which is taken from the following paper based on the interval constraint 5<=x_1<=7 and 1/9<=x_2<=9.

Reference: Tekile, H. A., Fedrizzi, M., & Brunelli, M. (2021). Constrained eigenvalue minimization of incomplete pairwise comparison matrices by Nelder-Mead algorithm. Algorithms, 14(8), 222.


Implementation of the MATLAB code: One can modify only the incomplete pairwise comparison matrix (A),  the number of missing entries (numberOfMissingEntries) and the lowe bound (lb) and upper bound (ub). Then, run the code.



# Ergu et al.'s 2016  Least Square Method (LSM) using fmincon :

This method is used to find the optimal values of missing comparisons by minimizing the sum of errors (geometric mean induced bias matrix (GMIBEM) ) subject to the interval constraint [1/9,9].

References:
1. Tekile, H. A., Brunelli, M., & Fedrizzi, M. (2023). A numerical comparative study of completion methods for pairwise comparison matrices. Operations Research Perspectives, 100272.
2. Ergu, D.; Kou, G.; Peng, Y.; Zhang, M. Estimating the missing values for the incomplete decision matrix and consistency optimization in emergency management. Appl. Math. Model. 2016, 40, 254–267

# Incomplete Logarithmic Least Squares Method (LLSM) using fmincon:
Incomplete LLSM using fmincon on the interval [1/9,9]. i.e, 1/9<=w(i)/w(j)<=9 , to put inside fmincon
The constraints are: 
1. 1/9 <=x(i)/x(j)<=9, for i,j=1,2,3,4,...,n by considering i<j.
2. x(1) + x(2) + x(3) + x(4) +...+x(n)= 1;
3. x(i) > 0 for i=1,2,3,4,...,n

Reference: 
1. Tekile, H. A., Brunelli, M., & Fedrizzi, M. (2023). A numerical comparative study of completion methods for pairwise comparison matrices. Operations Research Perspectives, 100272.



# Connecting Paths Method

Missing  elements  of the  incomplete matrix A  are obtained by taking the geometric mean of intensities of all connecting paths  connecting the two alternatives i and j in A

Reference: 
1. Tekile, H. A., Brunelli, M., & Fedrizzi, M. (2023). A numerical comparative study of completion methods for pairwise comparison matrices. Operations Research Perspectives, 100272.

# The DEMATEL-based completion method for incomplete PCMs in AHP

The DEMATEL-based completion method provides a new perspective to estimate the missing values in iPCMs with explicit physical meaning: calculate the indirect relation of two alternatives/criteria if their relative importance (i.e. direct relation) is unknown.

References:
1. Zhou, X., Hu, Y., Deng, Y., Chan, F. T., & Ishizaka, A. (2018). A DEMATEL-based completion method for incomplete pairwise comparison matrix in AHP. Annals of Operations Research, 271, 1045-1066.
2.  Tekile, H. A., Brunelli, M., & Fedrizzi, M. (2023). A numerical comparative study of completion methods for pairwise comparison matrices. Operations Research Perspectives, 100272.
