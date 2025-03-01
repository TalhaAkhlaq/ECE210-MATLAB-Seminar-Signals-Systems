# Assignment 3: Ones and Zeros

## Questions
[Questions](https://github.com/TalhaAkhlaq/ECE210-MATLAB-Seminar-Signals-Systems/blob/main/Assignment%202%3A%20Vectorization/Assignment%202%20Vectorization.pdf)

## Solution
```matlab
% Assignment 3 (Talha Akhlaq) (2/24/2025) (ECE210-A) (Prof. Darius)

% Question 1:
x = linspace(-pi/2, pi/2, 1e4);
u = abs(tan(x));
v = u(u > 0 & u <= 10);
gm = exp(mean(log(v)));
disp(['Geometric Mean: ', num2str(gm)]);

% Question 2:
[A, B] = meshgrid(1:256, 1:256);
L = (abs(A - 100) + abs(B - 100) < 40) & (sqrt((A - 100).^2 + (B - 100).^2) > 15);
figure;
imshow(L);
title('Matrix L');

% Question 3:
dice = 1:6;
[d1, d2, d3] = ndgrid(dice, dice, dice);
s = d1 + d2 + d3;
valid_count = sum(s(:) >= 11);
total = numel(s);
p = valid_count / total;
disp(['Probability of sum >= 11: ', num2str(p)]);


