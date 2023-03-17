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



# Connecting Pathes Method

Missing  elements  of the  incomplete matrix A  are obtained by taking the geometric mean of intensities of all connecting paths  connecting the two alternatives i and j in A

Reference: 
1. Tekile, H. A., Brunelli, M., & Fedrizzi, M. (2023). A numerical comparative study of completion methods for pairwise comparison matrices. Operations Research Perspectives, 100272.


