# Assignment 5: Plotting

## Questions
[Questions](https://github.com/TalhaAkhlaq/ECE210-MATLAB-Seminar-Signals-Systems/blob/main/Assignment%205%3A%20Plotting/Assignment5.pdf)

## Solution
```matlab
% Assignment 5 (Talha Akhlaq) (3/18/2025) (ECE210-A) (Prof. Darius)

% Question 1
x = linspace(-5, 5, 1000);
cos_true = cos(x);
orders = 2:2:20;
num_orders = length(orders);
taylor_approximations = zeros(num_orders, length(x));

for k = 1:num_orders
    order = orders(k);
    taylor_approximations(k, :) = compute_taylor_cos(x, order);
end

figure;
plot(x, cos_true, 'LineWidth', 2);
hold on;
for k = 1:num_orders
    plot(x, taylor_approximations(k, :), '--', 'LineWidth', 1.5);
end
hold off;
xlabel('x axis');
ylabel('y axis');
title('Cosine Function and Taylor Approximations');
legend(['cos(x)', arrayfun(@(n) sprintf('%dth Order', n), orders, 'UniformOutput', false)], 'Location', 'Best');
xlim([-5, 5]);
ylim([-5, 5]);
xticks(-5:1:5);
yticks(-5:1:5);
grid on;

% Question 2
figure;
subplot(1,2,1);
plot(x, cos_true, 'LineWidth', 2);
xlabel('x axis');
ylabel('y axis');
title('Original cos(x)');
xlim([-5, 5]);
ylim([-5, 5]);
xticks(-5:1:5);
yticks(-5:1:5);
grid on;

subplot(1,2,2);
hold on;
for k = 1:num_orders
    plot(x, taylor_approximations(k, :), 'LineWidth', 1.5);
end
hold off;
xlabel('x axis');
ylabel('y axis');
title('Taylor Approximations');
legend(arrayfun(@(n) sprintf('%dth Order', n), orders, 'UniformOutput', false), 'Location', 'Best');
xlim([-5, 5]);
ylim([-5, 5]);
xticks(-5:1:5);
yticks(-5:1:5);
grid on;

% Question 3
[X, Y] = meshgrid(linspace(-5, 5, 100), linspace(-5, 5, 100));
R = sqrt(X.^2 + Y.^2);
Z = sin(pi * R) ./ (pi * R);
Z(R == 0) = 1;

figure;
surf(X, Y, Z);
shading interp;
xlabel('x axis');
ylabel('y axis');
zlabel('z axis');
title('Surface Plot of sinc Function');
xlim([-5, 5]);
ylim([-5, 5]);
colorbar;
grid on;

function approx = compute_taylor_cos(x, order)
    approx = zeros(size(x));
    for n = 0:2:order
        approx = approx + ((-1)^(n/2)) * (x.^n) / factorial(n);
    end
end
