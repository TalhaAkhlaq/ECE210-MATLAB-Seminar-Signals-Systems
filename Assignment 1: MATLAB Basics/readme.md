# Assignment 1: MATLAB Basics

## Questions
[Assignment 1 Questions](https://github.com/TalhaAkhlaq/ECE210-MATLAB-Seminar-Signals-Systems/blob/main/Assignment%201/Assignment%201.pdf)

## Solution
```matlab
% Assignment 1: MATLAB Basics (Talha Akhlaq) (2/3/2025) (ECE210-A) (Prof. Darius)

% Question 1.1:

u = [17,30,8]

% Question 1.2:

v = [9;15;12]

% Question 1.3:

A = [-3*u;-2*u;-1*u;1*u;2*u]

% or: 

B = [-3;-2;-1;1;2]

A = B.*u

% Question 1.4:

B = [A',v]

% Question 2.1:

c = exp(j*pi/3)

% Question 2.2:

d = sqrt(j)

% Question 2.3:

m = 20000^(1/4.3)

% Question 2.4:

n = floor(2^7.5) + ceil(25*log(250))

% Question 3.1:

A = [8,1,12
    -7,-2,-11
    1,-4,0]

b = [109;-84;56]

x = A\b
