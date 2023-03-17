# MATLAB-projects
Ergu et al.'s 2016  Least Square Method (LSM) with MATLAB'S fmincon
Hailemariam A. Tekile
4 August 2021
The LSM could be used to find the optimal values of missing comparisons by minimizing the sum of errors (geometric mean induced bias matrix (GMIBEM) ) subject to the interval constraint 

References:
Tekile, H. A., Brunelli, M., & Fedrizzi, M. (2023). A numerical comparative study of completion methods for pairwise comparison matrices. Operations Research Perspectives, 100272.
Ergu, D.; Kou, G.; Peng, Y.; Zhang, M. Estimating the missing values for the incomplete decision matrix and consistency optimization in emergency management. Appl. Math. Model. 2016, 40, 254–267

[clear; close; clc

% global variables
global A;
global NumberOfMissingEntries;
global n;
global xPosition;


% Incomplete PCM 
A=[...
 1   0 3 1;...
 0 1  1/2 4;...
 1/3 2  1 5;...
 1 1/4 1/5 1];

%size of A
n = size(A,2); 

% number of missing entries in  the upper triangular  matrix A
NumberOfMissingEntries = 1; 

x0 = ones(1,NumberOfMissingEntries); % initial value
lb = 1/9*ones(1,NumberOfMissingEntries); % lower bound
ub = 9*ones(1,NumberOfMissingEntries); % upper bound

%% MATLAB fmincon - applying the algorithm 'interior-point'
options = optimoptions('fmincon','Display','iter','Algorithm',...
    'interior-point','PlotFcns',@optimplotfval);
x= fmincon(@objectiveFunction,x0, [],[],[],[],lb,ub,[],options)

% to write the reconstructed complete PCM
for r = 1:NumberOfMissingEntries % r is another index
    A(xPosition(r,1),xPosition(r,2)) = x(r); % put x(r) in the position (i,j);
    A(xPosition(r,2),xPosition(r,1)) = 1/x(r); % put 1/x(r) in the position (j,i)
end

% The Completed matrix
B = A; 
disp(B)

 function LSM =objectiveFunction(x) % objective function
% 
global A;
global xPosition;
global NumberOfMissingEntries;
global n;
%xPosition=ones(NumberMissingEntries,2); % preallocate memory for a variable 
                                  % to speed up the algorithm
index = 1; % an index that verifies the position of i and j
for j = 2:n % for i < j
    for i = 1:j-1
        if A(i,j) == 0
            xPosition(index,1) = i; % position of t in the ith row
            xPosition(index,2) = j; % position of t in the jth column
            index = index+1; % update index until (A(i,j) == 0) ends
        end
    end
end

%t0 = log(ones(1,numberOfMissing)); % initial value: t0 = log([1,1]) or x0 = (1,1).
% using exponential function x = exp(t)
for s = 1:NumberOfMissingEntries % s is another index
    A(xPosition(s,1),xPosition(s,2)) = x(s); % put x in the position (i,j);
    A(xPosition(s,2),xPosition(s,1)) = 1/x(s); % put 1/x in the position (j,i)
end

% Least square Method - Ergu et al. 2016
AT = A'; % transpose of A
L = ones(n,1);
R = ones(1,n);
for i=1:n
    for j=1:n
        L(i,:)=nthroot(prod(A(i,:)),n); % row geometric mean
        R(:,j)=nthroot(prod(A(:,j)),n); % column geometric mean             
    end
end

L; %row geometric mean
R;  % column geometric mean
P = L*R; % matrix product
ErrorMatrix = P.*AT - 1; % GMIBEM error matrix

% Error square 
LSM = 0;
for i = 1:n
    for j = 1:n
  LSM = LSM + ErrorMatrix(i,j).^2; % LSM
 %ErrorSquare = ErrorSquare + abs(ErrorMatrix(i,j)); % LAE

    end
end
LSM;

end](url)





