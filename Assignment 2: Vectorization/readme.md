# Assignment 2: Vectorization

## Questions
[Questions](https://github.com/TalhaAkhlaq/ECE210-MATLAB-Seminar-Signals-Systems/blob/main/Assignment%202%3A%20Vectorization/Assignment%202%20Vectorization.pdf)

## Solution
```matlab
% Assignment 2 (Talha Akhlaq) (2/10/2025) (ECE210-A) (Prof. Darius)

% Question 1.1:

u = (-5 : 3 : 7)
 
% Question 1.2:

v = (-pi : pi/2 : pi)'

% Question 2:

n = prod(1 : 10)

% Question 3.1:

A = eye(5) ;    
A(3 , 3) = 0 ;        
A(5 , 4) = 1        

% Question 3.2:

b = [12 , 11 , 10 , 6 , 5 , 4] ;

first_half = reshape(b , [3 , 2]) ;

second_half = first_half - 3 ;

B = [first_half, second_half] 

% Question 4(i):

t = linspace(-pi , pi, 5000) ;

% Question 4(ii):

n = (0 : 50)' ;
a_n = 2 * n + 1 ;

% Question 4(iii):

S = sin(a_n * t) ./ a_n ;

% Question 4(iv):

s = sum(S , 1) ;

% Question 4(v):

plot(t , s);
xlabel('Time (t)');
ylabel('Square Wave Approximation');
title('Square Wave Approximation using Fourier Series');
grid on;
